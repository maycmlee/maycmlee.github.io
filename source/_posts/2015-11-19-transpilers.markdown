---
layout: post
title: "Transpilers or Source-to-Source Compilers"
date: 2015-11-19 20:32:10 -0500
comments: true
categories: 
---

Yesterday before we started learning Ember we were given a crash course in Babel, a transpiler or transcompiler, for Javascript.  I had never heard of transpilers so decided to look a little more into them.

<b>Transpilers</b> are also known as <b>source-to-source compilers</b>, meaning they translate the source code of a program written in one language into a source code written in another language.  These two source code languages have similar levels of abstraction and are both high-level languages, like Ruby, Python, or JavaScript.

<center><img src= "http://qph.is.quoracdn.net/main-qimg-13f269ab119b5c97abf0ad52c57fffac?convert_to_webp=true">
<br><small>Source: <a href ="http://softwareengineeringdaily.com/2015/07/30/transpiler-tradeoffs-typescript-coffeescript-es6/">Software Engineering Daily</a></small></center>
</center>


A <b>compiler</b>, on the other hand, translates the source code of a high-level language program to a low-level language, such as machine code, which is understood by the computer's CPU.

<center><img src="images/high-to-low-level-languages.png" width=250px>
<br><small>Source: <a href ="http://learntocodewith.me/programming/source-code">Learn to Code With Me</a></small></center>

CoffeeScript, TypeScript, Dart, ECMAScript 6 or ES6 (transcompiled using Babel) are just a couple of languages that transpiles to JavaScript.

Why use transpilers?  It seems that one main reason is so that you don't have to wait for browsers to be updated to start using certain new features because transpilers allows code to be translated into older versions of JavaScript.

Different transpilers also offer different benefits.  For example, CoffeeScript has similarties to Ruby and Python and implments some of the features from those two languages.  So if you know Ruby or Python then CoffeeScript might feel more familiar and be easier for writing JavaScript programs. 

Typescript, another example, is a superset of JavaScript which means that any JavaScript code you write would work with it, but Typescript offers more object oriented programming features than JavaScript alone.  Also, Typescript has similarities to Java and C# so would be easier to program in if you already know those languages.

For more pros and cons of different JavaScript transpilers: <a href = "http://jessewarden.com/2015/02/javascript-transpiled-languages.html">
JavaScript Transpiled Languages</a>