---
layout: post
title:      "Chapter 10: Colon versus Equals"
date:       2018-04-06 20:53:08 +0000
permalink:  chapter_10_colon_versus_equals
---


This week I’ve been learning a dash of Angular. In theory, this isn’t my first run-in. However, my first run-in with Angular was more than a year ago and it was AngularJS. And that’s a completely different beast. 

As I work through this initial tutorial to learn some of the basics of Angular, it feels more like React than anything I would have compared it to a year ago. But the thing that keeps tripping me up is where do I use a colon and where do I use an equals sign?

**Here’s what I learned:**

The colon vs the equals is a feature of TypeScript, not a feature of Angular. Angular could be using vanilla Javascript and then we would probably all carry on writing the code without ever thinking very hard about colons or equals because it’s what we’ve gotten used to. But Angular is using TypeScript, so we’ve got to figure out some new features. 

Fortunately, it will be as easy as learning when to use `let` and `const`. 

**What is TypeScript?**

TypeScript is a “superset” of Javascript. What does that mean?

Well, it was a language that was built on top of Javascript. Legend has it that the folks over at Microsoft got tired of some of Javascript’s idiosyncrasies, and they decided to create something new that would mitigate those idiosyncrasies. Also they needed a language that would work better to develop really large applications. 

Ok, here’s what’s definitely true out of the legend: 
1. Microsoft developed TypeScript
2. It’s based on Javascript, but makes some things easier/better
3. It works well to develop really large applications

What’s different about TypeScript?
1. It incorporated all of the planned ECMA2015 changes 3 years before those were released (things like classes and arrow functions).
2. It adds a variety of other features, but what we are most concerned with is type annotations.

**Back to colon vs equals**

Type annotations means that TypeScript allows you to declare a variable’s type and then have it checked at compile time. 

`true` is a boolean type

`let hasAType: boolean` Here we use the colon to set the type of our variable

`let hasAType: boolean = true` Now we’ve both set a type (boolean) and assigned it a value

Keeping this really simple, equals signs are used to assign the value to a variable. A colon is used to assign a type. 

**Where simple doesn’t work**

The simple explanation above doesn’t work with JS Objects. The colon will be used inside the JS Object, just like in vanilla Javascript. Let me show you what I mean.

In my recent React project, I have a component that is keeping state like this:


```
this.state = {

      name: '',
			
      description: '',
			
      number_of_days: '',
			
      category_id: '',
			
      stars: [{}, {}, {}, {}, {}, {}, {}]
			
}
```


As you can see, there are colons after each property variable. If I rewrote that object in TypeScript, it would look the same. 

Let’s look at a TypeScript example. This comes from the Angular Tutorial. First we set up a Hero class:


```
export class Hero {

  id: number;
	
  name: string;
	
}
```


I think of this as our cookie cutter. It gives us the standard shape of a hero, and you can see that we are setting types inside the Object. 

When we want to use our cookie cutter and actually create one individual hero, it looks like this:


```
 hero: Hero = {
 
    id: 1,
		
    name: 'Windstorm'
		
  };
```


Notice that outside of the Object’s curly brackets, we have the same pattern we saw before. A variable hero, then a colon to set the type to an instance of the Hero class, and then an equals to give a specific value to the Hero Object. 

Let me know if anything here is confusing, if you have another way of understanding things, or if I’ve gotten something wrong. Thanks for the feedback!

