---
layout: post
title:      "Beer Club with jQuery "
date:       2019-04-01 17:53:12 +0000
permalink:  beer_club_with_jquery
---


‘Beer Club’ is a rails app that allows users to create an account, write, and share beer reviews with the community. In addition, as a user writes more reviews, they can earn different medals, thereby increasing their ‘beer cred’ status among the community. In the first implementation of ‘Beer Club’, resources were loaded and render in the traditional manner. By utilizing jQuery, I set out to make many of the resources available on the user show page, which would be added dynamically to the DOM, improving the overall user experience.

The first modification I implemented, using jQuery, was to render a list of all the reviews created by a user on the users’ show page. Moreover, when the user is viewing this index of all their reviews, they can select a single review to see the full text, as well as buttons to edit or delete that review. I created a function—getUserReviews—which handles the get request, and either appends the users reviews to a div located on the user show page or alerts the user that they have not yet written any reviews.

The second modification I worked on followed similar logic. On the beer index page, which lists all the beers ever reviews on ‘Beer Club’, I wanted a user to be able to click a ‘see reviews’ link, which would then render a list of all that beers reviews at the bottom of the same page. Accordingly, I created a getBeerReviews function that operated similarly to the getUserReviews function.

The third and final modification was submitting a new review via ajax. I added an event listener to hijack the submit event of the form, serialized the form data into a JSON using rails serializers, and submitted that data in a post request. If the request was successful, i.e. there were no validation errors on the backend, the returned datatype would be an object as opposed to a string of html. I used this distinction to alert the user if they had improperly submitted the form. Conversely, if the submission was a success, I collected the data returned in the JSON object supplied it to a JavaScript Review Class, which made handling the data much more intuitive. The user would see their new review dynamically appended to a list of ‘past reviews’, which is located on the new review form. Moreover, the user could now submit any amount of reviews without refreshing the page.

