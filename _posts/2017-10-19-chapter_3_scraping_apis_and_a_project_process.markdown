---
layout: post
title:      "Chapter 3: Scraping, APIs, and a Project Process"
date:       2017-10-19 19:13:35 -0400
permalink:  chapter_3_scraping_apis_and_a_project_process
---


The CLI Data Gem Project is the final project of the first big unit of Flatiron School. I got all pumped that I’m almost done with the first unit, and then learned that I had a lot to learn to make this project work. 

# My Process
* Research
* Choose a data source
* Choose a method
* Start the project
* Set up a gem
* CLI first
* Research
* Get the data
* Create the objects
* Make sure the objects connect
* Research
* Start over with getting the data
* Create the objects
* Make sure the objects connect
* Rewrite the CLI to use real data
* Rewrite the CLI
* Rewrite the CLI
* Add something new to the CLI
* Rework the objects connections
* Rewrite the CLI
* Show my family -- get lukewarm reactions
* Make sure the objects connect
* Make it colorful
* Research
* Rewrite the CLI
* Connect to the goodbye method

# Initial Research
In the initial Research, I attended several of Corinna’s study groups to help me understand what the project asks for and what are the best ways to approach it. Corinna gave some great advice about how to find a website that is scrapable and won’t send you into pulling-your-hair out fits. She also mentioned the possibility of using an API instead of scraping, so I attended that study group as well. I also watched all of Avi’s videos, taking notes, and reading through the actual code. 

I had three ideas for “topics” for the project: botanical gardens, books, and self-care. After attending the API study group, I remembered that the New York Times offers an API, which I realized I could connect to my books topic. 

I started researching the NYT Books API, and also the Bestsellers List page. After exploring the page, I thought it was actually pretty scrapable, so I decided to use scraping instead of the API. 

# Planning
After deciding on my topic and method, I planned what I wanted the app to do. In his video Avi calls this “outside in” programming -- meaning that you start with the user’s perspective (the outside) and then build inward to construct the Classes, Objects, and methods you will need to provide that user experience. 

My plan was to present a list of categories featured on the New York Times Bestsellers List. These include things like “Combined Ebook and Print Fiction”, “Hardcover Nonfiction”, “Series”, etc. The user can then pick a category to see the list of books by author and title in that category. Then the user can pick an individual title to see more details, like a brief summary and how many weeks it’s been on the list. 

# Building
I started with the CLI and just input “dummy” information. Using the outside in approach, I was trying to get the methods that I would need to present each list and book information, and move from one to another. It’s also a good ego boost when you can run the program really quickly. 

My next step was to build my scraper. I decided to create a Scraper class, and let it handle all of that data. 

And here’s where the first struggle started. 

The website was actually pretty straightforward to work with and I was able to get all of the information I wanted -- title, author, weeks on the list, amazon url, etc. But I had a huge problem with pulling the category and keeping it connected to the book info. The website set the category up as a “subcategory” which then had a “header” to hold the actual text I wanted, but I couldn’t pull from that area and keep it connected to the first book in the subcategory. 

I worked for hours. I could get the list of categories, I could get the list of books, I could get all the details about an individual book, but I couldn’t separate the list of books by category. Every way I tried just turned into another mess. 

# Making the Switch
As I write this, I’m thinking to myself, hmm… maybe if I had just done… But I felt like I had exhausted all of my options, and so I turned back to the New York Times Books API. They let me explore it before I signed up for the API code. I learned there are several different options, including everything on one category’s list, a historical list, and an overview. 

I chose the overview. It presents all of the individual categories, but only gives the top 5 books in that category for the current week. It was exactly what I wanted, and gave more categories than I could have scraped from the website, so ultimately I am satisfied with the switch. 

Researching the API lead to another round of research, including RestClient and JSON and how to pair my API key with the url provided by the New York Times. 

# Building, part 2
Building started over again with an api.rb file, and after learning how to use RestClient and JSON, I had to learn how to include them as dependencies in the gemfile.spec, and how to get the data from them. My binding.pry skills are really improving. 

Once I had the data in JSON format, I had to decide how to use it. I started by looping through the lists and pulling the list_name to instantiate a new Category. Within that loop I also looped through the books and pulled all the detailed information to instantiate a Book. Because I had worked so far through the scraping, I had existing Category and Book classes and was able to refactor them to use the information coming from the JSON. 

One thing that I debated for a while was whether to keep that loop with it’s two instantiations together in the API class. On another round of research, I rewatched Avi’s video where he creates the RubyWeekly Newsletter. He says he doesn’t want every class to know about everything else, so the Scraper should know about Newsletters, but not about Articles. The Newsletter should know about Articles. So that is the approach that I went with. Now the API instantiates a Category, and then the Category instantiates a Book. 

Then I refactored the CLI. I was able to get the list of all categories pretty quickly. I mentioned before that the bonus of the API was more categories -- a total of 14 this week. From the website, I would have only had 5. 

Then I worked on how to create the list of the top 5 books in an individual category, and then on the details about one book. 

I just kept refactoring and refactoring. My current CLI has many many methods. I’m not sure if that’s overkill, but it was helping me to think about each piece of information and each question as a separate method. It also made it easier when I was linking them together into a menu. 

# Relationships
I knew at the beginning that my Category and Book classes are related. Books belong to Categories, and Categories have many Books. It took a lot of work to get them functioning together though. I wanted to make sure that I was instantiating each new Book with Category as a class, and not just a string of the name. It took a lot of trial, errors, and pry-ing, but they are now linked. Each Book has a Category that is, in fact, a Category. And each Category has an array of Books. 

# Reactions
I was pretty proud of myself for getting the app working, so I was showing it off. The reactions were fairly lukewarm (people with smartphones are unimpressed by the command line interface), but I noticed some squinting to read especially the book details. I researched the Colorize gem that was used in the Student Scraper lab so that I could add color and distinguish things like “Summary” from the actual description of the book. 

# Finally
There was a lot of planning involved in building this app. I think one of the things that helped me the most was drawing out in my first planning stage exactly what I wanted to have happen. Then as I progressed, I drew diagrams to model the relationships between the Category and Book classes. Planning and being able to write in English what I want to have happen made it a lot easier to translate into code. 

There was also a lot of error reading. Building this app made me feel more comfortable with “hmm… error… what’s happening? Ok, not totally sure, but I think it's this. Which file? What line?” And then exploring there until I could see what was going wrong. Sometimes I still didn’t understand the error, so it became, “What happens if I do this?” When I first started learning code, I felt very frustrated with that process. I wanted to know exactly why an error was happening and exactly what would fix it, but I am seeing now that if I experiment a little, it helps me to understand why something has happened. 

And this process feels like the process of writing, get started, back up, start over, think a different way, try again, add new things, rewrite, rewrite, rewrite, back up. And of course, proofread carefully (it always manages to keep me humble). And then finally you say, I’m satisfied with how this works for now. 

