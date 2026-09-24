# LAMP-Colors-Lab
Colors lab git repository, made after the project was completed

This project involves the purchase of both a DigitalOcean LAMP droplet, as well as a web domain, in order to create a working app that allows users to link colors to specific userIds when logged in.
These colors will persist across all sessions as they directly edit the database that the website uses.

Technologies used :
 Frontend:
   HTML - page structuring 
   CSS - styling
   Javascript - client and API call logic

  Backend: 
    PHP - API endpoints
    JSON - data format passed between front and backends

  Database:
    MySQL - stores the tables for users and colors

  Hosting:
    DigitalOcean droplet - hosts the server
    GoDaddy - DNS
    Apache - web server for the COLORS website
    
In order to setup the web application as a whole:
  1. Provision the server by obtaining a digitalOcean Ubuntu Droplet with a LAMP stack
  2. Configure the web domain, I found godaddy to be the easiest with it's offers for cheap websites
  3. Set up the databases through command prompt or some other terminal interface program (PUTTY or MOBAXterm come to mind, but neither were used)
  4. Configure the API by configuring them for the right overall username, password, and especially webpage (that was a large reason the webpage didn't work at first)
     (Specific credentials can be found at the top of each .php file:   "$conn = new mysqli("localhost", "<db_user>", "<db_password>", "<db_name>");". These must be swapped out with the correct user credentials)
  5. Deploy the frontend HTML, CSS, and JS files to the server in the /var/www/html. Also, add the configured .php files to the LAMPAPI directory.

How to Access:
  go to http://<purchased-domain>/index.html for the main login page. After successfully logging in, colors can be added then searched for corresponding to the userID of the login you used.

  The API endpoints can also be tested directly (e.g. with Postman or curl) by sending a POST request with a JSON body and the Content-Type: application/json header, for example:

      POST http://<your-domain>/LAMPAPI/Login.php
      { "login": "<username>", "password": "<password>" }



  Assumptions:
    - there must be at least one entry in your "users" database for the page 
    to work, as there is no self service user registration
    - the webserver and MySQL database run off the same droplet so the API connects to the database as "localhost"

  Limitations:
    - There application does not use HTTPs
    - passwords are hashed with MD5
    - Frontend uses "XMLHttpRequest" with minimal error handling

  Ai Usage: 
  Claude was used throughout this project for clarification on setup steps and troubleshooting when steps didn't work.
  Claude was also used for assistance in creating this GitHub Depository in order to keep the structure neat and the commits clear and concise
  All information provided by Claude was applied in accordance with class policy
