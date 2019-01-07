---
layout: post
title:      "My Sinatra Project & Process"
date:       2019-01-07 13:56:51 +0000
permalink:  my_sinatra_project_and_process
---


In keeping with a basketball theme, my first Sinatra application was a basic version of fantasy basketball. I have not yet implemented any of the game features, however, the majority of the essential components are there. I determined that along with a User model there would be a Team and a Player model. Once the models and their relationships were sketched out, my first task was to setup the application architecture. After a bit of trial and error and few tutorials I was ready to create my migrations.

Each user has a username, email, and password digest. A player has a name and a team id. A team has a name, user id, and roster spots. The associations are as follows: a user has a team; a team belongs to a user and has many players; a player belongs to a team. With the migrations complete and the associations established I created a scraper class that got all of the current NBA players to fill the players table. I then worked on the controllers and views simultaneously, staring with the users. I repeated the same process with teams, “playing catch” between my forms and views. 

The teams’ patch action was where the bulk of my time was spent. The corresponding form can edit a team name and allow a user to create a custom player that will be placed on their roster, so long as they have enough roster spots. In addition, there is a checkbox where a user can select any of the available NBA players, so long as they have the spots and they have not yet been selected by another user.

Unlike users and teams, I did not implement any player views or controllers. This is because I did not want a user to be able to edit or delete a player. Moreover, if I were to create a show page for an individual player, I would need to scrape more data from the web to populate the view with enough information to make rendering a player show page meaningful. I plan to implement the player controllers/views with relevant data, but for the purposes of this project I did not want to get bogged down too much in extraneous detail.

