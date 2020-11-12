---
layout: post
title:      "Make something helpfull"
date:       2020-11-12 04:07:27 +0000
permalink:  make_something_helpfull
---


As with the previous project. I hit a wall when trying to think of what I wanted to make. But one thing that was helpful in making my decision was a line in the project description. That was to make something important to you. So I came up with the idea to make an app that a parent can use to keep track of doctor appointments and milestones for their children. I am often wondering when the next appointment is. And really wanted to have a way to keep track of all the news things he is learning. 

I used the corneal gem to create the skeleton for the app. This gave me the base file structure for the app.  Using the command `corneal scaffold NAME` , I was able to create the models, views, and controllers with one command for each of my classes. This command also gave me the necessary crud routes for each model. Along with accompanying views for each controller. This made development very quick.

I started out making my routes without user authentication. After I had completed a couple of my controllers, I started to utilize the current_user and logged_in helper methods to set the user_id into the browser session and make sure a user had to be logged in to access any of the pages that held child information. By utilizing the belongs_to and has_many active record associations, I made sure a user couldn't access information on a child that wasn't theirs.

For the appointments and milestones views, I had to create the route to view individual instances. However, these didn't hold much information on thier own. These instances also had all of their information displayed on the show page. So I didn't include a link to view them individually. But they were needed in order to create the edit routes for each of them. When I displayed them on the show page with the .each loop, I added the edit link to each instance using their unique id to access each of them. 

In the children controller, I decided to use the slugify methods to make the url easier to read. It is easier to remember my child by name than by a sqlite id number. While this works for my app right now. I feel that it would not work if it was adopted by many users. There will definitely be parents that have children by the same name. So there could be duplicate entry issues with the database if two or more parents have a child with the same name. Though, with the parent association, it may not matter.

I have worked with node.js on a course in the past. I can see many similarities with the routing structures that are used in sinatra. But I didn't have to get as in depth with the project as I did with tracker jack. But I still recognize the coding tasks that were taken care of for me while using active record and sinatra. Having learned how to create the classes and each of the basic methods for them, I have gained a great appreciation for active record and sinatra libraries making it very easy to quickly spin up a dynamic web app. 


