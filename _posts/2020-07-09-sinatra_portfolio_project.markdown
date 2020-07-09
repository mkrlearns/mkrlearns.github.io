---
layout: post
title:      "Sinatra Portfolio Project"
date:       2020-07-09 18:44:10 +0000
permalink:  sinatra_portfolio_project
---


For quite some time I've been looking for a simple timer application that could keep track of how much time I've spent on daily tasks. Something that required no more than a button click to start and stop and was quick and easy to see the progress. It seemed like a good candidate for this project and I proceeded to get in over my head.

In order for this to work the timers needed to keep track of total time in seconds, time remaining, time started, and current state (playing or paused). Every time the play button is pressed I needed to update the state and subtract the current time from the time started to update time remaining, then set time started to the current time. This worked okay in theory, but it took me more time than I'd like to admit to get this working in practice. After realizing that I also had to do these calculations every time the page was loaded and inserting it into `get '/'` I was off to the races.

To present the progress visually I had to use a bit of JS in order to update each of the running timers every second. I'm using HTML 5 progress bars, so I just needed to update the "value" of each to match the percentage of remaining time. The progress bar elements themselves are created with attributes with total time, time remaining, and running state for easy scraping with JS.

I tried to keep everything as clean as possible and contained to a one page layout. I combined the signup & login "pages" into one popup form, used the form element attributes for data validation, and added sinatra-flash for any other errors that the form couldn't catch. All the create, edit, and destroy functions are also tied to popup forms with the same types of validation.

There is one major limitation of the app that I want to come back to at some point: If the page is open on multiple devices or windows, the timers won't update on all pages when they are paused/played. I debated on using AJAX to help with this issue as it has the unique quirk of not following redirects on post commands, but ultimately decided that it was outside the scope of this project.

Ultimately, I got exactly what I wanted. It's a clean, simple, easy to read interface to keep track of my daily tasks. There are things that I would like to change and/or update and I will definitely be coming back to this one as I continue through these courses.
