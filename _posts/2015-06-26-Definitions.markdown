---
layout: post
title:  "Ruby Definitions"
date:   2015-06-26 18:58:19
categories: ruby sql
---
### What is a class?
A class in Ruby is a blueprint which creates individual objects. An individual object is comprised of different attributes which is what distinguishes itself from other objects in the class. For example, my Pet class can create an individual pet object with attributes such as name, breed and owner. 

### What is a model?
Models are basically classes. In Sintara, we group our class files into the models folder. Models use ORM methods to extract data from our database and convert them into class objects. 

### What is a method?
Ruby methods are created to help us from repeating our code and make our code more organized. They return some sort of Ruby datatype that we need to create a program. A good rule of thumb is that anything you find yourself doing repetetively should probably go in its own method.

### What is a variable?
Variables are essentially a way to store a value and assign a name to that value for reference purposes. A variable can store any type of Ruby datatype.

### What is a request?
 When we are using our programs on the web in a browser, all our actions (or user actions) produce HTTP requests that are sent to the server. The server replies to each of these requests, then browser uses these server responses to build each page that we see in its window. Right now we are using our computer as a local server, but eventually we would use a hosted server where other people can see our web app. 
 
### What is a route?
A route is esentially a path that the browser takes to reach a specific action and file associated with that path. For example, we can have a path /add_user that sends the user to that path, maybe does some ruby logic and spits out a page for them to see based on that logic.

### In the context of a web application, what is a "response"?
In a web application, the user conducts many requests. The web application retrieves data from the program, many times stored in a database, and responds to that user with the applicable information requested.






