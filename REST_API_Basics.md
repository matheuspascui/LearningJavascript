# Basics of REST API with JavaScript and Node/Express

## Restful Convention

:arrow_right: GET `/api/customers` <br>
:arrow_right: GET `/api/customers/1` <br>
:arrow_right: PUT `/api/customers/1` <br>
:arrow_right: DELETE `/api/customers/1` <br>
:arrow_right: POST `/api/customers` <br>


## Process to get Up and Running with Express and Node/NPM

- `npm init --yes` :arrow_right: to initialize a json package
- `npm i express` :arrow_right: to install express module


## Building a Web Server with Express

- create an `index.js` file, `server.js`, anything like this
- `const express = require('express')` --> to initialize (instantiate) express
- `const app = express()` --> calling the express function returns an object of type express, which is stored in the variable app
- our variable app (the instance of express function), has a bunch of useful methods (including the 4 most used http verbs)


## Refactoring Routes

Using the `http` module, we define routes as functions and IF a request is '/', we send the home page, etc. With the Express Framework, we simply use the `app.get()`, or `app.delete()`, instead of creating various IFs for each route. <br>
:exclamation: Besides that, we can group routes in separate files according to their related function/type.


## Nodemon and Hot Reload

So far, every time we changed the code and saved, we had to stop the server (with Ctrl + C) and reloading it. With a module called `Nodemon`, we can simply save and it automatically hot reloads our server, with no need for interruptions. <br>
To install it **globally**, `npm i -g nodemon`. <br>
To use Nodemon, **instead of using `node file.js`, we will start our applications with `nodemon file.js`**.


## Environment Variables



