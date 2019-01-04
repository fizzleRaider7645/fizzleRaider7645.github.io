---
layout: post
title:      "What I Like Most About ActiveRecord"
date:       2019-01-04 18:27:39 +0000
permalink:  what_i_like_most_about_activerecord
---


What's the most important thing to understand about ORMs and ActiveRecord? It’s a tougher question to answer than I originally anticipated. For one, ActiveRecord’s associations abstract away a lot of work, doing away with the need to define instance variables, not to mention all of the built-in methods that ActiveRecord provides, as well. These features cut down the need to write repetitious code, which can sometimes lead to problems. Wrapping SQL queries in Ruby code allows us to persist data and avoid repeatedly dipping into the database, which is also tremendously useful. However, if I had to choose one aspect of ActiveRecord that is most important, it would be the logical patterns it offers developers that make interacting with a database more intuitive.

Without ActiveRecord developers would either have to use raw SQL or write their own custom methods. SQL queries can of course become complex and require the same code to be written over and over, which from a design perspective, is not optimal. This will hinder collaboration with other developers, as the code will be that much more cumbersome. Moreover, if all developers had to write their own ORM the lack of conventions would necessitate that all developers learn the syntax and conventions of the ORM used in a particular application. Again, this would hinder the possibility of collaboration, and it would greatly increase workloads.

In sum, the conventions and logical design patterns that ActiveRecord provides makes interacting with a database intuitive. To no longer have to think about how to access the data you want, and to be able to retrieve it with less, and more semantic code, is invaluable and has so far been what I found to be most important.  

