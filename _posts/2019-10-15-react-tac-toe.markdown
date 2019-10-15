---
layout: post
title:      "React-Tac-Toe"
date:       2019-10-15 12:46:04 +0000
permalink:  react-tac-toe
---


Recently I decided to create a Rails API/React version of a CLI Tic-Tac-Toe game I created several months ago. First, I generated a Rails API and created the React client within Rails. I used Foreman utility manager and created a Procfile to start up both the Rails' server and the React server.

With the basic setup in place, I went about creating a Game module that would encapsulate all the logic needed to play a full game of tic-tac-toe. The Game class takes in an ID, a board (an array), and turn count. I did this so if a user loads a previous game they can start playing with the appropriate token (either X or O), or if a user creates a new game the same game logic can be applied:

```
export default class Game {
  constructor(id, board = [" ", " ", " ", " ", " ", " ", " ", " ", " "], turnCount = 0) {
    this.id = id
    this.board = board
    this.turnCount = turnCount
  }
}
```

After fleshing out a few methods for the game class the essential logic was up and running, all that was next was to create a grid via CSS, as well as style the overall application. My next step; deploy to Heroku.


