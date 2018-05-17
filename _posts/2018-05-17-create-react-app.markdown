---
layout: post
title:      "Create-React-App"
date:       2018-05-17 19:52:26 +0000
permalink:  create-react-app
---


With the API ready to go, it’s time to start on the React portion of this app. In my previous project, Habit Tracker, I chose to set up the React app inside the Rails app. This time I’ve decided to try out the other option -- create two separate repositories -- in order to see the pros and cons of each. 

## create-react-app

Just like ```rails new```, ```create-react-app``` initializes a new app with all the set up and organization you will need. You can run ```npm start``` and it will open a test page in the browser to show you that it is fully functional. 

```create-react-app workout-react-app```

Despite how amazingly convenient ```create-react-app``` is, there is still a bit of set up for you to do. Part of this helps you to incorporate Redux into the project, and part of it is just to make it how you want. 

## Add Dependencies

To add the dependencies, I used npm, but you can also use yarn. 

```npm install --save name-of-dependency```

The dependencies I added were:
redux
react-redux
redux-thunk
react-router-dom
ajv
styled-components

The first three, redux, react-redux, and redux-thunk, allow us to incorporate Redux and it’s single source of truth store fully into the project. 

React-router-dom allows us to make specific components to URLs, even though it is a single page application. 

I added styled-components for it’s easy styling. 

After I had all of those dependencies set up, I got a warning that one of my dependencies needed AJV. So I added it. It’s a package called “Another JSON Validator.”

## Add Folders

In the src folder, I added folders for actions, components, containers, reducers, and store. I will probably add an api folder as well, but I’ll leave that for a little later on. 

In the React app, the src folder holds all the parts of your app. It’s created with everything just hanging out at top level in that folder, but adding some folders and a little more structure as you want makes it a little easier to navigate as you continue building out your app. 

## Add RootReducer

In the reducers folder, you’ll need a rootReducer.js file. Again this is just making stuff easier for the future. As you build out your app, you’ll get several different reducers and it’s easier to understand them if they are in separate files. We’ll write them separately and then pull them back together in the rootReducer. 

For the initial set up, it will look like this:
```
import { combineReducers } from 'redux';
// import all other reducers

const rootReducer = combineReducers({
  // name all reducers
});

export default rootReducer;
```

After you build out your app, you’ll have several working reducers added here, so it will look like:
```
import { combineReducers } from 'redux';
import sessionReducer from './sessionReducer';
import { habitReducer } from './habitReducer';
import { starReducer } from './starReducer';

const rootReducer = combineReducers({
  session: sessionReducer,
  habits: habitReducer,
  stars: starReducer
});

export default rootReducer;
```

## Add ConfigureStore

With the rootReducer mocked out, we can create the store. I created a file /src/store/configureStore.js. 

```
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from '../reducers/rootReducer';

export default function configureStore() {
  return createStore(
    rootReducer,
    window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__(),
    applyMiddleware(thunk)
  );
}
```

Our function here uses the createStore provided by Redux, uses our rootReducer, and uses the middleware Thunk to create a store that can hold all of our app information and serve as the single source of truth. 

Then we added some dev tools functionality to make life nicer. 

Unlike the rootReducer, this will be all that the store needs. After this set up, you shouldn’t need to return to this file down the road. 

There’s just one more place to wire it up so it’s all working properly. 

## Index.js

The index.js file is initialized with create-react-app. But it needs some tweaks now. This is the file where you will call on the store we set up in the configureStore file and pass it to your app. 

```
import React from 'react';
import { render } from 'react-dom';
import configureStore from './store/configureStore';
import SomeComponent from './components/SomeComponent/SomeComponent';
import './styles/styles.css';

const store = configureStore();

render(
  <Provider store={store}>
      <SomeComponent />
  </Provider>,
  document.getElementById('app')
);
```

This file is another one that might change beyond this initial set up. One thing that might cause more changes is incorporating routes with react-router. 


Ok, that’s the end of today’s work. We’ve got a React app, it’s got the Redux side properly wired in, and we’re ready to start creating our components. 

If you’d like another tutorial on setting up a React/Redux app, I found this one really helpful as I was going through the process: https://code.likeagirl.io/tutorial-for-adding-redux-to-a-react-app-1a94cc1738e5
