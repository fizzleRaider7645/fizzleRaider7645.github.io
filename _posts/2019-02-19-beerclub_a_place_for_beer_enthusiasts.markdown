---
layout: post
title:      "BeerClub: A Place for Beer Enthusiasts"
date:       2019-02-19 17:38:46 +0000
permalink:  beerclub_a_place_for_beer_enthusiasts
---

For my Rails project I decided to change up the subject matter. I'm a big Boston Celtics fan, and my previous two projects had been basketball-related. However, over the past few months, the Celtics' level of play has fallen way below preseason expectations, and the thought of basketball just made me depressed; I needed a beer. After a sip or two a deep feeling of reassurance swept over me; beer is always good and would never let me down, so at least there’s that… 

I decided to create BeerClub, a web app that allows users to write and share reviews about beer with their friends. In addition, users can win medals, thereby increasing their ‘beer cred’, if they review beers that meet certain criteria, i.e., review a beer over 12% ABV. My first step was to flesh out the database. There would be a users’ table and a beers’ table, which have a has many to has many relationship through a Reviews’ table. I also needed to create a medals’ table and medals users’ join table, to implement a has many to has many relationship between medals and users.

The next step was to create the custom methods I would need for the user model. The majority of these methods dealt with determining if a user was eligible for a medal, and then calling on a medal class method to award the correct medal and update that user’s ‘beer cred. I also added a custom method on the beer class to return the average rating for a beer.

I then turned my focus to the controllers and views. The most difficult action to implement was ‘create’ in the reviews’ controller. My idea was that upon submission of a new review, a beer would either be found, or created, and associated with that review. My first attempt at implementing this was a success, however, the controller was too overcrowded and I needed to figure out a way to slim it down. Hence, I decided to utilize accepts_nested_attributes_for: beer. The power of this tool is still somewhat befuddling, so there was a lot of trial and error correctly setting the strong params for a review, but that was nothing compared to getting the setter method, beer_attributes=(beer_attributes), to function properly.

Beyond the review controller actions, what I found to be deceptively difficult was creating the schema (the mess in my migrations folder is testament to that). It is important to be diligent in planning out what will be included in the project’s tables, how they relate, and what data types will be needed. However, I have also found that what your database really needs, sometimes, becomes clearer only after you’ve started working on your models.

