---
layout: post
title:      "CLI Data Gem Portfolio Project"
date:       2020-01-03 10:53:27 -0500
permalink:  cli_data_gem_portfolio_project
---

This project was quite the challenge. It took quite some time to land on an idea that both interested me and could fulfill the requirements of the project.

Initially, I wanted to create something that would be able to convert between CSS color codes. While searching for sites to scrape for that project I stumbled upon a deep learning color palette generator called [Colormind](http://colormind.io/). When provided with between one and four colors, [Colormind](http://colormind.io/) uses deep learning to return the remainder of a five color palette. I couldn't help but use this in my project.

## Connecting to the API

Connecting to the [Colormind API](http://colormind.io/api-access/) was fairly easy. Using their instructions and [Curl to Ruby](https://jhawthorn.github.io/curl-to-ruby/) to convert the curl commands into net/http made it a breeze.

The [Colormind API](http://colormind.io/api-access/) only accepts RGB values and only in a certain format, so the challenge here was converting other color codes over to RGB and then modifying the values returned into a formatted array that the API expects.

## Creating the Scraper

In order to convert the color codes provided to RGB I ended up thinking back to my original Idea for this project — converting CSS color codes. To do this I decided to scrape the site [convertingcolors.com](http://convertingcolors.com/). I could have used their provided API as well, but I felt that scraping the site would be more appropriate given the requirements of this project .

[Convertingcolors.com](http://convertingcolors.com/) has a very useful structure to their URLs, essentially providing the color codes within them:

* https://convertingcolors.com/hex-color-6EC3B1.html
* https://convertingcolors.com/rgb-color-110_195_177.html
* https://convertingcolors.com/hsl-color-167_41_60.html

This way I could take the user's input and modify the strings a bit to grab the page I needed. With a bit of scraping I had not only the RGB required for [Colormind's API](http://colormind.io/api-access/), but also the added feature of converting between any HEX, RGB, and HSL color.

## User Experience

I spent a good bit of my time on the design of the menus and making sure that at no point would the user get "stuck" in a menu. I provided as many options to start over or go back as possible.

By using the gem [Rainbow](https://github.com/sickill/rainbow) I was able to improve the style of the menus and provide context for the returned colors:

![Selection Example](http://i.imgur.com/1eRUqMo.png)

![Returned Palettes](https://i.imgur.com/ytcZ2nx.png)

I found Rainbow to be easier to work with than Colorize, which was used in the previous scraper project.

## Exceptions

Since there are multiple ways to represent color codes I tried to account for every exception.

* Hex codes can be represented with a # or without and also as six characters or just three.
* HSL codes can contain percent and degree symbols or none at all.

With some string manipulation and extensive testing I was able to account for each of these cases.

## Conclusion

Though I'm aware that I could have used an API or a gem for color conversions, I think it was important for the project and for myself to create a scraper to do the work, even if it adds to loading times.

I couldn't be happier with how the project turned out and had a good time creating it.

