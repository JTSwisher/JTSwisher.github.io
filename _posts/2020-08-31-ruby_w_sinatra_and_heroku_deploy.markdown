---
layout: post
title:      "Ruby w/Sinatra & Heroku Deploy"
date:       2020-08-31 18:01:00 +0000
permalink:  ruby_w_sinatra_and_heroku_deploy
---

[Medium Article](https://medium.com/@jefftswisher/sinatra-app-heroku-57a918f6c5be)

At the time of this article’s writing, I had just wrapped up my second project for Flatiron School’s Software Engineering program. Our task for this project was to create a Sinatra app that incorporated full CRUD(create, read, update & delete) functionality utilizing the Model View Controller software design pattern.
Image for post
Image for post
Frank Sinatra

My project was designed to allow a user to create an account and search for their favorite movie, provide a rating and any other comments and save that movie to their account. This being made possible by the incorporation of an API from TMDb (The movie database.) After the build process for my application was complete I wanted to deploy my app for the world to see without a user having to clown down its repo, install dependencies and run it on their local machine.

Heroku is a cloud hosting platform that was the perfect solution to help me do this. My app was built utilizing Sinatra which is a web application library and domain-specific language written in Ruby. This was not the cause of my issues though, the culprit was the relational database management system I was utilizing within my app - SQLite. Unfortunately for me, Heroku does not support SQLite on their platform. I ended up changing my database management system to PostgreSQL to get my app deployed. Lets go over it below and in the case you encounter the same issues you will be able to bypass them and deploy your app.

    Remove ‘sqlite3' gem and add ‘pg’ gem to gemfile

Image for post
Image for post

2. Remove specified versioning from ‘activerecord’ & ‘sinatra-activerecord’ gems in gemfile if present.
Image for post
Image for post

3. Delete Gemfile.lock and run ‘bundle install’ in terminal.

4. Navigate to your ‘DB’ folder and delete ‘development.sqlite’ , ‘test.sqlite’ & ‘schema.rb’ if those files exist. Ensure you only have a ‘migrate’ folder. Also make sure you are specifying your versioning for your ActiveRecord::Migration
Image for post
Image for post

5. Navigate to your ‘config’ folder and create a file ‘database.yml’ , this is where we will setup our postgres database.
Image for post
Image for post

6. Navigate to your environment.rb file and remove:
Image for post
Image for post

7. Navigate to your ‘config.ru’ file and remove:
Image for post
Image for post

At this point you need to be sure you have the Postgres app installed on your machine. Ensure that the app is running. Once it is running navigate back to your terminal and run the following commands.
Image for post
Image for post
Image for post
Image for post

With Postgres you have to create the databases before you migrate them. When you migrate for the first time you will run ‘rake db:create’ to create the databases. You will only need to run this once unless you drop your databases.

At this point you will have switched form utilizing a ‘sqlite’ database to ‘postgres’ allowing you to now deploy your app and finish migrating your databases in Heroku. I hope this article was helpful in getting your app deployed if you were encountering the same issue as I did.

Check out MyMovieLog

