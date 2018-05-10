# Week 4 Lab: Build a custom WordPress theme

## Overview:
Today lab is your final exercise of our Web Design Bootcamp class. We will be building a basic custom WordPress theme using HTML, CSS, and a bit of PHP. The goal of the lab is to get you understand how templates in WordPress work, and how you can make your own templates.

We will develop our custom WordPress theme in local environment (with MAMP). When we are happy with our theme, we can deploy it to the remote server using FileZilla.

First, we will create the main stylesheet `style.css` with theme information, and our core template files such as `header.php`, `footer.php`, `sidebar.php`. Then we will create the `index.php` to load all the html elements from other files.

Below is a result of your custom theme (Blog page) with just dynamic HTML content:

<img src="https://i.imgur.com/AYH0Ok8.png" alt="mocha1">

Next, we will start styling our websites with the `style.css`, and we will add a few more template files such as `functions.php`, `page.php`, and `single.php` for further customization.

Here is a final result of your custom theme (Blog page) with dynamic HTML content and CSS styling:

<img src="https://i.imgur.com/NWsmtFI.png" alt="mocha2">

## Milestone 1: Update Homepage and Main Menu
Currently your homepage is showing all your *Posts* in reverse chronological order. We want to just show a static page. Let's fix that.
1. Create a `Home` page, and a few more pages such as `Services`, `Portfolio`, and `Blog`. The `Blog` page will be the place showing all the latest *Posts*.
2. Add some content to your `Home` page since it will be your landing page.
3. Access your **Main Menu** from `Appearance > Menus`
4. Remove the `Sample Page` from the Menu Structure, and add `Home`, `Services`, `Portfolio`, and `Blog` pages to the Menu. It should be in this order: Home, About Me, Services, Portfolio, Contact,Blog. Save your Menu.
5. Go to `Settings > Readiurg`, choose `Your homepage displays: A static page` with `Homepage: Home` and `Posts page: Blog` then click Save Changes.
6. Now, go back to your site and reload the browser, it should show your `Home` page as the landing page for your website:

    <img src="https://i.imgur.com/cm08NY7.png" alt="homepage">

## Milestone 2: Create the core template files
1. Go to `/MAMP/htdocs/` and open the `my-first-wp-site` directory in your favorite text editor
2. Go to `/wp-content/themes` and create a folder name `mocha`. We will build our custome theme inside this folder (all the files created will be in here):

    <img src="https://i.imgur.com/qS1UyMz.png" alt="my-first-wp-site">

    Now, let's create the core template files. Beside one stylesheet, you will be making some PHP files. Don't worry if you don't know anything about PHP. You will still be able to create a custom theme in this lab.

    PHP files can read both HTML and PHP code. HTML code starts with HTML opening tag, content, then HTML closing tag e.g. `<h1>Heading</h1>`. PHP code starts with PHP opening tag `<?php`, PHP content, then PHP closing tag `?>` e.g. `<?php bloginfo('title'); ?>`
    ```php
    <h1><?php bloginfo('name'); ?></h1>
    ```
    The above code is very common in a PHP file where the blog (post) name is dynamic and is styled by the HTML `<h1>` wrapper.

### Create style.css
3. Create a `style.css` file. This is your main stylesheet and you will be using only this stylesheet for all the styling in this exercise.
4. Now, to follow WordPress standards for themes, we need to add a block of CSS comment to the top of `style.css` to define the theme: 
    ```css
    /*
    Theme Name: Mocha
    Theme URI: http://www.coderschool.vn/
    Author: [Your Name]
    Description: This is a custom theme made in CoderSchool Web Design Bootcamp
    Version: 1.0
    License: GNU General Public License v2 or later
    License URI: http://www.gnu.org/licenses/gpl-2.0.html
    */
    ```
    The minimum you need to have in the comment block is the `Theme Name`. Save the stylesheet after adding the comment block. We aren't doing any styling yet. We will do it after we have all the HTML content loaded properly in our new custom theme.

### Create header.php
5. Create a `header.php` file. The `header.php` file contains the top part of `index.html` file that you normally know. It has the open `<html>` tag, the `<head>` content, and the top part of `<body>`.
6. First, add the `<head>` content to the `header.php`
    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <link rel="stylesheet" href="style.css">
        <title></title>
    </head>
    ```
7. Now, input the dynamic content into your `header.php` file. Insert the php code 
`<?php bloginfo('title'); ?>` in your `title` tag. We don't want to give the `title` a static name. If we just input something like `My Blog` for title, every single page of our WordPress site will have the title `My Blog` and we don't want that.
8. Another thing that we need to change is to make the css path `href` dynamic. Let's add another another PHP `bloginfo` function but this time we're passing in the parameter `stylesheet_url`.
This should be your result:
    ```php
    <link rel="stylesheet" href="<?php bloginfo('stylesheet_url'); ?>">
    <title><?php bloginfo('title'); ?></title>
    ```    
9. Next, add the first part of `<body>` content to the `header.php`
    ```html
    <body>
        <div id="container">
            <header>
                <h1></h1>
                <div id="search"></div>
            </header>
            <div style="clear:both;"></div>
            <nav class="main"></nav>
    ```
    In here, we added a container, a header, a search box, and a navbar. Because the search box is floated. I need to clear the float by adding `<div style="clear:both;"></div>` right below the search box.
10. Again, let's make the content in the `<body>` dynamic:
* Add `<?php bloginfo('name'); ?>` inside the `<h1>` tag. 
* We are not doing anything for the search box yet. 
* For the navbar menu, add `<?php wp_nav_menu(); ?>` inside the `<nav>` tag.
    This should be your result:
    ```php
    <header>
        <h1><?php bloginfo('name'); ?></h1>
        <div id="search"></div>
    </header>
    <div style="clear:both;"></div>
    <nav class="main"><?php wp_nav_menu(); ?></nav >
    ```
    We won't be adding any logo for now, we will just be using the site title as the logo wrapped in `h1` tag, the biggest heading available in HTML.
11. Save the `header.php` file.

### Create footer.php
12. Create a `footer.php` file. This file contains the bottom part of the `index.html` file that you normally know: the <footer> content, the bottom part of `<body>`, and the closing `</html>` tag.
13. Add a footer with a simple `Copyright` text, the &copy; for the logo, `2018`, and some closing tags:
    ```html
            <footer>Copyright &copy; 2018</footer>
        </div>
    </body>
    </html>
    ```
    The closing `</div>` is for the `container` div (declared in header.php file). All content should be in the `id = "container"` div. That's all we need for the `footer.php`. Save it.

### Create sidebar.php
14. Create a `sidebar.php` file. 
15. Add in the following html code:
    ```html
    <div id="sidebar">

    </div>
    <div style="clear:both;"></div>
    ```
    Since the sidebar is pretty much likely will float on the right side, We added a div with style `clear:both` at the bottom.

    This one line *clear* div code doesn't do any harm, What it does is that if things are float above, they will stop floating at this div and below.
16. Save the file.

### Create index.php
17. Now, let's create an `index.php` file which will link all the above PHP files together (this file is like the `index.html` file)
18. First, we grab the `header.php` first. We can do that with the PHP function `get_header()`. The function doesn't take any parameters inside the parentheses. All functions need to have parentheses regardless of if they need parameters or not.
    ```php
    <?php get_header(); ?>.
    ```
19. At the bottom we want to bring in the sidebar, so we can do that with the `get_sidebar()` function.
20. The last thing you want to include is the footer so let's add it in with the `get_footer()` function.
21. This should be your result in `index.php` up to this point
    ```php
    <?php get_header(); ?>.


    <?php get_sidebar(); ?>
    <?php get_footer(); ?>
    ```
    With these functions, what it means is that we include header, sidebar, and footer pretty much every page.

### Loop of Posts inside index.php
22. We got the header, the sidebar, and the footer. Now, we need the area of posts in the middle, and this area is a **loop of posts**. The way that PHP is able to do this is through a loop. There are a few different kind of loops (for loop, while loop, etc). In this exercise, we will use the **while loop**. What we'll try to do is to make a loop that says: "If there are posts, then show the next post." All up until there's no post in which the loop will end.
23. Let's do this. We want all the posts wrapped in a `main` div. Add this HTML code between the `get_header()` and `get sidebar()` functions:
    ```html
    <div id="main">

    </div>
    ```
24. Now, inside this `main` div, include the while loop:
    ```php
    <?php while(have_posts()) : the_post(); ?>
        <div class="post">
            <h2><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
            <?php the_content(__('Continue Reading')); ?>
        </div>
    <?php endwhile; ?>
    ```
    What it means here is that while there are posts, output all the posts. 
    
    If you look at the WordPress site, a Post has a title and a body content: 
    
    The `<h2>` tag is the title of the post. You can also use `h3` or `h4` for the post title. Then, we need to dynamically print out the post title between the `h2` tag. To do that, we insert `the_title()` func inside the `h2` tag.

    Then, we need to make the title as a **hyperlink**. To do that, we add an anchor tag and wrap around the title. We use a PHP function `the_permanlink()` to specify where the link goes to. That's the function when user click on the link title, they are taken to the page or to the single post.

    Next, we add the body content with the `the_content()` code. We don't want the content to be too long for a single post in a loop of posts. We add a paramenter `__('Continue Reading')` for the function to call. `the_content()` func will output the content (main body) of the post, and the 'Continue Reading' link is where we want it to be cut off.

    We are not putting the date and name of the author yet, we'll do that later.

    The while loop is closed with the `<?php endwhile; ?>`. This will give us the loop of posts.
25. What happens if there is no posts? We also need to cover this condition as well. I'll use an **if-else statement** for this. 
    **If** there are posts, we want to start the **while loop**. **Else**, if there is no post, we want to display a text 'Sorry, no posts were found'. Add this **if-else statement** code inside the `main` div:
    ```php
    <?php if(have_posts()) : ?>

    <?php else : ?>

    <?php endif; ?>
    ```
* The *while loop* should be nested inside the `if(have_posts()) :`.
* Inside the `else :`, insert this code:
    ```php
    <?php echo wpautop('Sorry, no posts were found'); ?>
    ```
26. This should be the result of your **if-else statement** inside the `main` div:
    ```php
    <div id="main">
        <?php if(have_posts()) : ?>
            <?php while(have_posts()) : the_post(); ?>
                <div class="post">
                    <h2><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></h2>
                    <?php the_content(__('Continue Reading')); ?>
                </div>
            <?php endwhile; ?>
        <?php else : ?>
            <?php echo wpautop('Sorry, no posts were found'); ?>
        <?php endif; ?>
    </div>
    ```
27. Save the `index.php` file. 

Good job! We have completed the first part of our theme.

## Milestone 3: Load your custom theme with dynamic HTML content
1. Go to your wp-admin `Dashboard`
2. Go to `Apperance > Themes`
3. See now that I got my custom theme "Mocha" showing up here
    <img src="https://i.imgur.com/LQME2Bg.png" alt="custom-theme">
    This is the template that we have made and is now available for us to use.
4. Click on the theme to see the theme details. You can also try a `Live Preview` of it.
5. Now, click on `Activate`
6. This is what I have now for my 'Blog' Page

    <img src="https://i.imgur.com/AYH0Ok8.png" alt="mocha1">

    The PHP code reads the dynamic HTML content correctly, It reads the `Title`, the `Main Menu`, the *loop of posts*, the `Post Title`, the `Post Content`. It has the **Continue Reading** link. Click on the Post Title will take me to that single post.

    It's all working, we just need to add some styling to the side, which we'll do in the next milestone.

## Milestone 4: Style your theme with style.css
We now have a beautiful theme (just kidding it looks pretty bad). Let's go back to the `style.css` file and start to add some styling, we also need to add a few more PHP template files as well.

### CSS Reset
One good practice for website styling is to always include a **reset stylesheet**, and what it does is to zero out the `paddings` and the `margins` because different browsers have different paddings and margins to certain elements. For example, **Internet Explorer** might add `10px` to an HTML element and **Firefox** might not. If we don't reset everything at first and just keep the defaults it's going to affect the way it looks in each browser so let's include a reset file from now on.

The one I usually use is the eric myer's css reset file: https://meyerweb.com/eric/tools/css/reset/. I'm not gonna add a new css file but will include the css reset code at the beginning of our main stylesheet `style.css`. 
1. Copy the css code from eric myer's css reset file
2. Go to the `style.css` and paste the css code at the top (below the comment block)

3. Save it.
4. Reload now and see that styling for your website has been reset (I will just use the Blog page for all captured screens since it has the most content): 
    
    <img src="https://i.imgur.com/VWy8WtG.png" alt="css-reset">
    
    Now, we have a clean slate since this is identical for **all browsers**.

### Style body
5. Now, let's first start styling your `<body>`. Add this below the CSS Reset code:
    ```css
    body {
        background: silver;
        font-size: 14px;
        font-family: arial;
        line-height: 1.6em;
        color: #666;
    }
    ```
6. Then, we style the core HTML elements: p, a, ul, ol, li, h1, h2, h3, and img. Add this below the body selector:
    ```css
    p { margin: 10px 0; }
    a { color: #666; text-decoration: none; }
    ul, ol { padding: 10px 0 10px 10px; list-style: square; }
    ul li, ol li{ line-height: 1.8em; color: #000; }
    h1 { font-size: 26px; padding-bottom: 8px;}
    h2 { font-size: 22px; color: #666; padding: 8px 0;}
    h3 { font-size: 18px; color: #666; padding: 8px 0;}
    img { margin: 15px; }
    ```
7. Save and reload the page, see some styles have been added

    <img src="https://i.imgur.com/D65f9aF.png" alt="styling-1">

### Style other HTML components
8. Now ,let's style your `container`:
    ```css
    #container {
        width: 960px;
        margin: 0 auto;
        border: #ccc solid 1px;
        overflow: auto;
        background: #fff;
        padding: 20px 15px;
    }
    ```
9. Save the `style.css` and reload the WordPress site to see changes.
10. Add some header styling:
    ```css
    header { height: 70px; }
    header h1 { padding: 15px 10px; float: left; width: 400px; }
    ```
11. Then, some navigation styling:
    ```css
    nav.main { height: 35px; padding-top: 10px; background: #333; overflow: auto; margin-bottom: 10px; }
    nav.main ul { padding: 0; }
    nav.main ul li { float: left; padding:0 10px; list-style: none; font-size:15px; }
    nav.main a { color: #fff; }
    ```
12. Save the `style.css` and reload the WordPress site to see changes.

    <img src="https://i.imgur.com/Fz6r3ef.png" alt="styling-2">

    We floated the list items of the nav to the left, and make them inline, gave some styling to it.

### Style posts
13. Next thing we want to do is to style our posts. Add the following:
    ```css
    #main{ float: left; width: 60%; overflow: auto; }
    #main .post{ padding: 20px 0; border-bottom: 1px #ccc dashed; overflow: auto; }
    #main .post a.more-link{ color: #074b77; display: block; margin-top: 5px; }
    ```
    Here, the **main** area of posts is only **60% in width** because remember we want to have a sidebar, and we want to it to float on the right side. We added a dashed bottom border for each post to sepearate them out. The 'Continue Reading' is now a block element rather than an inline element with a bottom padding to make it more stand out.
14. Save the `style.css` and reload the WordPress site to see changes.

    <img src="https://i.imgur.com/iuI6vKI.png" alt="styling-3">

## Milestone 5: Add Sidebar to your site
Now is a good time to add your sidebar to the right of your page.
1. Go to your `Dashboard > Appearance`. Remember that usually in `Appearance`, we should have the following:
* Themes
* Customize
* Widgets
* Menus
* Background
    Now, the `Widgets` and `Menus` links are no longer there because the current theme doesn't support these features. In other to bring back these features, we need to add the **dynamic sidebar functions**,, so let's create it. 

### Create functions.php
2. Go to our theme folder `/wp-content/themes/mocha` and create a new file called `functions.php`.
3. What we need to do is to register our positions for the widgets (or sidebars), and to do that we start with `register_sidebar()`. Add this in your `functions.php` file:
    ```php
    <?php

    register_sidebar()

    ?>
    ```
4. Now in the `register_sidebar()` func, we need to add an array as a parameter. `name` and `id` are the mandatory elements of the array. There are other elements of the array such as `description` of the sidebar, `before_title` and `after_title` to wrap around the title of the sidebar and gives it some styling.
    This is your top right sidebar:
    ```php
    register_sidebar(array(
		'name' => __('First Right Sidebar'),
		'id'   => 'first-right-sidebar',
		'description' => 'The widget position in the top right sidebar',
		'before_title' => '<h2>',
		'after_title'  => '</h2>'
	));
    ```
5. Copy the whole `register_sidebar()` code and paste below the first sidebar to register the position for the second right sidebar. Change the `name`, `id`, and `description`
    ```php
    register_sidebar(array(
		'name' => __('Second Right Sidebar'),
		'id'   => 'second-right-sidebar',
		'description' => 'The widget position in the bottom right sidebar',
		'before_title' => '<h2>',
		'after_title'  => '</h2>'
	));
    ```
6. Save the `functions.php` file.

### Update sidebar.php
7. Now, that alone doesn't give us the positions for our sidebars. We need to go to the `sidebar.php` and add the 2 registered dynamic sidebars in here.
8. Add this code inside the `#siderbar` div:
    ```php
    <?php dynamic_sidebar()?>
    <?php dynamic_sidebar()?>
    ```
9. Next, the parameters for these sidebars gonna be the `id`s that we specified in `functions.php` file. Add the ids in:
    ```php
    <?php dynamic_sidebar('first-right-sidebar')?>
    <?php dynamic_sidebar('second-right-sidebar')?>
    ```
10. Save the `sidebar.php` file and reload.

### Add dynamic sidebars to site
11. Go back to your admin portal
12. Click on `Appearance` on the left panel. We now got `Menus` and `Widgets` again.
13. Go to Widgets, and you see the 2 sidebars that we added in `functions.php` and `sidebar.php` are now on the top right corner.
14.  Add `Categories` and `Recent Posts` (change to 3 recent posts) to the `first right sidebar` and gives each of them a title. Then, add Recent Comments to the `second right sidebar` and also give it a title. 

    <img src="https://i.imgur.com/ebZaxOT.png" alt="widgets">

15. Save the Widgets and go back to your site.
16. We can see now that the sidebars are on the right side but they are overlapping with each other. We need to give the sidebars some styling.

### Style the sidebars
17. Open your `style.css` file
18. Add some styling to your sidebar:
    ```css
    #sidebar { float: right; width: 25%; overflow: auto; background: #f4f4f4; padding: 10px 15px; }
    #sidebar { list-style: none !important; }
    #sidebar ul { padding-left:10px; }
    ```
    Make the width 25% and float to right, and give it some paddings.
19. Save the `style.css` and reload the WordPress site to see changes.

    <img src="https://i.imgur.com/8F2lm2b.png" alt="styling-4">


## Milestone 6: Add Search box widget on top right corner
1. Remember the `search` div that we defined in `header.php` but we haven't touched it at all? Now, we will add the Search box to the site.

### Update functions.php
2. Go back to the `functions.php` and make another copy of a whole `register_sidebar()` code and paste below the second sidebar to get the 3rd widget position. Even though the function name is `register_sidebar()` but what it really means is to register a widget position. Hence, we don't have to name our third one `sidebar`, let's name it *Header Right*. Change the `name`, `id`, and `description` of this third widget:
    ```php
    register_sidebar(array(
		'name' => __('Header Right'),
		'id'   => 'header-right',
		'description' => 'The widget position in the header right',
		'before_title' => '<h2>',
		'after_title'  => '</h2>'
	));
    ```
3. Save the `functions.php` file
### Update header.php
4. Go to your `header.php` file and insert this code inside the `search` div to call the 3rd widget we have just registered in the `functions.php` file:
    ```php
    <div id="search">
        <?php dynamic_sidebar('header-right'); ?>
    </div>
    ```
5. Save the `header.php` file, and reload your wp-admin portal. You should see a new widget position called **Header Right** in the Widgets panel.
6. Drag and drop the Search widget inside the Header Right widget position.
7. Save and reload the WordPress site to see our Search box in the `header`.

### Update style.css
8. Now, let's add some styling to our Search box. Go to `style.css` file
9. Add this css code for your Search box:
    ```css
    header #search { float: right; width: 310px; padding-top: 14px; list-style: none !important; }
    ```
    Save and reload page. Now, you have a Search widget.

## (OPTIONAL) Milestone 7: Change Post Page's Template
We have a few more things to do. If you click on a Post link to open a Post right now, this Post still uses the `index.php` template. We want the Post to have its own template by using the `single.php` template to include Comment area and functionality. Currently, there is no Comment area in the current Post.

### Create single.php
1. Go to our theme folder `/wp-content/themes/mocha` and create a new file called `single.php`.
2. Copy all the code of `index.php` and paste them in `single.php`.
3. Add this code inside the if statement, below the `endwhile` line:
    ```php
    <?php comments_template(); ?>
    ```
    And what it does is giving us all the Comment functionality
4. We also want to add `author` and `date` for each Post, so let's do that. Add this line of code below the `h2` title and above the `the_content()` func:
    ```php
    <div class="meta">Written by: <?php the_author(); ?> on <?php the_date('F j, Y'); ?></div>
    ```

### Update style.css    
5. Add some styling for the `meta` div in `style.css`: 
    ```css
    .meta { padding: 3px 5px; background: #f4f4f4; width: 95%; }
    ```
    Now, we have a little styling to that `meta` line on website.
6. Save and reload. (If you still have the Disable Comments plugin active, makes sure to deactivate it.)
7. Then open a Post page. You can see now that you have the meta line on top and a comment area at the bottom of each Post:

    <img src="https://i.imgur.com/ce1ZdWu.png" alt="styling-5">

    <img src="https://i.imgur.com/pkVqu3y.png" alt="styling-6">

8. Congrats! You have made your first custom theme!

## (OPTIONAL) Milestone 8: Push the Custom Ttheme to Remote Server
You should know how to do this by now. Just copy the `mocha` folder from your local `/wp-content/themes/` to your remote `/wp-content/themes/`

