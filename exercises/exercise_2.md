# Week 2 Lab: Build a Responsive Pricing Page with Bootstrap

## Overview:
In this lab, you will again *pair program* with another person to create a responsive CoderSchool Pricing Page using `Bootstrap v4.1`. The goal of this lab is to help you get familiar with all the popular Bootstrap components and utilities. By the end of this lab, you will be surprised of how much less code you need to write to make a responsive website with Bootstrap! 

We will also go over [GitHub Pages](https://pages.github.com/) to help you publish your responsive webpage online.

Final result: http://www.buihdk.com/pricing-bootstrap-example/

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

## Milestone 3: Responsive logo on left <nav>
  Let us start with our first container: `<nav>`
  The Bootstrap stylesheet applies styling on an element when the element is given a *Bootstrap class name*. 
  1. Now, give the following class names to your `<nav>` element:
  ```html
  <nav class="navbar bg-light border-bottom"></nav>
  ```
  Reload the html file on your web browser to see a subtle change to your top container. There is now a thin horizontal gray line on top of your page. What happened just now is that your semantic `<nav>` element was given some styling from Bootstrap. 
  * `.navbar` provides a wrapper around the element and turns it into a [Bootstrap navigation bar](https://getbootstrap.com/docs/4.0/components/navbar/)
  * `.bg-light` changed the [background color](https://getbootstrap.com/docs/4.0/utilities/colors/#background-color) of the element
  *  `.border-bottom` provides a [border](http://getbootstrap.com/docs/4.0/utilities/borders/) at the bottom of your element
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

  3. Next, add a `<div class="container">` inside the `<nav>` element. The `.container` class is one of the main Bootsrap classed for basic layout. Other classes for Bootstrap basic layout are `.row` and `.col`. These classes have to be used in a correct order (container > row > col) to follow Bootstrap default [grid system](http://getbootstrap.com/docs/4.0/layout/grid/).
  `.container` provides a fixed-width [container](http://getbootstrap.com/docs/4.0/layout/overview/) for different breakpoints and center content (auto margin left and right).
  Your code for navbar should look like this now:
  ```html
  <nav class="navbar bg-light border-bottom box-shadow">
    <div class="container">

    </div>
  </nav>
  ```

  4. Now, add a responsive image inside the container using [picture](https://www.w3schools.com/tags/tag_picture.asp) tag and wrap around it with an `<a>` tag to create a hyperlink on the image.
  ```html
  <a class="navbar-brand" href="http://www.coderschool.vn/">
    <picture>
      <source media="(min-width: 768px)" srcset="https://svgshare.com/i/6RK.svg">
      <source media="(max-width: 767px)" srcset="https://svgshare.com/i/6P9.svg">
      <img src="https://svgshare.com/i/6P9.svg" alt="CS-responsive" width="180px;">
    </picture>
  </a>
  ```
  Save and reload your browser. Try resizing your page horizontally and see the logo changes when the *viewport* is smaller or larger.
  
## Milestone 4: Responsive links on right <nav>
  We got the left of the navbar, the only thing left is the navigation links on the right. Even though the CoderSchool logo is responsive, the navbar itself is not responsive yet. 
  1. To make it responsive, add the following class to the `<nav>` element: `.navbar-expand-lg`. 
  2. Then, add `.navbar-light` to the `<nav>` to make the color easy to see, and `.fixed-top` to make the navbar fixed at the top of the page.
  3. Finally, add the following code inside the `<nav>` and below the hyperlink logo:
  ```html
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent"
    aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav ml-auto">
        <li class="nav-item ml-3 pt-1"><a class="nav-link text-uppercase" href="#">Our Classes</a></li>
        <li class="nav-item ml-3 pt-1"><a class="nav-link text-uppercase" href="#">Recent Projects</a></li>
        <li class="nav-item ml-3 pt-1"><a class="nav-link text-uppercase" href="#">About</a></li>
    </ul>
  </div>
  ```
  Don't worry too much about the attributes inside the button for now. These are used to work with top navigation bar only.
  Quick explanation for some of the class:
  * `.ml-auto` applies **auto** to `margin-left`. This moves the navigation links to the right
  * `.ml-3` applies **1rem** to `margin-left` of each `<li>` element
  * `.pt-1` applies **.25rem** to `padding-top` of each `<li>` element
  Save and reload your browser. Your navbar is now fully responsive! (Notice that your navbar now is very similar to the coderschool.vn's navbar)

  In the code about, there are two things: a `button` and a `div`. When the screen is `lg` (min-width: 992px), then the `div` is displayed with a list of horizontal hyperlinks. When the screen is smaller than 992px, then a hamburger `button` is shown instead. Clicking on the button will display the list of hyperlinks vertically.
  
## Milestone 5: Simple fix on the <header>
  There aren't much in the `<header>` tag compared to the `<nav>` tag and `<section>` tag.
  1. Add the following classes to the `<header>` tag
  ```html
  <header class="text-center mx-auto mt-5 py-5">
  ```
  Below is a brief explanation for each of the class:
  * `.text-center` applies **center** to `text-align`
  * `.mx-auto` applies **auto** to `margin-left` and `margin-right`
  * `.mt-5` applies **3rem** to `margin-top`
  * `.py-4` applies **3rem** to `padding-top` and `padding-bottom`
  2. Now, add the content to the `header`
  ```html
    <img class="my-2" src="https://i.imgur.com/hViW80o.png" alt="CS-logo">
    <h1 class="display-4 mb-4 text-danger font-weight-normal">Course Pricing</h1>
    <h4>Top-Rated Programming Courses Starting April 2018</h4>
    <p class="lead">Designed to help talented programmers to meet and learn new technologies fast. Meet twice a week from 7 to 9 PM and
        build real projects and get real experience.</p>
  ```
  Can you now guess what styling do `.my-2`, `.mb-4`, and `.font-weight-normal` apply to an element? 
  The other classes:
  * `.display-4` changes `font-size`, `font-weight`, and `line-height`
  * `.text-danger` applies **#dc3545** (red) to `color`
  * `.lead` changes `font-size` and `font-weight`
  3. We also want to wrap the `<p>` text around the center only. To do that, add this to the `style.css`
  ```css
  header { max-width: 600px; }
  ```
  Save and reload the browser, the text now fits nicely in the center.

## Milestone 6: Add product cards to <section>
  This is the fun part of the lab, we will add three different [cards](https://getbootstrap.com/docs/4.0/components/card/) with a price tag for three different coding courses being offered at CoderSchool.
  1. First, let's make the `<section>` as a container by adding the `.container` class to the element. Now, all the cards will be centered in the middle.
  2. Since we want to add more than 1 `card`, let's add a `.card-deck` container to make the list of cards itself responsive. Add the following code inside the `<section>` tag:
  ```html
  <div class="card-deck text-center">

  </div>
  ```
  3. Then, add 3 empty cards inside the `.card-deck`. Also, give some `margin-bottom` and `box-shadow` to each card.
  ```html
  <div class="card mb-4 box-shadow">
    <div class="card-header"></div>
    <div class="card-body"></div>
    <div class="card-footer"></div>
  </div>
  <div class="card mb-4 box-shadow">
    <div class="card-header"></div>
    <div class="card-body"></div>
    <div class="card-footer"></div>
  </div>
  <div class="card mb-4 box-shadow">
    <div class="card-header"></div>
    <div class="card-body"></div>
    <div class="card-footer"></div>
  </div>
  ```
  Now, let's add some content to each of the card. Currently, there are 2 courses being offered at CoderSchool: **Web Design Bootcamp** and **React + React Native**. One **Data Science** course will be offered soon in the near future.
  4. Start with the `.card-header`, add a banner img for each of the card:
  ```html
  <img src="https://svgshare.com/i/6Rb.svg" alt="web-banner" width="120px">
  <img src="https://i.imgur.com/gBBbwgH.png" alt="react-banner" width="120px">
  <img src="https://i.imgur.com/lLtWDST.png" alt="data-banner" width="120px">
  ```
  Also, add `.bg-transparent` to `.card-header` to change the background color
  5. Next, let's add the course details in the `.card-body`. Add the following for the **Web Design Bootcamp** card:
  ```html
  <h3 class="card-title">Web Design Bootcamp</h3>
  <p class="card-text font-weight-bold mb-auto">5 weeks, 7-9PM Tu/Th, starts April 17th</p>
  <ul class="list-unstyled my-4">
      <li>Build portfolio from scratch</li>
      <li>Responsive with Bootstrap</li>
      <li>Customize with Wordpress</li>
      <li>Mentoring support</li>
  </ul>
  <h3>4.9M VND
      <small class="text-muted">/ course</small>
  </h3>
  ```
  Also, add `.d-flex` and `.flex-column` to `.card-body` to enable `flex` behavior vertically.
  This is what you should get now []
  Do the same thing for React and Data cards. You can look here for more content http://www.buihdk.com/pricing-bootstrap-example/
  Notice that the <ul> elements of 3 cards are at the same level horizontally. This is the work of `.mb-auto` on `<p>` tag and *flex vertically* on `.card-body`
  6. The last thing we need to work on now is the `.card-footer`. We want them to either 'Check out' the current courses or 'Learn more' on the upcoming courses. When they click on the 'Check out' button, we want to direct them to the Checkout form; and when they click on the 'Learn more' button, we want to direct them to another informative page.
  Add the following inside **Web Design** and **React** `.card-footer`
  ```html
  <a class="btn btn-lg btn-danger" href="http://www.buihdk.com/pricing-bootstrap-example/checkout.html">Check out</a>
  ```
  Then, add the following inside **Data** `.card-footer`
  ```html
  <a class="btn btn-lg btn-danger" href="http://courses.coderschool.vn/data-science" target="_blank">Learn more</a>
  ```
  The `target="_blank"` attribute will force the user to open the linked page in a new window or tab without closing the current window.
  Finally, add `.bg-danger` to `.card-footer` of all 3 cards to change the background color to fit with the button inside.
  

