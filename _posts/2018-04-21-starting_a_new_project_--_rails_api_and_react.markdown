---
layout: post
title:      "Starting a New Project -- Rails API and React"
date:       2018-04-21 16:51:25 -0400
permalink:  starting_a_new_project_--_rails_api_and_react
---


I’m working on a new project this week. To go with it, I’m working on documenting the steps I am working through. My plan is for this article to be a multi-part series. Let’s start with the basics.

**Here’s the idea for the project:**

My sister wants to workout better. She has no problem doing cardio, but when it comes to strength training/weights/anaerobic workouts, she feels utterly lost. So at the moment, she just doesn’t do it. 

My app will be a workout app. At each workout, you can click “Start” and it will give you a series of 5 exercises to do. You do as many repetitions as you can, and when you’re done with 5, you’ve done your workout for the day. Go you!

For those who want to get a little more specific, I will include categories, so you can choose a specific category (like body weight training) and get 5 body weight exercises to do for the day. 

**Step 1: Planning**

I’ve diagrammed the project. In the Rails API, I will have two models -- workouts and categories. I’ve also laid out the fields for each model table. 

![Models](https://photos.app.goo.gl/apmgy9BtwiMV37tW2)

One thing that I noticed with my last project was I had not thought completely about the endpoints that I would need from the API before I started. So I am doing that here, because it will simplify the routes that I am creating, and the ActiveModel Serialization. I need to know now exactly what information I want and what I will be getting back.

![Routes](https://photos.app.goo.gl/uGtQukwlb7wVDFDz1)

In the React side, I’ve diagrammed the different views that I will present with the project, how they move, and how they interact back with the API. 

![React](https://photos.app.goo.gl/1NlmJBYDZFLJFobs1)

I’ve also planned the routes and what they will be called. (Something else I missed in my last project). 

![ReactRouter](https://photos.app.goo.gl/3369HW3zEhcRZi9G3)

I love the planning stage. Everything is so full of hope and possibility. 

