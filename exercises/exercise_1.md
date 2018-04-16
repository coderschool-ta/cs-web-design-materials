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

Throughout the course, I will be using mainly **Visual Studio Code** and **CodePen** for code demostration.

## Milestone 2: Link style.css file to index.html file
  1. Create a folder named `spotify`
  2. In the folder that you just created, create 2 empty files `index.html` and `style.css` 
  3. In the `index.html`, add the following code: 
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
  **Explanation:** This is the first skeleton of the HTML file. The `<!DOCTYPE html>` declaration means that the HTML file is HTML 5. The `<title>` tag defines a title in the browser toolbar, provides a title for the page when it is added to favorites, and displays a title for the page in search-engine results.
  Now, link the `style.css` with the `index.html` file by adding this code into the html file, below the `<title>` tag:
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

Now, give them some styling by giving height and background color to each of the container:
In the `style.css`, add the following code:
  ```css
  #navbar { height: 80px; background-color: black; position: relative; }
  #banner { height: 660px; background-color: pink; position: relative; }
  #white-1 { height: 650px; background-color: white; position: relative; }
  #color-1 { height: 600px; background-color: pink; position: relative; }
  #white-2 { height: 510px; background-color: white; position: relative; }
  #color-2 { height: 750px; background-color: pink; position: relative; }
  #footer { height: 500px; background-color: black; position: relative; }
  ```
**Explanation:** I give a `height` and a `background-color` to distinguish each div container. I also set the `position` from `static` (default) to `relative` for each div. This position setting allows me to move any child elements within each parent container based on the parent container position and not on the page itself.
**Question:** Using either `position: relative` or `position: absolute` will allow child elements to move around inside the parent container based on the parent container's position. Here, what is the difference between `relative` and `absolute` in this case? What happens if I use `position: absolute` for these containers instead?

Save and reload the index.html file on your Chrome browser. Now you can see 7 different containers layed out one on top of another.

<img src='https://i.imgur.com/zWROKej.png' alt='7 containers img' />

## Milestone 4: Create the top navigation bar
<img src='https://i.imgur.com/Jzp39Q3.png' alt='top nav bar full' />

The top navigation bar has four requirements: 
  * Spotify logo on top left
  * Horizontal list of hyperlinks on top right
  * Fixed position on top of the page
  * Transparent background color
In this milestone, I'll walk you through on how to implement the first two. 
The last two requirements you can try to implement yourself (hint: google 'fixed position css' and 'transparent background css').
### Spotify logo on top left
There is a trick to get all images on a website:
  <img src='https://i.imgur.com/DkmNLKW.png' alt='Chrome Developer Tools' />
  1. On Chrome, go to https://www.spotify.com/vn-en/
  2. Right click anywhere on the webpage and choose `Inspect`
  3. On the `Network` tab, choose `Img` as your filter
  4. Click Cmd+R or Ctrl+R to reload the page (this will reload all the images)
  5. Go through the list of image names at the bottom-left panel until you find out the Spotify logo
  6. Right click on the image on the bottom-right panel and choose `Save...`
  7. Now, you have downloaded the Spotify logo in your local computer
  8. Rename it to `spotify-logo.svg`
  9. In the `spotify` folder, create another folder named `img` and put the spotify logo in there. This new folder is the place to store any image that you use for your website.
  10. Add this line of code inside your `#navbar` to add the Spotify logo
  ```html
  <div id="navbar">
    <img class="spotify-logo" src="img/spotify-logo.svg" alt="spotify-logo">
  </div>
  ```
  11. Save the `index.html` file and reload the page on Chrome. Notice that the logo doesn't have the right size and right location.
  12. In the `style.css`, add the following code at the bottom to style the Spotify logo:
  ```css
  #navbar .spotify-logo {
    width: 132px;
    position: absolute;
    top: 20px;
    left: 20%;
  }
  ```
  **Explanation:** I apply `170px` to the `width` property of the logo. I also changed the position of the logo from `static` (default) to `absolute`. This position setting allows me to move the logo around using `top`, `right`, `left`, and `bottom` properties based on the parent container's position which is the `#navbar div`. Here, I moved the logo from the top by `20px`, and from the left by `20%`.
  **Question:** What is the difference between `px` and `%`?
### Horizontal list of hyperlinks on top right
  1. In the `index.html` file, add a list of hyperlinks into the `#navbar`. It should look like this:
  ```html
  <div id="navbar"> 
    <img class="spotify-logo" src="img/spotify-logo.svg" alt="spotify-logo">
    <ul>
      <li><a href="">Premium</a></li>
      <li><a href="">Help</a></li>
      <li><a href="">Download</a></li>
      <li><a>|</a></li>
      <li><a href="">Sign up</a></li>
      <li><a href="">Log In</a></li>
    </ul>  
  </div>
  ```
  Notice that this is an unordered vertical list of hyperlinks. Each of the hyperlinks has a defaut style: *blue color* and *underlined*. We need to change the style for this list.
  
  2. In the `style.css` file, add the following code at the bottom:
  ```css
  #navbar a {
    color: white;
    text-decoration: none;
  }
  ```
  This css code changes the style of all hyperlinks in the `#navbar` container: *white color* and *no underline*.
  
  3. Next, add the following at the bottom:
  ```css
  #navbar ul li {
    display: inline;
    margin: 15px;
  }
  ```
  `display: inline;` changes the direction of the list from vertical to horizontal, and `margin: 30px;` adds extra space between each of the hyperlink.
  4. Now, we need to re-locate the list by moving the whole list to the right. Add the following code:
  ```css
  ul {
    position: absolute;
    top: 15px;
    right: 20%;
    font-size: 16px;
    font-weight: 700;
  }
  ```
  Bam! Now you got the horizontal list of hyperlinks on top right. The top bar should look like below:
  <img src='https://i.imgur.com/gbAhUeb.png' alt='top nav bar' />
  **Note:** You may need to change the values of `top`, `left`, and `right` of each element to make sure they are centered on the screen. Use Page Ruler plugin for Chrome to get the exact px.

## Milestone 5: Create the hero banner
<img src='https://i.imgur.com/qZCyX6C.png' alt='hero banner full' />

The hero banner need to satisfy the following requirements:
* Linear-gradient background
* Bubble background image
* Center large white text
* Green 'FREE' button
* Transparent 'PREMIUM' button
* Less than and larger than signs on the sides
In this milestone, I'll walk you through the top three. The last two requirements you can try to implement yourself.
### Linear-gradient background
  1. On the Spotify original page, locate your mouse inside the banner. Right-click and select 'Inspect' to open the Chrome Developer Tools
  2. On the `Elements` tab, look for a div "wrap" i.e. `<div class="wrap">`
  3. Click on the div to open the corresponding styles on the right panel, and look for the selector `.wrap`
  ```css
  .index-homepage .wrap {
    background-color: #f037a5;
    background: -webkit-gradient(linear,left top,left bottom,color-stop(-60%,#f037a5),color-stop(140%,#fae62d));
    background: linear-gradient(#f037a5 -60%,#fae62d 140%);
  }
  ```
  Here you only need the 3rd property: `background: linear-gradient(#f037a5 -60%,#fae62d 140%);`
  4. Copy the 3rd property and replace the code with the pink background color in the `#banner` selector in your `style.css` file. The selector should look like this:
  ```css
  #banner {
    height: 660px;
    background: linear-gradient(#f037a5 -60%,#fae62d 140%);background-color: pink;
    position: relative;
  }
  ```
  Save and reload your page on Chrome. Now you should get the same gradient background.
### Bubble background image
  1. Using the same trick to get all the images. This time, you want to look for a svg image named `hero-burst.svg`
  2. Download and save it to your img directory (same place as where you saved your spotify logo)
  3. Add the image to your banner container in `index.html`
  ```html
  <div id="banner">
    <img src="img/hero-burst.svg" alt="hero-burst img">
  </div>
  ```
  Save and reload your page on Chrome. The image is added but it doesn't have the right size and position.
  4. In `style.css`, add the following code to correct the img size and position
  ```css
  #banner img {
    width: 80%;
    position: absolute;
    left: 15%;
    top: -85%;
    z-index: 1;
  }
  ```
  The image now has the right size and position. However, because its position was changed from `static` to `absolute`. The image is no longer contained inside the parent container `#banner`. It overflows into the top and bottom container. To fix this problem, add `overflow: hidden;` property to `#banner` selector to hide the overflow parts of the image. The selector should look like this:
  ```css
  #banner {
    height: 660px;
    background: linear-gradient(#f037a5 -60%,#fae62d 140%);
    position: relative;
    overflow: hidden;
  }
  ```
  Save and reload the page. The image should look exactly like how it looks in the original Spotify landing page.
  <img src="https://i.imgur.com/3EVEUZW.png" alt="banner a">
  
  **Note:** You may need to re-position your image using `top` and `left` property in the `#banner img` selector.
### Center large white text 
  1. In `index.html` file, add an h1 heading inside the banner container, give it an `id="title"`
  ```html
  <div id="banner">
    <img src="img/hero-burst.svg" alt="hero-burst img">
    <h1 id="title">Music for everyone.</h1>
  </div>
  ```
  2. Now, we need to give some styles to the `#title`. Open your `style.css` and add the following to the bottom:
  ```css
  #banner #title {
    color: white;
    position: relative;
    text-align: center;
    top: 200px;
    font-size: 80px;
    font-weight: 900px;
    letter-spacing: -0.04em;
  }
  ```
  Save and reload the page. The title text should be white and centered.
  **Bonus:** Apply the correct font-family for the title text
### Green 'FREE' button


## Other Resources
Tools that will help you with designing and developing the landing page:
1. Prettier plugin for VSCode - format and make your code looks prettier
2. ColorZilla plugin for Chrome - detect a pixel color from any page
3. WhatFont plugin for Chrome - detect a font on any page
4. Pesticide plugin for Chrome - detect and outline each element to better see their placements on the page
5. Page Ruler plugin for Chrome - draw a ruler to get pixel dimensions and positioning