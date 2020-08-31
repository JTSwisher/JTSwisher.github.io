---
layout: post
title:      "Async Logic with Redux-Thunk"
date:       2020-08-31 18:05:34 +0000
permalink:  async_logic_with_redux-thunk
---

Medium Article

If you have worked with React before you have most likely encountered the built-in state object available within React components. The state object allows us to store property values that belong to the component where they have been declared. Our ability to access state declared in one component from another component is entirely possible within our app but can become convoluted as our application grows and we need to re-use the information contained in a state object within other components in our app.

Redux is a state management tool that helps alleviate some of the issues we encounter when working with local component state and provides us with the ability to store all of our state in a Javascript object separate from all of our components. This separation provides us the ability to allow any component within our app to access our state just by connecting it to our store which contains all of our application state. That’s a very high-level overview of Redux and the opportunities it provides us. If you have not worked with Redux before I recommend reviewing their documentation as the remainder of this article will be covering an async request life cycle white utilizing the Redux Thunk middleware.

For a project at Flatirons Software Engineering program, I created an application that utilized a React front end with a Rails API backend. This application utilized Redux to manage the state for the entire application on the client-side. Within a normal Redux store, we can only implement synchronous updates when we dispatch our actions. However, when we are requesting information from an external API or the backend API of our app we need to use an asynchronous approach when fetching and persisting data. This is where the Thunk middleware comes into play.

Redux Thunk allows us to complete these asynchronous requests by returning a function within our action creator instead of an action. The inner function that is being returned within our action creator takes in “dispatch” and “getState” as arguments. The action creator below utilizes the dispatch function being passed in as an argument to dispatch two different actions to the reducer.
Image for post
Image for post

The first dispatch call tells our reducer that we are requesting the news data from the external API. This action will hit a case in our switch statement that will update our state changing the value of the “requesting” flag to true. The value of the requesting attribute in our state object allows us to update what is being rendered on the client-side while we are fetching our data, like a spinner or loading bar. When the Fetch call returns the Promise and the Response object we can then manipulate that data as we see fit and send the second dispatch call changing the value of the “requesting” flag and update our applications state completing the request cycle.
Image for post
Image for post

Hopefully this quick overview gave you a better understanding of Thunk in Redux and how you can implement in within your action creators to to complete asynchronous operations.
