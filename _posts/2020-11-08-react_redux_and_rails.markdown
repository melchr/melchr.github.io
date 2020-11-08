---
layout: post
title:      "React, Redux and Rails"
date:       2020-11-08 21:34:33 +0000
permalink:  react_redux_and_rails
---


Redux was by far the most challenging aspect of this curriculum, as expected. It's wild to think about how far I've come with learning programming, problem solving, and how to make an idea come to life.

The first, and easiest, step of this project was to create my Rails API. I decided on models, relationships, which Serializer to choose and what seed data I needed. I wanted to keep it as simple as possible, so I didn't overwhelm myself with all the information I was trying to apply at once, so I chose a Blog app for a Music Review site I've been meaning to create for a little over a year now. I created a different rendition of this site using a heftier and more detailed version of Rails previously, but knew (or heard about) how simple React can make creating an app.

For my React side of the app, I utilized the create-react-app toolchain, since I knew it was going to be a single page application. Create-React-App gave a lot of helpful template code, and then I just removed a few things I knew I wouldn't need. Next, I created a fetch call in my App.js file just to make sure rails + react were talking to each other. I, then, created a store file, imported my store to the index file in order to pass the store to the provider. I added a reducer - reviewReducer and connected it to my store.

I think it was about this moment I realized what a Reducer was really for - In order to add state, you need to create a Reducer and then add an action to get to it. So, I did just that - I added a synchronous action for my reviewReducer, as well as a GET fetch. I needed somewhere to render this GET request, so I created a ReviewList component to display the reviews in my backend, then imported the ReviewList to my App file.

I imported the usage of react-router-dom in my App file so I could create paths for my components, so when a Link was clicked, the page would render to the specified component attached to that link/path.

I then created a form to submit a new Review, and repeated the same process above with my POST request, added a reducer and an action.

Adding styling via CSS was surprisingly one of the trickier parts of creating this app, outside of making sure everything was connected as it should be. I messed around with the styling for this app a bunch, and decided on a very simple layout so I could focus on the structure and functionality first and foremost.

All in all, building this blog app was really rewarding and surprisingly fun. It reminded me why I became interested in learning programming in the first place.

I hope to always be building on my programming skills, and I'm super grateful to have learned React. I can't promise I'll always use Redux in the future (I really really did not like working with it, a lot of moving pieces), but I definitely learned a lot in the end and would not change anything.
