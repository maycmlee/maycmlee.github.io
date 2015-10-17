---
layout: post
title: "What it all comes down to...Binary Code"
date: 2015-10-17 18:24:03 -0400
comments: true
categories: Flatiron&nbsp;School
---

While I was working on the "Secret Handshake" lab, I became interested in binary codes.  I knew vaguely that computers at the lowest level operated on a binary system, but I didn't quite understand what that meant. How does a computer understand what we are asking for when run a program?  I decided to investigate into this.

First I found out how to convert our regular decimal numbers into binary code.  Our counting system is a base-ten system, meaining we have digits from 0 to 9.  The binary number system or base-two contains only 0 and 1.  To convert a number from base-ten to base-two:

14/2 = 7 remainder 0
7/2  = 3 remainder 1
3/2  = 1 remainder 1
1/2  = 0 remainder 1

1110 in base-2 = 14 in base-10

So that is how a computer converts numbers into what it can understand, the binary system.

But what about the alphabet and other symbols such as #, &, % and etcs?

That's where the ASCII (American Standard Code for Information Interchange) table comes in.  The ASCI table converts the upper case, lower case alphabet and symbols into a decimal number.

{% img ../public/images/ASCIItable.jpg %}

From the decimal number the computer can then convert it into a binary number.

For example, let's take the capital letter "A".  Looking at the ASCII table we see that it is 65.  Converting 65 into a binary number...  

65/2 = 1
32/2 = 0
16/2 = 0
8/2  = 0
4/2  = 0
2/2  = 0
1    = 1

Binary code for A is 1000001.

Hello World 
01001000 01100101 01101100 01101100 01101111 00100000 01010111 01101111 01110010 01101100 01100100

How does this all come together?  Computers, in terms of their hardware just toggles between, being on or off.  They are really only a collection of on/off switches (transistors) so it's through the 0's and 1's that they know what data to store and what to execute.

http://binarytranslator.com/


