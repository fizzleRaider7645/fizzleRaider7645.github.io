---
layout: post
title:      "CelticsRoster: My Project Overview"
date:       2018-10-31 17:02:43 +0000
permalink:  celticsroster_my_project_overview
---


Figuring out what my project should be centered on was easy enough. The Boston Celtics were playing in the background as I was reading the project instructions, and I’m a big fan. I began looking for sites to scrape and decided that my gem would list the current Celtics’ roster—allow the user to select a player—and then display that player’s stats from the previous game they played.

Having fleshed out the general concept, I focused on creating the CLI from the perspective of the user. I defined a CLI Class and created the methods that would output information to the user and get user input. Once I had a functioning skeleton, I zipped all of the CLI methods in a single ‘call’ method.

My next step was to create a Player Class to store all of the necessary information about each player. Every player should have a name, number, and position, so these became my instance variables. In addition, each player also needed a URL instance variable to store the link to their individual stats page. When a player is instantiated, it is automatically shoveled into a Class variable called ‘full_roster’, which holds all of the players currently on Celtics’ roster.

I then turned my focus to defining the scraper methods that would get the data I needed to instantiate my players. I did not want to clutter the Player Class with the scraper logic, so I defined a separate Scraper Class. The actual scraping was the hardest part of the project. There was a lot of trial and error, and I spent the majority of my time in pry. Once I got the data I wanted, I defined a Class method that retrieved the necessary data and created a new Player object with it.

Now that I could instantiate players, I defined another Class method that scraped the URL instance variable that each player object has, thereby retrieving that players stats from the previous game. Everything functioned, but I wanted to add color and banner art to the interface. I found ‘tty-font’ and ‘pastel, two gems that made accomplishing this easy. In addition, I scraped another site to collect quotes for the great Celtics coach/general manager, Red Auerbach. Now every time a user exits the program a random quote from Red is outputted as a way of signing off. 

