# reverse-engineering-authentication
week-14 assignment

Reverse Engineering Authentication

Walk-through of Codebase

This app allows users to create an account, log into the account and sign back out securely. All user data is stored in a mysql database.

TECH USED

-   BCRYPTJS :- a secured way to store passwords in your database using password hashing

-   EXPRESS :- Standard server framework for node.js

-   EXPRESS-SESSION :- uses a cookie to store a session id (with an encryption signature) in the user's browser and then, on subsequent requests, uses the value of that cookie to retrieve session information stored on the server.

-   MYSQL2 :- used to serve the use-case of connecting, querying and iterating on results.

-   PASSPORT :- authentication middleware for Node. js

-   PASSPORT-LOCAL :- Passport strategy for authenticating with a username and password

-   SEQUELIZE :- a promise-based Node. js ORM for Postgres, MySQL, MariaDB, SQLite and Microsoft SQL Server.

GETTING STARTED

1.  Clone repository

2.  Create a db called "passport_demo"

3.  Change the credentials in the config file to match your server credentials

4.  Install all npm packages. Run the npm i command in your terminal

5.  Run node server.js in your terminal to connect your server and use the app

FILES EXPLAINED

Config Folder

Config.json :- JSON file containing connection credentials and configuration to connect to the server

passport.js :- code telling passport we want to use a Local Strategy, meaning we want to login with a username/email and password. The file also contains validation to check the email entered is in the database and if so makes sure that the password is the correct one.

MIDDLEWARE FOLDER

isAuthenticated.js :- This is middleware for restricting routes. A user is not allowed to visit if not logged in. If the user is logged in, app continues with the request to the restricted route, however If the user isn't logged in, app redirects them to the login page

Models Folder

index.js :- connects to database and imports users log in data

 User.js :-  requires "bcrypt" for password hashing. File also contains JS that defines what is stored on the database by creating the user model

Public Folder

Html files :- html file for signup, login and members page

JS FOLDER

login.js :- this file gets the references to the form and inputs, validates the form has an entry before submit and clears the input areas once submitted. There is a function that posts the entry to api/login route and redirects users to the members page once successful

member.js :- This file just does a GET request to figure out which user is logged in and updates the HTML on the page

signup.js :- this file gets the references to the form and inputs, validates the form has an entry before submit and clears the input areas once submitted. There is a function that posts the entry to api/signup route and redirects users to the members page once successful

STYLESHEETS FOLDER

Style.css :- styling for the form

Routes Folder

api-routes.js :- routes for signing in, logging out and getting users specific data to be displayed client side

html-routes.js :- routes that check whether user is signed in, whether user already has account and sends them to the correct html page };

server.js :- requires packages, sets up PORT, creates express and middleware, creates routes and syncs database