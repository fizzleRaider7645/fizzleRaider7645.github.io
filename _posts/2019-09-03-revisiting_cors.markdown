---
layout: post
title:      "Revisiting CORS"
date:       2019-09-03 12:16:25 +0000
permalink:  revisiting_cors
---


Recently, I’ve been working on a new React app called [True Taste](http://https://github.com/fizzleRaider7645/true-taste). In short, True Taste will generate a new restaurant/business rating based on the ratings collected by several sources (Yelp and Zomato for now), as well as sentiment analysis applied to the actual written reviews. However, soon after implementing the API clients, I ran headlong into CORS issue, so I figured it was a good time to revisit CORS and provide a short overview.

What is the big deal: Basically, the reason CORS is security—it’s a standard that browsers use to protect themselves from loading potentially hazardous assets. With all of the data, and origins of said data that modern websites rely on, it makes sense that we should be careful about what data we’re consuming, otherwise we might mistakenly introduce malicious software into our machine.

What is CORS: Short for “Cross-Origin Resource Sharing” is the standard by which different domains can access resources. These resources are most commonly stylesheets, scripts, images, etc., but can also be data retrieved from APIs. CORS defines what origins can access or modify resources on a server. In regard to React, there are several ways to overcome CORS issues.

In your request headers, you can add the following: Access-Control-Allow-Origin: *

Adding this ‘wildcard value’ will allow all domains to access the server’s resources, however, this can be risky and gives rise to potential issues down the road.

Another way to deal with CORS, and this is route I chose, is to create a proxy server using Node.js/Express. As David Katz writes in [3 Ways to Fix the CORS Error — and How the Access-Control-Allow-Origin Header Works:](http://https://medium.com/@dtkatz/3-ways-to-fix-the-cors-error-and-how-access-control-allow-origin-works-d97d55946d9)

> How does this work? The proxy uses express middleware to apply an Access-Control-Allow-Origin: * header to every response from the server. At its own jokes/random GET endpoint, the proxy requests a random joke from another server. The same-origin policy doesn’t step in to block the request, even though the domains are different. After all, this is a server-to-server request. Finally, the proxy creates a response to the original requester (an app on the browser) consisting of the resulting data and the middleware-applied Access-Control-Allow-Origin: * header.

[This](http://https://medium.com/@maison.moa/setting-up-an-express-backend-server-for-create-react-app-bc7620b20a61) is a great resource for creating your first React proxy server, and with the proxy server in place you should no longer encounter the CORS issues that can be such a bottleneck for new developers trying to get their frontend up and running.

