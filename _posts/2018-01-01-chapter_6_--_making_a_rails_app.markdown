---
layout: post
title:      "Chapter 6 -- Making a Rails App"
date:       2018-01-01 17:21:30 -0500
permalink:  chapter_6_--_making_a_rails_app
---


# The Project:
Make a Rails app, with many specific requirements on associations, nested forms, etc. 

My Project is a Farmers’ Market App. It is designed to help Vendors (whether farmers, bakers, craftspeople, etc) track their market schedules and their inventory. 

It’s got two uses:
1. Vendors have a details page where they share public information about their shop, including a description and the markets where they sell. The markets are linked to a market#show page which will give an interested party all the information that they need to go to that farmers’ market. 

2. Vendors have a personal profile page where they can add, edit, and remove items from their inventory in order to track their inventory. It also provides them with a list of markets where they sell so that they can easily track their schedule. 

# The Process:
I started with some serious diagramming. I felt like building the Flatiron Store Project was a bit of an extra struggle for me because the models were designed by someone else and I felt through the whole project that I didn’t really understand the design and would have done it in some different way. Because of that struggle, I knew I really needed to get down on paper exactly what I wanted this app to look like. 

The first step was models and their relationships to each other. Then I diagrammed the columns that I would need in their corresponding databases. That was great, because it actually lead me to understanding that I would need a separate model for the addresses -- Farmers’ Markets have addresses. 

Then I diagrammed the views, and added features to meet the requirements of the project. 

The diagram was really helpful, and I kept going back to it as I coded, because it kept me on the right track. 

# Things I Struggled With:
-- Adding OmniAuth. Actually adding it was not the hard part at all. But it made me realize that my Vendors would be instantiated without all the details about their shop. So I knew I’d need a form that didn’t instantiate them, but that let them add all that information, the way I would have had a new form do. My work-around was to create a link on their profile page to update their shop information. 

-- After working through that small issue. I decided to juggle who my app was meant for. At first I had envisioned Vendors and Users, and Vendors could use it as you see, but Users could write reviews. Although I still really like that idea, it got too unwieldy for my current project. So I chose to focus instead on the Vendors. 

-- Displaying validation errors. Ok, here’s the thing, I understand that this wouldn’t work because HTTP is stateless and doesn’t remember the errors from one view to the next. However, I was writing the erb exactly the way the documentation demonstrated, so I don’t understand why it wouldn’t work. 

Nonetheless, I reworked it so that it actually does display the errors. 

-- Using Scope to Filter. I am properly filtering the items by_category on the inventory page and filtering the vendors by_category. But I would also like to filter the farmers’ markets (index list) by their location (state). But I’m struggling to get the relationship to work out. 

# To Dos:
* Expand the inventory tracking abilities. I imagine that there are more things the vendors would like to track and adding those things would make this a more useful tool. 
* Add the User and ability to write reviews. I’d like the user to be able to save their favorite markets, look at their pages and see what vendors are offering this week. I think reviews will help both markets and vendors to get more people to try their products. 
* Make it a more attractive site to visit -- like a farmers’ market itself. 

# Two Big Takeaways:
1. I felt like this section of the curriculum got into some really hard things that tangled my brain for a while (looking at you nested forms). But overall, coding the project made me feel better about my skills and the things that I have learned. 

2. I was talking to a friend about whether or not to add a couple of things to the project. She asked the perfect question: “Would doing those things help you learn more?” It got right to the heart of what I am really here to do, so I added an Admin role, added filtering to another area, and did some CSS styling. All these reinforced my learning. 
