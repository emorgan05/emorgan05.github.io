---
layout: post
title:      "Chapter 5: Making a Sinatra App"
date:       2017-11-16 19:38:07 +0000
permalink:  chapter_5_making_a_sinatra_app
---


**The Project -- Build a Sinatra CRUD app with multiple models and relationships.** 

My project is a Medication Tracker. The idea is that a user can sign up and then input their medications (prescription or supplements) and all the details about them. 

For the past 10 years, I've watched my grandfather (83 now and still doing this) carry around all his presciptions in a little pouch with a notebook and golf pencil. Three or four times a day, he sits down to take his meds and writes in tiny handwriting in the notebook what he took and what time it is. I know this system works for him, and I will never convince him to change. But I know most of us will need a different system. I designed this app to give us a list of all our medications, so we know and can tell a doctor exactly what we are taking, and to warn us when we need a refill. 

It’s got 2 uses right now: 
1. The user will have a full list of medications and doses for when they visit their doctors. 
2. The app will also calculate the date that they will run out and need a refill. It will tell them the date and give a date 5 days before when they should call to get the refill. The dates will turn red as a warning when the dates approach. 

**The Process:**
I started by setting up the file structure and all the files that I needed myself. I just wanted to make sure that I could do it. 

Then I scrapped that and generated the app using the Corneal gem. I decided that would give me a more polished looking website as the end result. And I'm happy with the way it looks. 

The next step was planning the database tables and creating the migrations. I polled my parents and grandparents for all the prescription information that a user might want to put into the app. The big takeaway from my polling was an rx number and information about the prescribing doctor, so I added both of those to my long list of columns for the medicines. The tables also needed to reflect the has_many/belongs_to relationship of the user and medicines, so it has a foreign key in the medicines table. 

Then I created the models with those same relationships, and with a secure password for the User. 

After the models, I began working on the controllers and views. This is where the hard part comes in, so I drew out all the controllers and views that I would want to have. I tried to make sure that I knew exactly what I was doing in advance. Then I got down to actually coding. 

My personal process was to make the get method, then the form view, then the post method. That workflow kept me clear on what the params were and what I was trying to do. 

**Rake db:seed**
Really soon after I started the controllers I realized that I needed a couple of users and medicines so that I could use shotgun and see that my app was actually working the way I intended. So I read up on seed files, and set up a very simple seed file. That got me 3 users and medicines, and I was able to see much more about how my program was working. I can see it needs refactoring, but it was functional during my development.

**Finishing up**
After I got the user working and able to CRUD all their medicines, I decided I wanted to add one more thing, a calendar view that would list the refill dates sorted in order, so they could see by date when refills were coming. This would help a user see that their first medicine needs refilling this week, but their fourth will need a refill next week, so they can save themselves a trip. 

I added a new table and a new model Calendar. Calendar belongs_to a User and has_many Medicines through User. I set up User with a has_one Calendar relationship. 

I then added the controller and view, and put linking buttons on the other pages. When a new user signs up for the site, a calendar will automatically be created for them and from their full list of medicines, they'll be able to go to a calendar view.

**To Dos**
I’m happy with how the app turned out. The one big thing I would still like to do in the next upgrade is streamline the new medicine form so that it’s a simpler user experience. For example, the user could just select take 2 pills per day instead of typing in 2, or the user could just select “am,” “empty stomach” as the instructions. 

The version 2.0 (or higher) of this app, would be to add a daily tracker that a user can see all their pills for one day and check off that they did take them. 


