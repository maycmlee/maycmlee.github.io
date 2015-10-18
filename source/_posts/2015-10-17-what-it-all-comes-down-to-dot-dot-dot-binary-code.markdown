---
layout: post
title: "What it all comes down to...Binary Code"
date: 2015-10-17 18:24:03 -0400
comments: true
categories: Flatiron&nbsp;School
---

While I was working on the "Secret Handshake" lab, I became interested in binary codes.  I knew vaguely that computers at the lowest level operated on a binary system, but I didn't quite understand what that meant. How does a computer understand what we are asking for when we run a program?  I decided to do a little investigation.

First, I found out that a computer, in terms of its hardward, can actually only understand the states of 'on' and 'off'.  So everything a computer does is based on a combination of turning switches (transistors) on and off. These on and off states are represented by the binary code of 0's and 1's.

So what is the binary number system?  Our counting system is a base-ten system, meaning we have digits from 0 to 9.  The binary number system or base-two contains only 0 and 1.  

So how do we convert our regular decimal numbers into binary code?  

For example, how do we convert 14 into binary code?

14/2 = 7 remainder <b>0</b>

7/2&nbsp;&nbsp; = 3 remainder <b>1</b>

3/2&nbsp;&nbsp; = 1 remainder <b>1</b>

1&#47;2&nbsp;&nbsp; = 0 remainder <b>1</b>

<b>1110</b> in binary = <b>14</b> in our decimal counting system.

But what about the alphabet and other symbols such as #, &, % and etc?

That's where the ASCII (American Standard Code for Information Interchange) table comes in.  The ASCII table converts the upper case, lower case alphabet and symbols into a decimal number.

<img src="images/asciitable.png">

Another <a href="http://www.ascii.cl/htmlcodes.htm" target=_blank>ASCII table</a>.

From the decimal number the computer can then convert it into a binary number.

For example, let's take the capital letter "A".  Looking at the ASCII table we see that it is 65.  Converting 65 into a binary number...  

65/2 = <b>1</b>

32/2 = <b>0</b>

16/2 = <b>0</b>

8/2&nbsp;&nbsp;  = <b>0</b>

4/2&nbsp;&nbsp;  = <b>0</b>

2/2&nbsp;&nbsp;  = <b>0</b>

1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;= <b>1</b>

Binary code for "A" is <b>1000001</b>.

And the binary code for a string like 'Hello World' is...

01001000 01100101 01101100 01101100 01101111 00100000 01010111 01101111 01110010 01101100 01100100

I found it fascinating that everything we input into a computer can all come down to just a long long string of 0's and 1's.

http://binarytranslator.com/


