---
layout: post
title: "Customizing Devise Gem"
date: 2016-01-29 20:39:40 -0500
comments: true
categories: 
---

Having built out the authentication system for the last project I worked on I decided to try out the Devise RubyGem this time.

For this post, I'm going to assume that you have already used Devise to setup a basic authentication system for a user to sign up, log in and log out. Devise is a Rails engine that sets up its authentication system by generating its own ```views```.  To access these views we have to copy them from the Rails engine by entering this command...

```
rails generate devise views
```

Now if you open your ```views``` folder you'll see all the views that Devise had created in a subfolder called ```devise```...

{% img /images/devise_post/devise_views.png %}

So currently the sign up page looks something like this...

{% img /images/devise_post/signup.png %}

Right now, as you can see, the user password created is requred to have 8 characters.  So what if we just wanted it to have 6 characters?

In ```app/config/initializers/devise.rb``` you'll see configurations options for Devise. 

There is one that is...

{% codeblock lang:ruby %}
config.password_length = 8..72
{% endcodeblock %}

...and if we change the ```8``` to ```6```...and go back to the Sign Up page, we see that the password requirement has now changed to 6 characters.

{% img /images/devise_post/signup_changed.png %}

Now let's say we want the user to be able to have a ```username``` and log in with that ```username``` instead of their email.  How do we do that?

First we have to create a column in the *__user table__* for ```username```...

```
rails g migration add_username_to_users username:string
```
```
rake db:migrate
```

Next we want to add the ```username``` field on the Sign Up page.  
So in ```app/views/devise/registrations/new.html.erb``` we add the following code...

{% codeblock %}
<div class="field">
  <%= f.label :username %><br />
  <%= f.text_field :username%>
</div>
{% endcodeblock %}

And our Sign Up now looks like this...

{% img /images/devise_post/signup_username.png %}

But our current Log In page still uses the email address to verify the user...

{% img /images/devise_post/login.png %}

So then if we want to use the ```username``` instead of ```email``` to log someone in we have to change the Devise configuration in ```app/config/initializers/devise.rb```.  In that file you'll see this line commented out...
{% codeblock %}
  # config.authentication_keys = [:email]
{% endcodeblock %}

To authenticate using ```username``` we have to uncomment this line and change it to be...

{% codeblock lang:ruby %}
config.authentication_keys = [:username]
{% endcodeblock %}


Then opening up ```app/views/devise/sessions/new.html.erb```, which is the Log In page, you'll see this block of code...

{% codeblock %}
<div class="field">
  <%= f.label :email %><br />
  <%= f.email_field :email, autofocus: true %>
</div>
{% endcodeblock %}

and need to change ```email``` to ```username```...

{% codeblock %}
<div class="field">
  <%= f.label :username %><br />
  <%= f.email_field :username, autofocus: true %>
</div>
{% endcodeblock %}

However, because you can't use Devise's ```:validatable``` when using an authentication key that is not ```:email``` a couple of changes have to be made in ```app/models/user.rb```.  

First, we have to comment out ```:validatable``` and then write out the validations for ```username```...

{% codeblock lang:ruby%}
class User < ActiveRecord::Base
  # Include default devise modules. Others available are:
  # :confirmable, :lockable, :timeoutable and :omniauthable, :validatable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable
  validates_uniqueness_of :username
  validates_presence_of :username
end
{% endcodeblock %}

 Sidenote: ```lockable``` and ```confirmable``` require an email field to work.

The Log In page now looks like this...

{% img /images/devise_post/login_username.png %}

 And you have a Devise user authentication system that logs users in with their ```username```!
