# Week 2 Lab: Build a Responsive Pricing Page with Bootstrap

## Overview:
In this lab, you will again *pair program* with another person to create a responsive CoderSchool Pricing Page using `Bootstrap v4.1`. The goal of this lab is to help you get familiar with all the popular Bootstrap components and utilities. By the end of this lab, you will be surprised of how much less code you need to write to make a responsive website with Bootstrap! 
We will also go over [GitHub Pages](https://pages.github.com/) to help you publish your responsive webpage online.

<img src='https://i.imgur.com/Y0Wub3u.gif' alt='Spotify Demo' />

## Milestone 1: Add Bootstrap to your HTML file
  1. Create a folder named `responsive-with-bootstrap`
  2. Set up and link `style.css` file to `index.html` the same way you did in lab 1
  3. Go to bootstrap [website](https://getbootstrap.com/) and click on 'Get started'
  4. Just focus on the `Quick start` section in the Introduction page. We will link BootstrapCDN directly to our HTML files
  5. Copy and paste the Bootstrap CSS `<link>` into your html `<head>` before all other stylesheets.
  6. Copy and paste the three Bootstrap JavaScript `<script>`s into your html `<body>`, right before the closing `<\body>` tag.
  When a page is rendered, all the external references in `<head>` are loaded first before the content in `<body>` is loaded. We want the stylesheets to be at the `head` so that the styles of pages are already ready when the content is loaded. Loading scripts often takes longer than stylesheets, so we don't want to include scripts in the `head` to slow down the rendering process. Also, most of the scripts are for interaction, and user won't be able to do anything until the page is fully loaded. To optimize the performance, most of the web pages nowsadays have scripts loaded at the end of the `body` tag, after all the content is loaded.
  7. Since Bootstrap's approach is *mobile first*, to ensure proper rendering, add the responsive viewport meta tag to your `<head>`
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  ```
  8. Your `index.html` should be similar to this:
  ```html
  <html>
    <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
      <title>Course Pricing</title>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/css/bootstrap.min.css" integrity="sha384-9gVQ4dYFwwWSjIDZnLEWnxCjeSWFphJiwGPXr1jddIhOegiu1FwO5qRGvFXOdJZ4" crossorigin="anonymous">
      <link rel="stylesheet" href="style.css">
    </head>
    <body>

      <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.0/umd/popper.min.js" integrity="sha384-cs/chFZiN24E4KMATLdqdvsezGxaGsi4hLGOzlXwp5UZB1LY//20VyM2taTB4QvJ" crossorigin="anonymous"></script>
      <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.0/js/bootstrap.min.js" integrity="sha384-uefMccjFJAIv6A+rW+L4AHf99KvxDjWSu1z9VI8SKNVmz4sk7buKt/6v9KI65qnm" crossorigin="anonymous"></script>
    </body>
  </html>
  ```
  Save the changes. 
  Good job! Bootstrap is now fully added to your webpage.

## Milestone 2: Lay out main containers and add favicon
  Last lab, we used `<div>` tag to lay out all the parent containers. This time, let's use [HTML5 semantic elements](https://www.w3schools.com/html/html5_semantic_elements.asp) to create and identify them.
  It totally depends on how you want to design your pricing page, you can either have 3 or 4 parent containers. Since I don't like to have one container wrapped by another container, I will start with 4 containers.
  Add the following code right below the `<body>` tag and above all the Bootstrap scripts.
  ```html
    <nav></nav>
    <header></header>
    <section></section>
    <footer></footer>
  ```
  You may want the `header` (or `footer`) element nested inside the `section` element instead if you want to start out with just 3 containers.
  Now, we have 4 distinct empty containers. If you open the `index.html` now on a web browser, you still see a blank page because there is still no content on the page. 
  The semantic tag names kind of tell us the purpose of each container. We no longer need to give each one of them a specific `id` name (unless you decide to have a second `header` or a second `section`).
  Next, add a CoderSchool favicon to your webpage using this url https://i.imgur.com/hViW80o.png (hint: use `<link>` in `<head>` tag). Feel free to add a different favicon and customize it to your own.

## Milestone 3: Navbar again, but now we make it responsive
  Let us start with our first container: `<nav>`
  The Bootstrap stylesheet applies styling on an element when the element is given a *Bootstrap class name*. 
  1. Now, give the following class names to your `<nav>` element:
  ```html
  <nav class="navbar bg-light border-bottom"></nav>
  ```
  Reload the html file on your web browser to see a subtle change to your top container. There is now a thin horizontal gray line on top of your page. What happened just now is that your semantic `<nav>` element was given some styling from Bootstrap. 
  * `.navbar` provides a wrapper around the element and turns it into a Bootstrap navigation bar
  * `.bg-light` changed the background color of the element
  *  `.border-bottom` provides a border at the bottom of your element
  To understand exactly what styling has really been applied, you can inspect the element in Chrome Developer Tools by right-click on the element and choose 'Inspect'.
  <img src="https://i.imgur.com/D1aNyiH.png" alt="chrome dev tools">
  2. I also want to add a shadow to the navigation bar. However, the search terms "shadow" and "box shadow" don't provide me any result on Bootstrap website. I will have to come up with my own styling for the shadow.
  Add `.box-shadow` to the `<nav>` element.
  In the `style.css` file, add the following: 
  ```css
  .box-shadow { 
    box-shadow: 0 .25rem .75rem rgba(0, 0, 0, .05); 
  }
  ```
  Save and reload the page. Now, there is a shadow for the nav bar.
  3. Next, add a `<div class="container">` inside the `<nav>` element. The `.container` class is one of the main Bootsrap classed for basic layout. Other ones are `.row` and `.col`. `.container` provides a fixed-width container for different breakpoints and center content (auto margin left and right).
  Your code for navbar should look like this now:
  ```html
  <nav class="navbar bg-light border-bottom box-shadow">
    <div class="container">

    </div>
  </nav>
  ```
  4. Now, add a responsive image inside the container using [picture](https://www.w3schools.com/tags/tag_picture.asp) tag and wrap around it with an `<a>` tag to create a hyperlink on the image.
  ```html
  <a class="navbar-brand mr-auto" href="http://www.coderschool.vn/">
    <picture>
      <source media="(min-width: 768px)" srcset="https://svgshare.com/i/6RK.svg">
      <source media="(max-width: 767px)" srcset="https://svgshare.com/i/6P9.svg">
      <img src="https://svgshare.com/i/6P9.svg" alt="CS-responsive" width="180px;">
    </picture>
  </a>
  ```



  
**Explanation:** I give a `height` and a `background-color` to distinguish each div container. I also set the `position` from `static` (default) to `relative` for each div. This position setting allows me to move any child elements within each parent container based on the parent container position and not on the page itself.

**Question:** Using either `position: relative` or `position: absolute` will allow child elements to move around inside the parent container based on the parent container's position. Here, what is the difference between `relative` and `absolute` in this case? What happens if I use `position: absolute` for these containers instead?

Save and reload the index.html file on your Chrome browser. 
Now you can see 7 different containers layed out one on top of another.

<img src='https://i.imgur.com/zWROKej.png' alt='7 containers img' />

## Milestone 4: Create the top navigation bar
<img src='https://i.imgur.com/Jzp39Q3.png' alt='top nav bar full' />

The top navigation bar has four requirements: 
  * Spotify logo on top left
  * Horizontal list of hyperlinks on top right
  * Fixed position on top of the page (BONUS)
  * Transparent background color (BONUS)

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
  **Note:** Depend on your lapton sreen, you may need to change the values of `top`, `left`, and `right` of each element to make sure they are centered on the screen. Use *Page Ruler plugin for Chrome* to get the exact px.

## Milestone 5: Create the hero banner
<img src='https://i.imgur.com/qZCyX6C.png' alt='hero banner full' />

The hero banner need to satisfy the following requirements:
* Linear-gradient background
* Bubble background image
* Center large white text
* Green 'FREE' button
* Transparent 'PREMIUM' button (BONUS)
* Less than and larger than signs on the sides (BONUS)

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
  **Note:** Property `z-index` is used when you want an element to be *in front* or *behind* another element. Try changing z-index to 0 or a negative number to see a difference!
  
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
  
  **Note:** Depend on your laptop screen, you may need to re-position your image using `top` and `left` property in the `#banner img` selector.
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
    letter-spacing: -0.04rem;
  }
  ```
  Save and reload the page. The title text should be white and centered.

  **Bonus:** Apply the correct font-family for the title text
### Green 'FREE' button
  1. In `index.html` file, add a button tag inside the banner container and give it a name `class="btn-free"`
  ```html
  <div id="banner">
    <img src="img/hero-burst.svg" alt="hero-burst img">
    <h1 id="title">Music for everyone.</h1>
    <button class="btn-free">Get spotify free</button>
  </div>
  ```
  2. Give it some styles
  ```css
  .btn-free {
    background-color: #1db954;
    color: white;
    letter-spacing: 2px;
    border-radius: 500px;
    padding: 18px 40px 13px;
    border: 2px solid rgba(50,205,50,.6);
    text-transform: uppercase;
  }
  ```
  You can use the *ColorZilla plugin for Chrome* to get the right green color for the button
  3. Add some effect when mouse is hovered
  ```css
  .btn-free:hover {
    cursor: pointer;
    background-color: #1ed760;
    transition-duration: .5s;
  }
  ```
  4. Move it to the right location. Add the following properties to the `.btn-free` selector
  ```css  
    position: absolute;
    left: 690px;
    top: 380px;
    font-size: 14px;
    font-weight: 700px;
  ```
  **Note:** Depend on your laptop screen, you may need to re-position the button.
  Your final result should look like this:
  <img src="https://i.imgur.com/uJdpfsa.png" alt="banner b">
  
  That should be it for your first lab! If you get up to this point, you can start calling yourself a web designer who can litterally create a replica of any website from scratch! Your next step would be working on the bonus requirements and the remaining containers. The more time you spend working on the lab, the more proficient you can be at web design. Also, when you get stuck at something for awhile, ask around! People will help you or, better yet, book an info session (https://calendly.com/coderschool/30min/04-03-2018) with me to go over the issues :)

## Other Resources
Tools that will help you with designing and developing the landing page:
1. Prettier plugin for VSCode - format and make your code looks prettier
2. ColorZilla plugin for Chrome - detect a pixel color from any page
3. WhatFont plugin for Chrome - detect a font on any page
4. Pesticide plugin for Chrome - detect and outline each element to better see their placements on the page
5. Page Ruler plugin for Chrome - draw a ruler to get pixel dimensions and positioning
