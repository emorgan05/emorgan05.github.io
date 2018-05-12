---
layout: post
title:      "Rounding Out the API"
date:       2018-05-12 23:17:34 +0000
permalink:  rounding_out_the_api
---


With my plan for my Workout App in place, and the Seed Data to provide a bunch of different workouts, it’s time to finish up the API part of this app. 

I’m using Ruby on Rails to create the API. With all the “Rails Magic,” it’s a pretty straightforward set up.

## Creating the App 

```rails new workout-rails-api --api --database=postgresql```

This creates the folder structure I need for my Rails app. I’ve used the option --api because I don’t need views with this app. I’m going to set up a React frontend to handle displaying all the data.

I also chose to set up the database with postgresql. Rails defaults to a SQLite database, which works perfectly, but in order to deploy on Heroku, which is my goal, I need to use PostgreSQL. It’s fairly straightforward to switch them later on, but this let’s me skip that extra step. 

## Adding Specifics

Adding the models, migrations, and seed data is the next step. This is where all that planning comes in handy. For this app, I have just two models: Workout and Category. I know that for each workout, I’ve got a name, description, video, number, and it belongs to a category. The categories only have a title, and a category has_many workouts. 

I added Active Model Serializers. Setting up the belongs_to/has_many relationship in the serializer helps me to get back exactly the information I want when I hit one of the API endpoints that I’m going to create. 

For example, without the serializer, if I call ```/workout/:id```, I won’t get back the title of the category it belongs to. I’ll only get back the category_id. And that won’t be very useful for my users. But with the serializer and the relationships set up, I can get the title of the category, and show that to the user so they know what to expect. 

## Routes

The next step is to add routes to ```config/routes.rb```. In my diagramming, I decided I only needed 3 routes: 
1. /workouts to get all the workouts
2. /categories to get all the categories
3. /category/:id/workouts to get the workouts for a specific category

I also decided that rather than declaring ```resource :workouts```, I only wanted to declare the routes that I was actually going to use. 

All pretty easy and straightforward except for that last route. What I’m trying to do is either let the user hit start and workout for a random 5 workouts from all the workouts, or choose a category and workout to a random 5 in that category. The problem was that when I nested workouts into category, Rails declared the controller action workout#index. But I already had a workout#index. 

After working on a couple of variations, I set up the routes like this:

```
Rails.application.routes.draw do
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
  get '/workouts', to: 'workouts#index'
  get '/categories', to: 'categories#index'
  resources :categories, only: [:show] do
    resources :workouts, only: [:index], to: 'workouts#category'
  end
end
```

I used the same nesting I planned to, I just gave it a new name. 

## Controllers

With the models, migrations, seed data, serializers, and routes in place, I was ready to work on the controllers. Again, keeping this a simple app means that there aren’t very many controllers to write. I needed a workout#index, category#index, and workouts#category to all return json.

Again that workouts#category needed a little more attention:

```
def category
    workouts = Workout.where("category_id = ?", params[:category_id])
    render json: workouts
  end
```

With all of that in place, a quick check shows that my endpoints return the data that I seeded. 

