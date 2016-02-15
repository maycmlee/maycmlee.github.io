---
layout: post
title: "Resizing Images Using the RMagick Gem"
date: 2015-12-30 17:48:27 -0500
comments: true
categories: 
---
The other day I was trying to find a way to resize photos that I found using the Flickr API.  Scouring around the web I found the RMagick Ruby gem.

To user RMagick, however, you had to first install ImageMagick, which actually does all of the image manipulation.  RMagick just provides a easier user interface.

To install ImageMagick I just did..

```
brew install imagemagick
```

And then added the RMagic gem into my gemfile...

```
gem install rmagick
```

I also had to add this to the file where I was going to use RMagick or wherever I set up the environment...

{% codeblock %}
require 'RMagick'
include Magick
{% endcodeblock %}

...because RMagick is implemented in the Magick module, the line ```include Magick``` adds RMagick's constants and methods to the Magick namespace.

Before I could manipulate the images, I had to first download the photos I found on flickr using their API.  So I wrote method to do just that...  


{% codeblock lang:ruby %}
 def download
    Dir.mkdir("images") unless File.exist?("images")
    open(url) {|f|
      File.open(photo_path,"wb") do |file|
          file.puts f.read
        end
      }
  end
{% endcodeblock %}

Line 2 creates a new directory called "images" if it doesn't already exist.  All the images are downloaded into this folder.  

In line 3, **url** is the url to the flickr image.

In line 4, __photo_path__ is the path to the downloaded photo image.  For example: images/img_0.jpg.

Then I wrote a method to resize the images...

{% codeblock lang:ruby %}
  def resize
    image = Image.read(photo_path)[0]
    resize = image.resize_to_fill(200, 150)
    resize.write(photo_path)
  end
{% endcodeblock %}

In line 2, ```Image.read(photo_path)``` opens the image file with RMagick.  It returns a collection and asks for the first element.

The ```image``` variable is a RMagick Image object.  We can now use Image object methods to manipulate the image.

Here I used the method ```resize_to_fill()```.  From the Rmagick documentation, this method "resizes the image to fit within the specified dimensions while retaining the aspect ratio of the original image. If necessary, crop the image in the larger dimension.

Here are the photos.  Left is the original.  Right is the resized one.

{% img /images/rmagick_post/img_original.jpg %}
{% img /images/rmagick_post/img_resize.jpg %}

Have fun!
