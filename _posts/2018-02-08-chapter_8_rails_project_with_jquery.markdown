---
layout: post
title:      "Chapter 8: Rails Project with jQuery"
date:       2018-02-08 17:56:37 +0000
permalink:  chapter_8_rails_project_with_jquery
---


The assignment:
“In this assessment your goal is to expand upon the rails assessment you did previously. The goal is to add dynamic features that are possible only through jQuery and a JSON API for your app.”

My project:
My Project is a Farmers’ Market App. It is designed to help Vendors (whether farmers, bakers, craftspeople, etc) track their market schedules and their inventory. 

It’s got two uses:
1. Vendors share public information about their shop, including a description and contact info. The markets give an interested party all the information that they need to go to that farmers’ market with an address and operating hours.  
2. Vendors have a personal profile page where they can add, edit, and remove items from their inventory in order to track their inventory. It also provides them with a list of markets where they sell so that they can easily track their schedule. 

Adding jQuery:
In the original Rails app, almost each different piece of information was on a different view page, which required the browser to do a refresh and load each individual page. 

In adding jQuery, I created two view pages -- the Markets page, and the Vendor’s Personal Profile page. 

On the Markets view page, you can see a list of markets, and then click on the button to see all the details of that market. Clicking on the button will insert the full set of information for that market into the page right below the button. That includes the list of vendors who sell at that market. Clicking on a specific vendor will insert the vendor’s details into the page right below the vendor button. 

On the Vendor’s Personal Profile Page, the vendor’s markets are displayed, there is a button for the inventory, the public info is displayed, and there is a button to edit that information. 

When the inventory button is clicked, a table displaying all of the vendor’s items is inserted into the page. The vendor can add an item, and edit an item without ever refreshing the page. The delete button does require a page refresh. (That is something I would like to improve). 

When the “edit public information” is clicked, the form is inserted into the page, and then the information on the page is updated without a refresh. 

Helpful Resources:
One of the things that really helped me on this project was finding a few additional resources, outside of rereading the lessons, that helped me implement something that I wanted to be able to do. 

First, the EngineYard blog had a great blog post about setting up jQuery in your Rails app. It helped me get my Gemile and manifests right. [https://www.engineyard.com/blog/using-jquery-with-rails-how-to](https://www.engineyard.com/blog/using-jquery-with-rails-how-to)

Second, I discovered that adding the vendor button to the market index page caused a problem and I wasn’t able to just capture that button with jQuery. I found this StackOverflow question and answers really helpful in binding those dynamically created elements. [https://stackoverflow.com/questions/203198/event-binding-on-dynamically-created-elements](https://stackoverflow.com/questions/203198/event-binding-on-dynamically-created-elements)

Finally, I chose to use Handlebars templates for the Inventory table. Creating it as a string in the AJAX calls was getting complicated, and I knew a template would help. This blog had an excellent tutorial that walked me through adding Handlebars to the app, and then implementing it. [https://blog.botreetechnologies.com/using-handlebars-js-with-ruby-on-rails-bcddce004947](https://blog.botreetechnologies.com/using-handlebars-js-with-ruby-on-rails-bcddce004947)

To Dos:
Rails side
1. Expand the inventory tracking abilities. 
2. Add the User and ability to write reviews. 
3. Make it a more attractive site to visit -- like a farmers’ market itself. 

The jQuery side
1. Add the filter function back in
2. Work with the delete button
3. Rework the admin functions
 
Two Big Takeaways:
1. Once again, there were things here that tangled my brain (looking at you TicTacToe). Coding this project was a great way for me to connect parts of the curriculum that felt very separate -- like the OO Javascript and the templates. I learned a lot and feel like I’ve gained understanding in how to use it. 
2. With this project, I got to a point (again) that I was debating about whether to do something else -- adding the templates. I’m so glad I took an hour to work on templates. That was relatively simple to add and showed me how useful they could be when connected to a full app. 

