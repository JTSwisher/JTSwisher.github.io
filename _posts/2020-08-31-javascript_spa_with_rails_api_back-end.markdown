---
layout: post
title:      "JavaScript SPA with Rails API Back-end"
date:       2020-08-31 18:03:24 +0000
permalink:  javascript_spa_with_rails_api_back-end
---

[Medium Article ](https://medium.com/@jefftswisher/gif-book-f87e205064b7)

After completing the JavaScript portion of Flatiron Schools engineering program and before we got to dive into the React framework we were tasked with building a SPA(Single Page Application) showcasing our newfound knowledge of the language. This application was required to utilize a pure JavaScript, HTML & CSS front end with a Rails API back end.

For my project I decided on creating an app that would allow a user to search for GIFs utilizing the GIPHY API and store their favorites to their account. Additionally through the use of the Twilio API the user would be provided the ability to send a GIF via SMS text to their desired recipient. Below I walk through the surprisingly easy integration of what I thought would be the most difficult aspect of my app, SMS messaging via Twilio.
Image for post
Image for post
GIfBook User Interface

The Twilio API can be easily integrated into a Rails application through the use of the Twilio Ruby helper library by installing the ‘twilio-ruby’ gem. After the gem was installed I integrated the Twilio client into my message model as a class method. In this method I needed to initialize the Twilio client and authenticate via the provided ‘account_sid’ & ‘auth_token’ I was given by Twilio. I was then able to call the ‘messages.create’ methods on the ‘client’ while passing in the associated arguments to include the phone number for the recipient, the message ‘body,’ and the associated URL for the GIF provided by the end user.
Image for post
Image for post
Class method to create and send new SMS text.

The ‘new_message’ class method gets called from the create action in the message controller when an associated POST fetch request is made by the user on the front end. The form on the front end captures the data passed in by the user via an event listener listening for the ‘submit’ event of the form. Once the event is triggered the parameters then get passed into the ‘create’ action in the Message controller via the ‘createMessage’ function in the main JavaScript file. This sequence of events then fires off the SMS message to the recipient.
Image for post
Image for post

Having never worked with Twilio before it was something I wanted to integrate into my app as I like to test my knowledge working with new systems and implementations that I am unfamiliar with. The integration of this feature was a last priority for me as I wanted the MVP up and running as quick as possible and I anticipated a lot more work then what was actually required to get it up and running. Thanks go to Twilio’s helper library, and ill be looking for something new and more difficult for the next project!

Check out the REPO here!

