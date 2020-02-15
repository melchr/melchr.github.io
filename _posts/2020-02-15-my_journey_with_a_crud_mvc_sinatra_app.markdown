---
layout: post
title:      "My journey with a CRUD/MVC Sinatra App"
date:       2020-02-15 22:50:21 +0000
permalink:  my_journey_with_a_crud_mvc_sinatra_app
---


The process of building and truly understanding this app taught me a lot about what I'm actually capable of, and to be honest, it shocked me.

There are a lot of requirements in order to create just the bare skeleton of a Sinatra App. However, Corneal covers all of that in a very well put together gem [found here](https://github.com/thebrianemory/corneal).
After installing that, and thinking of an extremely unuseful, unoriginal idea that definitely already exists, I created my database by adding tables and migrating them (rake db:migrate, never forget.)

*side note, it took me 3 straight weeks to understand what I was doing, as far as migrating tables goes. I will never (ever) forget how to create, update, or migrate a table in Sinatra.)*

I got most of the CSS out of the way at the beginning, because CSS is something I've worked with before and it was rather easy.

After CSS, I created two models - one for users and another for gigs. In each model, I included validations and the appropriate has_many/belongs_to relationships. In the user model, I included the has_secure_password macro, thanks to the 'bcrypt' gem (required in my gemfile.)

At the beginning of starting this process, I wrote all of my routes in one single controller, but soon realized how unorganized and hard to read that became. From there, I put users and gigs in their own controllers and ensured both controllers inherited from the Application Controller and that the Application Controller inherited from Sinatra::Base.

After this, config.ru had to be set up correctly. It can only 'run' one controller, and had to 'use' the rest.
I added the `Rack::MethodOverride` middleware line for the 'patch' and 'delete' routes in my controllers, as well.

From here, I had some struggles with updating when trying to edit one of my gigs, but I kept messing around with the code and trying to understand why it wouldn't save when updating. (The final consensus was that I needed the update method to accept the params of a gig.)

The only other complicated challenge I faced was understanding the show.erb file, as well as knowing which methods to add onto Class variables.

In the future, I'd like to add other features to this app to make it more useful and functional, such as a search feature, showing which user added what, ability to friend each user, and save a gig as a favorite if you didn't add it.


