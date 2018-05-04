---
layout: post
title:      "Seed Data in seeds.rb"
date:       2018-05-04 19:15:40 +0000
permalink:  seed_data_in_seeds_rb
---


This workout project has the most extensive seed data that I’ve written so far. 

After planning, I started researching. It would be great to find an already existing API that just delivers all the information I could ever want about strength training workouts. But I can’t find one. So I spent the past couple of days doing research and building what I want. 

## Models and Tables

If you remember my planning stage, I had two models -- Workout and Category. The Workout has several pieces of data in the table -- name, description of how to do the exercise, link to a video demonstration of the exercise, a suggested number of how many to do, and it belongs to a category. Category only has a title. 

In my previous projects, I didn’t have to create much seed data because they were mostly CRUD apps. The point of the app was that the user could create content, then read, update, or destroy it. 

With this app, I don’t want the user to worry about creating content. The point is to guide you through a workout, maybe introduce you to some new workouts, but not make you worry about finding a workout to add to your profile. 

## db/seeds.rb

That’s where the seeds.rb file comes in. 

When you create a new Rails app, it generates a seeds.rb file for you. It give you a bit of guidance in commented-out text at the top:

```
# This file should contain all the record creation needed to seed the database with its default values.
# The data can then be loaded with the rails db:seed command (or created alongside the database with db:setup).
#
# Examples:
#
#   movies = Movie.create([{ name: 'Star Wars' }, { name: 'Lord of the Rings' }])
#   Character.create(name: 'Luke', movie: movies.first)
```

In the past, I’ve created the seed file with just 3 entries, so I always created one at a time, like this:

```
sharon = User.create(username: "sharon", email: "sharon@gmail.com", password: "password")
```

And

```
item_1 = Item.create(name: "apples", price: "200", inventory: "250", vendor_id: vendor_1.id, category_id: category_1.id)
```

Using ```create``` there does ```new``` and ```save``` in the same line. 

Doing one item at a time was getting too unwieldy for my expanded database with 30 workouts. 

## Iterating

Option one for creating a dataset is to iterate over an array of the data. I decided to use this for the Categories, because their information is so simple, just a title. 

```
category_list = [
  "bodyweight training",
  "dumbbell training",
  "barbell training",
]

category_list.each do |title|
  Category.create(title: title)
end
```

As soon as you migrate your databases and run rake db:seed, you’ve got three categories with an id and a title. 

## Hash

The second option for creating a dataset is to set up each item in a hash, put all the hashes in an array, and call create on the whole thing. It’s the way one of the examples is set up in the seeds.rb file:

```
 movies = Movie.create([{ name: 'Star Wars' }, { name: 'Lord of the Rings' }])
```

Mine looks a little more complex:

```
workouts = Workout.create([
  {
    name: "bodyweight squats",
    description: "Stand with your head facing forward and your chest held up and out.
Place your feet shoulder-width apart or slightly wider. Extend your hands straight out in front of you to help keep your balance. You can also bend the elbows or clasp the fingers.
Sit back and down like you're sitting into an imaginary chair. Keep your head facing forward as your upper body bends forward a bit. Rather than allowing your back to round, let your lower back arch slightly as you descend.
Lower down so your thighs are as parallel to the floor as possible, with your knees over your ankles. Press your weight back into your heels.
Keep your body tight, and push through your heels to bring yourself back to the starting position.",
    video: "https://youtu.be/cB0cOX7gePg",
    number: 20,
    category_id: 1
  },
  {
    name: "push ups",
    description: "Get on the floor on all fours, positioning your hands slightly wider than your shoulders.
Extend your legs back so that you are balanced on your hands and toes. Keep your body in a straight line from head to toe without sagging in the middle or arching your back. You can position you feet to be close together or a bit wider depending upon what is most comfortable for you.
Before you begin any movement, contract your abs and tighten your core by pulling your belly button toward your spine. Keep a tight core throughout the entire push up.
Inhale as you slowly bend your elbows and lower yourself until your elbows are at a 90 degree angle.
Exhale as you begin contracting your chest muscles and pushing back up through your hands to the start position. Don't lock out the elbows; keep them slightly bent.",
    video: "https://youtu.be/8V-ZUMvQKr0",
    number: 10,
    category_id: 1
  },
  {
    name: "walking lunges",
    description: "Begin standing with your feet shoulder width apart and your hands on your hips.
Step forward with one leg, flexing the knees to drop your hips. Descend until your rear knee nearly touches the ground. Your posture should remain upright, and your front knee should stay above the front foot.
Drive through the heel of your lead foot and extend both knees to raise yourself back up.
Step forward with your rear foot, repeating the lunge on the opposite leg.",
    video: "https://youtu.be/YYWhkctnP2o",
    number: 20,
    category_id: 1
  },
.
.
.
])
```

Once I tweaked the set up a little bit, I was able to migrate all my databases, run ```rake db:seed``` and see all of my data. 

