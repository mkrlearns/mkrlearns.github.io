---
layout: post
title:      "CLI Data Gem Portfolio Project"
date:       2020-01-03 10:53:27 -0500
permalink:  cli_data_gem_portfolio_project
---


This one was quite the challenge. It took quite some time to land on an idea that both interested me and could fulfill the requirements of the project.

Initially I wanted to create something that would be able to convert between CSS color codes, but while searching for sites to scrape for that project I stumbled upon a deep learning color palette generator (http://colormind.io/). I couldn't help but use this in my project.

Colormind when provided with between one and four colors will use deep learning to return the remainder of a five color palette. 

### Connecting to the API

Connecting to the colormind API was easy enough. Using their API instructions and [Curl to Ruby](https://jhawthorn.github.io/curl-to-ruby/) to convert the curl commands into net/http made it a breeze.

The API only accepted RGB values and in a certain format, so the challenge here was converting other color codes over to RGB and then modifying the values returned to an array the API expected.

### Creating the Scraper

In order to convert the color codes provided to RGB I ended back on the original Idea for this project, converting CSS color codes. To do this I decided to scrape the site http://convertingcolors.com/. I could have used their provided API as well, but I felt that scraping the site would be more appropriate for this project's requirements.

convertingcolors.com has a very useful structure to their URLs, essentially providing the color codes within them:

* https://convertingcolors.com/hex-color-6EC3B1.html
* https://convertingcolors.com/rgb-color-110_195_177.html
* https://convertingcolors.com/hsl-color-167_41_60.html

This way I could take the user's input and modify the strings a bit to grab the page I needed. With a bit of scraping I had not only the RGB required for colormind's API, but essentially an added feature: converting between any HEX, RGB, and HSL color.

### User Experience

I spent most of my time on the design of the menus and making sure that at no point would the user get "stuck" in a menu. I provided as many options to start over or go back as possible. By using the gem [Rainbow](https://github.com/sickill/rainbow) I was able to make things look good and provide context for the returned colors:

![Selection Example](http://i.imgur.com/1eRUqMo.png)

![Returned Palettes](https://i.imgur.com/ytcZ2nx.png)

I found Rainbow to be easier to work with than Colorize (used in the previous scraper project).

### Exceptions

Since there are multiple ways to represent color codes, I tried to account for every exception.

* Hex codes can be represented with a # or without and also as six characters or just three.
* HSL codes can contain percent and degree symbols or not.

With some fancy string manipulation and tests I was able to account for each of these cases.


### Conclusion

Though I'm aware that I could have used an API or a gem for color conversions, I think it was important for the project and for myself to create a scraper to do the work. 

I couldn't be happier with how the project turned out and generally had a good time creating it.

