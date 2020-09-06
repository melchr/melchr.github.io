---
layout: post
title:      "JavaScript/Rails Single Page App"
date:       2020-09-06 18:29:40 +0000
permalink:  javascript_rails_single_page_app
---


This project completely defeated me numerous times. It's also equally hard to focus while the world around you is in constant chaos from any angle you look at it.

I think both of these statements prove why I created the type of app I did.

I chose to create an app that hosts resources for current issues around the world. In the future, I hope to host this on Heroku and share with people who can use these resources.

The starting point of this project was to create a new rails app api via my terminal, followed by creating the github repo and then connecting the local app to my github repo.
Next came building the models, along with the migrations, model classes and associations. My models were Category and Material. Categories belong to Materials, and a Category has many Materials. After testing everything, I created seed data and seeded my database.

I then built out my Routes for both materials and categories, each controller (namespaced under api/v1), and the fast JSON API serializer. These serializers definitely hindered me for a while regarding the way my JSON data was accessed via my eventual POST fetch request on the frontend.

After confirming my Rails endpoints (ex. http://localhost:3000/api/v1/materials), I needed to tackle the frontend.

This included creating an index.html and an index.js file. In the index.js file, I added some basic JavaScript (like DOMContentLoaded) and began working on my GET fetch request, which fetched information from the backend via an endpoint I created and added to the index.js file.

After this came the POST fetch request. I created a form in my index.html file to get input from the user, and to make it easier, although in the future I will need this form to be created out of JavaScript to be more adaptable.

I did some refactoring here and there, and then built my Material class in my material.js file. This allows the use of Object Orientation and the ability to edit a particular resource.

All in all, this project taught me a lot about what I think I can handle vs. what I can ACTUALLY handle. It always feels super discouraging to have an issue that can't be figured out, but when it does get figured out, the world finally makes sense again.

It's very clear I need more practice in JavaScript. It's a super free language that allows for unlimited possibilities, and that's scary! I'm excited to take on the final project and further my knowledge in JavaScript, and learn React.
