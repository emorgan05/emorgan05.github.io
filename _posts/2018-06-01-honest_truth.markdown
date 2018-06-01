---
layout: post
title:      "Honest Truth"
date:       2018-06-01 18:44:07 +0000
permalink:  honest_truth
---


Pausing our regular series on this workout app for a moment for a behind the scenes insight into the struggle. You’ve seen my beautifully diagrammed plans, but at the moment, I feel like they’re not worth much. I’m struggling with how to set up the components. 

I have the way I setup components in my Habit Tracker and as a comparison I have the model that I saw demonstrated during a Learn React meetup. They seem to be reasonable models for the approach to components. I think it’s clear that the setup from the meetup is better. The components are more reusable, and they are more separated by their function -- styled components are just styled components (for the most part). On the flip side, my version in my Habit Tracker was all about how data was moving around the app and what components would do.

My diagramming was using the meetup approach, which I imagine like this:
Container → Page Template → Page Container
				                                                 → Page Content

And the props (the React name for data) will move down the arrows as well. 

But the problem I’m having right now is connecting a click of the “Categories” button to rendering a list of the categories that are available. Somewhere in the passing on of that information, the categories are getting lost. Like the actual categories aren’t in the Redux store. 

Because I feel like this passing props problem is happening because of the setup of the components, I’m kind of frustrated with the setup. I’m not sure whether to press on or rework them completely. If you have an opinion, please let me know in the comments!

I’m off to study up so I can fix this bug and keep moving forward.

