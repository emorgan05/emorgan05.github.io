---
layout: post
title:      "Chapter 9: React/Redux Project"
date:       2018-03-20 22:48:57 +0000
permalink:  chapter_9_react_redux_project
---


**The Project:**</br>
Create a React app that uses the Redux store and persists data to a Rails API. 

**HabitTracker:**</br>
My project is a Habit tracker. A user can put in a habit that they want to track, giving it a name, description, the number of days per week they want to do it, and selecting the appropriate category for it. 

Their habits are rendered in a list. They can click on a circle to show they completed the habit today. If they click on the habit name, they get a details/show view that shows all the information about the habit and their goal, as well as their current streak (how many days in a row they’ve completed the habit up to today) and their longest streak ever. 

The HabitTracker can be used for any habit -- health, fitness, intellectual, emotional, etc. In the seed file I included examples like floss, run, and meditate.

**Planning:**</br>
This project has so many moving parts that I really learned the importance of planning. I planned out my Rails API the same way that I did for the Rails Project (my Farmers’ Market app), and that was really beneficial. 

I also planned out what I wanted the React frontend to look like, but now that I have completed the project, I know I needed more detailed planning about what the components would be, what fetches I would need to make to the API, and how to connect the information together. I would like a diagram of the data that needs to be sent to the app, and then the view broken into components with the ones that are containers (connected to the Redux store) and the ones that don’t need that data. 

I think all the learning I did on this app will help me plan the next one so it goes just a little smoother. 

**Eating an Elephant:**</br>
**Q:** “How do you eat an elephant?”
**A:** “One bite at a time.”

This app was an undertaking like eating an elephant. At times I felt extremely overwhelmed with how to connect everything together, but I tried to focus on building one piece at a time. 

**First:** The Rails API. I was so happy to be back in Ruby on Rails land that I really enjoyed building the API. I created it as simply an API, so everything that it needed was pretty straightforward. 

At the end of the project, I added methods to the HabitsSerializer -- a completely new task for me -- to calculate the current streak and longest streak. This was a cool thing to learn and watch show up in the Redux store. 

**Second:** I created the React app. On the first pass, I just created the frontend entirely with React, never connecting it to Redux or the API. 

At points later, I felt like this was a big mistake, because I wound up feeling like I rewrote the entire app when I connected Redux. Mistake or no, I really learned a lot about React and what it can do by building a React-only app. It also helped me really understand and see how Redux works when I got to that part, because I could see exactly what Redux was responsible for. 

**Third:** Connecting the API and React together through Redux. Redux made this kind of silly static frontend app much more powerful. I learned a lot about the flow of of data and the flow of changing the state. 

**ToDos:**</br>
As with all projects, there are things that I would like to add to make this better. 
1. In the Habits List I’d like to show a representation of the current week. I envision this as circles with a check mark or x depending on whether the habit was completed, and a clickable circle if it’s an upcoming day. </br>
2. I’m happy with the current streak and the longest streak just outputting numbers, but part of the fun of React would be changing that to a visual representation. It could be blocks on a calendar (like on the Learn frontpage) or a progress bar. But I’d like something visual. 

**Big Takeaways:**</br>
1. Break it down -- Do one thing at a time and focus on making that one thing work. This is particularly hard when there are so many different files involved in making a React component that a user can interact with, that then creates an Action, calls the API, returns data, and sends it to a reducer. But, the point remains, focus on one thing at a time. </br>
2. Take your time -- Take the time to plan the app. Take the time to make a rock solid API. Take the time to diagram your components. Each of these pieces is a building block, so make sure they work. </br>
3. I am amazed with how much I have learned. When I showed my app to my family, some were enthusiastic, and some were underwhelmed. To the underwhelmed ones I want to say, “Do you know how much code I wrote to get it to do that?!!!!!” I’ve learned so much. There was a time just a few months ago that I felt overwhelmed by creating an entire Rails app, but with this, that was the fun part. The same will happen for React too. 
