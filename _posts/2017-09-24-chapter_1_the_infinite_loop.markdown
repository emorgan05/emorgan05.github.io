---
layout: post
title:  "Chapter 1: The Infinite Loop"
date:   2017-09-24 19:28:20 +0000
---


This week was moving week, so I am now in Cary, North Carolina about 3 hours away from my previous home. Moving is exhausting, however you choose to tackle it. I decided to sell much of my furniture and kitchen items and try to only move what was absolutely necessary. 

After I sold my dining table set, aka my primary workstation, I headed over to Starbucks to try and make some progress on a lab or two. I've never considered Starbucks to be a loud place, but when I suddenly needed to concentrate hard, it was deafening! So I paired a loud environment with a major lack of sleep and got terrible results on my lab. 

As part of the lab I was working on, I was writing a while loop. I wrote it based on my guess of what I thought it should be. But I knew it wasn't completely correct, so I ran the tests. And the tests wouldn't run. 

I started with the normal troubleshooting things: Am I connected? Let's refresh and restart just in case. Make sure everything saves, etc. 

Nothing helped. The tests just wouldn't run. After staring at it for a while, I noticed that it went ```learn``` and then blinked for a long time and finally just went to a new command input line. 

I asked for help with a screenshot of my code and the spinning test. We chatted back and forth for two hours, at which point I was told it needed to go up to a higher level. 

It was late and I was hungry, so I went home. When I got there, I reopened my computer and had a message from another coach: "You have an infinite loop in your while loop because you haven't changed your counter."

Yes, my while loop looked like this:
```
i = 0
while i < array.length do
  some great code
end
```

And I completely missed the crucial 
```i += 1```

Lesson learned: Write the counter like you write ```end``` as soon as you start the code.
