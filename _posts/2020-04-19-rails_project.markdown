---
layout: post
title:      "Rails Project"
date:       2020-04-20 01:20:47 +0000
permalink:  rails_project
---

I finally completed my Rails Project and I could not be happier. Despite having learned everything necessary to complete this project, I was led down so many different rabbit holes and twists & turns - I never could have predicted it would be this complicated.

The main idea behind this project is a real-life idea I had about a year ago. Quick uninteresting fact that sets me apart from no-one: I love music. My friend and I created a music review site where we posted reviews of albums we couldn't stop listening to. About two months ago, I had the idea to create another site that functions completely the opposite - A site where a community of people write about music they hate....so here we are.

The first thing I did was install Devise, which was a big mistake. I'm not comfortable enough with Rails yet to bring in a whole extra outside source of information, and it clearly did not work out, so after 3 days of messing with Devise (but somehow getting Google Oauth to work almost immediately), I started over. Upon the new Rails App creation, I used a resource generator for user, album, review, comment, then later decided I didn't need comments at all. Plus, I wanted this project to be as far away from a standard "blog" as possible. Next came proper associations between each model and table migrations. Then, I began adding actions to controllers, as well as my Sessions controller. Throughout all of that there was also adding user_params to users#create to ensure appropriate parameters are being saved when a user is created, remembering sessions#create is how a user is stored into the system throughout a session, and just general maintaining of my actions to views. Naturally, I forgot to install bcrypt and has_secure_password for users so nothing was working or persisting properly. For my Albums, I installed active storage to create the ability to upload an image to an album. Then, I added complete functionality of all CRUD actions for Albums and Reviews. Soonafter, I changed the reviews index page to no longer be nested under albums and gave it its own resource. Re-reading this, it all sounds so simple. But it was truly an unforgiving process.

One thing I need to remember always is something being PLURAL and not plural, a lot of errors have happened from this alone and it's way too easy to mix up and forget. Another issue I had for a while was my Reviews not saving when being created. I fixed it with this line "belongs_to :album, optional: true". I had a method chaining issue as well (review.user.name) but fixed it by adding @review.user = current_user to my albums#show action.

There were a few things I really had to dig deep in order to figure out: one being Google Authentication. So meticulous! But it felt so good when it finally worked and I saw my google email login options showing up, at last. Another deep dive was with active storage - When I went to upload an image to an album, and then create a new album with no image, the last image I used would persist itself to the database. I fixed this by adding .purge to the album#destroy method and that was that!

Styling was super easy with Materialize CSS, I highly recommend that to the people definitely not reading this.

Overall, I feel like I need to create 5 more Rails apps to really ingrain everything into my brain. However, as frustrated as I was with creating this, I've never felt happier with myself for sticking to it and trying my best. I love Rails so much and I really want to continue working with it in the future. I'm sad it's over (for now) but I'm excited for what's to come!

