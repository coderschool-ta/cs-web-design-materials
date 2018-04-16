# Week 1 Lab: Build Spotify Landing Page (Desktop)

## Overview: 
In this lab, you will be [pair programming](https://en.wikipedia.org/wiki/Pair_programming) with another person sitting next to you to create the Spotify [landing page](https://www.spotify.com/vn-en/) from scratch using only HTML and CSS. The goal of this lab is to help you understand the materials that we went over in our first lecture especially around [CSS Box Model](https://www.w3schools.com/css/css_boxmodel.asp) and [CSS Positioning](https://css-tricks.com/almanac/properties/p/position/). After completing the lab, you should be able to create any webpage from scratch quichkly without any issue.

Below is a replica of Spotify Landing page that was developed using only HTML and CSS:

<img src='https://i.imgur.com/Y0Wub3u.gif' alt='Spotify Demo' />

## Milestone 1: Setup environment
At this point, you should have a working Text Editor that you are familiar with. Some of the most popular text editors are: 
* [Visual Studio Code](https://code.visualstudio.com/download) (Recommended)
* [Sublime Text](https://www.sublimetext.com/3)
* [Atom](https://atom.io/)
* [Notepad++](https://notepad-plus-plus.org/download/v7.5.6.html)
* [Vim](https://www.vim.org/download.php)
* [Emacs](https://www.gnu.org/software/emacs/)
* [Brackets](http://brackets.io/)

Alternatively, there are also online Text Editors that let you write code in the browser and see the results instantly. Popular ones are:
* [CodePen](https://codepen.io/) (Recommened)
* [JSFiddle](https://jsfiddle.net/)
* [CSS Deck](http://cssdeck.com/)
* [JS Bin](http://jsbin.com/)

Throughout the course, I will be using mainly Visual Studio Code and CodePen for code demostration.

## Milestone 2: Create 2 files: index.html and style.css, and link them together
* First, create a folder named `spotify`
* In the folder that you just created, create 2 empty files `index.html` and `style.css` 
* In the `index.html`, add the following code: 
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Music for everyone - Spotify</title>
  </head>
  <body>
  </body>
</html>
```
This is the first skeleton of the HTML file. The `<!DOCTYPE html>` declaration means that the HTML file is HTML 5. The `<title>` tag defines a title in the browser toolbar, provides a title for the page when it is added to favorites, and displays a title for the page in search-engine results.
* Now, link the `style.css` with the `index.html` file by adding this code into the html file, below the `<title>` tag:
```html
<link rel="stylesheet" href="style.css">
```
This line of code has to be within the `<head>` tag.

## Milestone 3: Layout all the parent containers
Spotify landing page has 7 parent containers from top to bottom:
1. Navigation bar
2. Banner
3. First white container (white-1)
4. First color container (color-1)
5. Second white container (white-2)
6. Second color container (color-2)
7. Footer
In the `index.html`, add the following code inside the `<body>` tag to add the 7 containers:
```html
  <div id="navbar"> </div>
  <div id="banner"> </div>
  <div id="white-1"> </div>
  <div id="color-1"> </div>
  <div id="white-2"> </div>
  <div id="color-2"> </div>
  <div id="footer"> </div>
```
Each of the container has their own id/name and the name should be easy to understand.
Now, there are 7 distinct containers layed out in the html file.

<img src='https://i.imgur.com/zWROKej.png' alt='7 containers img' />


Now, give them some styling by giving height and background color to each of the container:
In the `style.css`, add the following code:
```css
#navbar { height: 80px; background-color: black }
#banner { height: 660px; background-color: pink }
#white-1 { height: 650px; background-color: white }
#color-1 { height: 600px; background-color: pink }
#white-2 { height: 510px; background-color: white }
#color-2 { height: 750px; background-color: pink }
#footer { height: 500px; background-color: black }
```

Save and reload the index.html file on your Chrome browser. Now you can see 7 different containers layed out one on top of another.

## Milestone 4: Create the top navigation bar
The top navigation bar has the following properties: 
* Spotify logo on left
* Horizontal list of hyperlink on top right
* Fixed position on top of the page
* Transparent background color
In this milestone, I'll walk you through on how to implement the first 3. The last property you can try to implement yourself (hint: google 'transparent background css')
# Spotify logo on left
There is a trick to get all images on a website:
  1. On Chrome, go to https://www.spotify.com/vn-en/
  2. Right click anywhere on the webpage and choose `Inspect`
  3. On the `Network` tab, choose `Img` as your filter
  4. Click Cmd+R or Ctrl+R to reload the page (this will reload all the images)
  5. Go through the list of image names at the bottom-left panel until you find out the Spotify logo
  
  <img src='https://i.imgur.com/DkmNLKW.png' alt='Chrome Developer Tools' />
  6. Right click on the image on the bottom-right panel and choose `Save...`
  7. Now, you have downloaded the Spotify logo in your local computer
  8. Rename it to `spotify-logo.svg`
  9. In the `spotify` folder, create another folder named `img` and put the spotify logo in there. This new folder is the place to store any image that you use for your website.
  10. Reference the 



## Other Resources
Tools that will help you with designing and developing the landing page:
1. Prettier plugin for VSCode - format and make your code looks prettier
2. ColorZilla plugin for Chrome - detect a pixel color from any page
3. WhatFont plugin for Chrome - detect a font on any page
4. Pesticide plugin for Chrome - detect and outline each element to better see their placements on the page
5. Page Ruler plugin for Chrome - draw a ruler to get pixel dimensions and positioning