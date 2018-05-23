---
layout: post
title:      "The First Components"
date:       2018-05-23 15:37:18 +0000
permalink:  the_first_components
---


With this React app, we’ve got all the systems up and ready to go. Now we need start adding our components. As we’re adding them, we’ll go ahead and wire them up with the appropriate calls to the API and get our app rendering the information we want. 

## Styling

You might have noticed I added styled-components as a dependency in the last post. That’s what I am going to use to add some styling to the app. The documentation for styled-components is very good and easy to use. https://www.styled-components.com/

## Reusable Components

I attended a Meetup (shout out to Triangle ReactJS) where we set up a React project. The leader used styled-components and had a way to set up the components so that they were reusable. Because we worked through the project it was easier for me to understand, so I chose to set up my components in a similar fashion. 

## React Router

I also want to be able to use React-Router, so how to connect that to the components is also a consideration. 

## Basic Component Structure

The Index.js file will handle the React-Router. 

At the moment, it looks like this (that will change as I continue adding components):

```
ReactDOM.render(
  <Provider store={store}>
    <Router>
      <div>
        <Route exact path="/" component={HomePageContainer} />
      </div>
    </Router>
  </Provider>,
  document.getElementById('root')
);
```

From the HomePageContainer, I set up a set of reusable components:

* PageTemplate
* PageContainer
* PageContent

PageTemplate is designed to allow me to add whatever parts to the page I want, including a sidebar, heading, navigation bar, etc. 

PageContainer and PageContent hold only the styling from styled-components. 

This is the current styling of PageContent:

```
const PageContent = styled.div`
  margin-left: 20px;
  margin-top: 100px;
  padding: 2rem;
  display: ${props => (props.displayBlock ? 'block' : 'flex')};
  flex-direction: column;
  justify-content: center;
  flex-wrap: wrap;
  min-height: calc(100vh - 164px);
  border: 3px solid #FC6618;
  border-radius: 20px;
`;
```

Visually, I want each workout to have a border and look like a card, so that is why I have the border and border-radius attributes. 

## HomePageContainer

All I need in the HomePageContainer is three buttons: Learn More, Categories, and Start. They’re pretty self-explanatory, but Learn More will give a little more information about the project and how to use it even if it is self-explanatory. 

For the moment, the HomePageContainer renders this:

```
return (
      <PageTemplate>
        <div>
          <Link to="/learn-more" exact="true"><Button>Learn More</Button></Link>
          <Button onClick={this.handleCategoryClick} >Choose a Category</Button>
          <Button>Start</Button>
        </div>
      </PageTemplate>
    )
```

Three buttons, and as we continue, I’ll be making each one work when it is clicked. 

