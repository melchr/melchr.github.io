---
layout: post
title:      "Has Many Through and Why I Thought I Built My Rails Application Wrong"
date:       2020-04-26 13:53:00 -0400
permalink:  has_many_through_and_why_i_thought_i_built_my_rails_application_wrong
---


I feel like it's natural to hate something you don't understand. It feels limiting and ultimately defeating.

`Has_many, through:` associations defeated me, and I hated them for it. Relationships between Rails models were one of the last concepts I felt I didn't entirely grasp. They felt clear until 'many to many' and all the functionalities included with them came into play.

My initial idea of this application was not incorrect. I had three models; a User, a Review, and an Album. Users write reviews on albums, an Album has reviews (and thanks to the through association, many Users), and a Review belongs to an Album and a User.

```
# user.rb
has_many :reviews
has_many :albums, through: :reviews

# album.rb
has_many :reviews
has_many :users, through: :reviews

# review.rb
belongs_to :album, optional: true
belongs_to :user
```

Seemed simple, to the point, and didn't require extra logic. That was, until I needed to build the association out for a Review.

For a reason I could not comprehend,  `review.album.user` gave a list of 2 instances of the single user who uploaded the album/wrote the review. Was that because the user uploaded the album but also wrote a review on that album, and I only had one way to relate Albums to Users? I had no idea what was going on at this point and I had to come to terms that this way of associating was incorrect for what I wanted to accomplish.

I quickly realized the way I wrote my User associations was by only relating the User to the Albums they wrote reviews on. But what about the albums the user uploads? Enter => the `source:` key.

**Source specifies which association actually points to where I'm trying to go.**

```
#user.rb
has_many :reviews
has_many :reviewed_albums, through: :reviews, source: :album
has_many :albums

#album.rb
has_many :reviews, :dependent => :destroy
has_many :reviewers, through: :reviews, source: :user
belongs_to :user

#review didn't change
```

I renamed the association for the User to `:reviewed_albums` and sourced it through the album model, and renamed the association for Album to `:reviewers` and sourced it through the user model.

I called it reviewers to not get confused with the method/association `.user` that refers to the creator. I understood that normally, Rails would refer the database table name from the name of the association. Since I'm giving a different name, I have to explicitly give the name of the table I'm referring to, which is the Users table.

The final outcome ends up looking like this:
![](https://i.ibb.co/fHLQ2xM/Screen-Shot-2020-04-26-at-12-54-29-PM.png)

By creating another association, we take a different route to get from album to user (not the direct line in the image.) In order to get to the users that left a review on this album, we have to go through the reviews table. By doing this, we are giving the name (source) of the table so Rails knows where to look for this association.


Done! That was a lot, not to mention it took me a solid 3 days to thoroughly understand everything. Associating my models this way allows me to keep the rest of my app written exactly as-is. I'm truly grateful for this mistake, as I was able to find this solution and it gave me the opportunity to learn about this concept in greater detail.
