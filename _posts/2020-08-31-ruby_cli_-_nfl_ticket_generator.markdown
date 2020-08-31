---
layout: post
title:      "Ruby CLI - NFL Ticket Generator"
date:       2020-08-31 17:59:30 +0000
permalink:  ruby_cli_-_nfl_ticket_generator
---

[Medium Article](https://medium.com/@jefftswisher/ruby-cli-nfl-ticket-generator-479a155da390)

Tasked with my first project for Flatiron’s Software Engineering program I decided to first begin with some research on APIs. Now, this wasn’t the first time I had heard of an API but at this point in the program, we had not covered them in any capacity. However, my cohort had been given the opportunity of choosing either an API or Nokogiri to complete our first project.

If you haven’t heard of Nokogiri before, it is a Ruby gem that allows you to parse the HTML of a website and operate on it via CSS selectors to retrieve specific pieces of information. Web scraping with Nokogiri had been covered in the program at this point and I felt comfortable using it thus far.

However, with my current lack of knowledge and the more widespread use of APIs in the professional world I decided to take the option of learning something new. At first, the thought of using an API to get the data I needed was very intimidating, however with the help of Postman and my chosen API’s documentation I ended up creating a pretty cool CLI program.

We were tasked with building a Ruby gem that provides a Command Line Interface (CLI) to an external data source. I decided to use Ticketmaster’s API to build my CLI program. My program allows a user to enter in the name of any NFL team to return all future games for that team provided tickets are actively being sold.

Once the team name has been entered by the user the program makes an API call to retrieve the following info for each available game:

1. Names for both teams in the game
2. Date of game
3. Time of game
4. Game venue
5. Game location — City/State
6. URL — Direct link to the purchasing page for tickets to the game.
Image for post
Image for post
Initial prompt & results of user input.
Image for post
Image for post
Results for selected game.

The Application programming interface or API for short allows my program to access Ticketmaster’s system to search for NFL games based on the query parameters I have set in my API call. The query parameters allowed me to fine-tune the data I wanted to access from their system. Postman was great at allowing me to test these parameters and see exactly what they would return upon making the API call. Postman is a collaboration platform for API development amongst other things. For my needs, I utilized it for exploratory testing to see what values would be returned when the API calls were made.

After reading the Ticketmaster API documentation I knew how to add onto the root URL that would be used for my API call with both my API key and my desired parameters. In Postman I used this URL to send a request to see the values returned to my program. Postman highlights the query parameters that you’re using and allows you to toggle them on/off to see different results from your API call which is a really useful feature.
Image for post
Image for post
Postman Interface — Sample results of API call

Once I was happy with the results from my API calls the real coding began. I wanted my program to return results based on the user’s input. Through my testing in Postman, I knew that I could enter any team name for the “keyword” query parameter when making my calls and I would get the results for that specific team back. At this point, I knew I could then just ask the user for their favorite team throughout the program and then interpolate that input into the URL as the “keyword” when making the API calls, in turn returning all games for the requested team.
Image for post
Image for post
API class. Class method takes in users input as an argument and then interpolates into URL.

The Ticketmaster API returns its data in JavaScript Object Notation (JSON) format, this format being similar to a hash in Ruby. While a hash is formatted using “key”/”value” pairs, JSON is formatted using “name”/”value” pairs. This allowed me to easily iterate over the data set to capture the data I needed for my instance variables for each game object. After each iteration through the data set the above class method creates a new “Games” object until all games have been created for the given team.

The remainder of the coding needed was to manage the game objects being created and creating a CLI interface for the user to utilize when running the program. Overall this project was a great learning experience that helped me step out of my comfort zone to create something tangible that I can show my family and friends. Going forward I would like to restructure the program to allow users to access ticket information for not just NFL games but many of the other mainstream sports as well.

You can also check out the Github Repo.
