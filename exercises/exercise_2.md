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

## Milestone 3: Navbar - Responsive logo on left
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
  Save and reload your browser. Try resizing your page horizontally and see the logo changes when the *viewport* is smaller or larger.
  
## Milestone 4: Navbar - Responsive links on right
  We got the left of the navbar, the only thing left is the navigation links on the right.
  Even though the CoderSchool logo is responsive, the navbar itself is not responsive yet. To make it responsive, add the following class to the `<nav>` element: `.navbar-expand-lg`. 
  Then, add `.navbar-light` to the `<nav>` to make the color easy to see.
  Finally, add the following code inside the `<nav>` and below the hyperlink logo:
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
  In the code about, there are two things: a `button` and a `div`. When the screen is `lg` (min-width: 992px), then the `div` is displayed with a list of horizontal hyperlinks. When the screen is smaller than 992px, then a hamburger `button` is shown instead. Clicking on the button will display the list of hyperlinks vertically.