# Week 4 Lab: Set up website with WordPress software

## Overview:
This is your final lab, and you will be learning all the *nuts and bolts* of a running website application in the internet. We will use WordPress software as the platform and the engine for our website. We will also register a free domain name and a free hosting server for your website. Besides HTML, CSS, and JavaScript on the client side, WordPress works with PHP and MySQL on the server side. We will also get to understand a bit of these technology terms. 

A domain name is an easy-to-spell, easy-to-remember name for your website (eg. WordPress.org). Without a domain name, your website online address will just be an IP address (eg. 151.101.129.121), which is hard to remember. A webhost server is a machine that hosts your websites. It is where your websites live. When a person wants to visit a website from a browser, the browser (Safari, Chrome, Firefox, etc.) makes GET requests to the webhost server to retrieve the website information. A domain name and a webhost server works together i.e. they have to point to each other. 

PHP is the language that is used to send data back and forth between the browser (client) and the web-host (server). PHP interacts with both front-end and back-end. MySQL is a back-end language that talks to the database and manage all the data of a website. 

A webhost server nowsadays always comes with the AMP (Apache, MySQL, PHP) stack which is a solution stack for running a website. WordPress needs to have the AMP stack to be able to start.

In today lab, we will get to learn these technology stacks in details. You will be pair programming with a person sitting next to you. The goal of today lab is {INSERT HERE}

## Milestone 1: Install and run WordPress locally
The WordPress.org website has [detailed instructions](https://codex.wordpress.org/Installing_WordPress) on how to install WordPress and run it locally. However, the guide is too long and has information that you do really need to know. 

I will provide a quick and easy way to get WordPress running locally in your computer. Below are the steps:
1. Install WordPress
2. Install MAMP
3. Set up WordPress in local server (MAMP)

### Milestone 1.1: Install WordPress
1. Head over to https://wordpress.org/download/ and dowload the lastest stable version of WordPress (v 4.9.5)
2. Unzip the WordPress package in a desire position. The directory contains the unzip file is a WordPress software for your website. Your WordPress directory should have the following files:
<img src="https://i.imgur.com/Ke3Kcbnl.png" alt="WP files">
Each website requires a seperate WordPress software i.e. if you want to make 3 different websites then you will have to install 3 seperate WordPress software locally. 

### Milestone 1.2: Install MAMP 
Now, you will need a local server (environment) for the WordPress to run on. WordPress.org has a [list of recommended servers](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/). I will use MAMP since it's easy and will help you understand the science "behind the scence". 
There is a new tool called [Flywheel](https://local.getflywheel.com/) that's gaining a lot of traction lately. I actually like this tool more than MAMP because of its intuitive UI and user-friendly. However, I'll recommend you to use one other tool first before getting started on Flywheel.

3. Go to https://www.mamp.info/en/ and download the MAMP free version. MAMP comes with PHP, Apache server, and MySQL server.
4. Open MAMP and click on 'Start Server'
5. When the Apache server and MySQL server are all set up (green light), click on 'Open WebStart page' to start the local server. It will open a new tab on your web browser. The url is either `http://localhost:8888/MAMP/?language=English` (on Mac) or `http://localhost/MAMP/?language=English` (on Windows)
<img src="https://i.imgur.com/9pnBnX0.png" alt="MAMP">

6. This is a **Start** page, where you intereact with your local server. Click on **phpInfo** to be taken to the information page of PHP and Apache. Click on **Tools > phpMyAdmin** to be takend to the MySQL databases that contain all data of your websites.
7. We will need a database for your new website (if there are 3 websites, there will be 3 different databases).
Go to phpMyAdmin and click on `New` in the left panel. On the right panel, type "my-first-wp-site" in the database name. *Collation* is a set of rules that determine how data is sorted and compared. Pick "utf8_general_ci" as it is the most common collation. Then click `Create`.
You will be taken to the Structure tab of your database. The database is empty because there is no table. 
<img src="https://i.imgur.com/iANKTtK.png" alt="phpMyAdmin">
When WordPress is set up with this database, there will be additional 12 tables added by WordPress.
You can also create an additonal custom table for your custom plugins but we won't go into that now. 

### Milestone 1.3: Set up WordPress in MAMP
8. Remember the unzip `wordpress` package that we did in step 2? Change the folder name from `wordpress` to `my-first-wp-site` (same name as database name).
9. Manually move (copy-paste or drag-drop) the `my-first-wp-site` folder to inside the /MAMP/htdocs folder. `htdocs` folder is where all your wordpresses (websites) live.
<img src="https://i.imgur.com/vWCyeQV.png" alt="htdocs">
10. Now, go back to your MAMP `Start` page by click on the "Open WebStart page" on MAMP. Then, click on the `My Website` tab. You will be taken to `http://localhost:8888/` or `http://localhost/` depends on your Operation System
11. You should see something like this:

# Index of /
* [my-first-wp-site](#)/

Click on the `my-first-wp-site` hyperlink to start the WordPress set up.

12. Going through the instructions and click on `Let's go!` button to be taken to the **database connection details** page.
13. Make changes to your database connection details so it looks like below:
* Database Name:      my-first-wp-site
* Username:           root
* Password:           root
* Database Host:      localhost:8888 (or localhost for Windows)
* Table Prefix:       wp_

Click 'Submit'
14. Awesome! WordPress is all set up for the local server. Now, we can start the installation on the server. Click on `Run the installation` to be taken to the installation page.
15. Fill the information as below (use your email address):
<img src="https://i.imgur.com/gzMIRKZ.png" alt="WP installation details">
We use `root` for default username and password. You can change it later when you are more familar with WordPress.
Click on `Install WordPress` when you are done.

16. Success! WordPress has been installed. Now you can log in to your local WordPress Dashboard using the default username and password.
<img src="https://i.imgur.com/tFUL9fW.png" alt="WP Dashboard">


## Milestone 2: Personalize your local WordPress
Go to `../my-first-wp-site/wp-admin/`. This is a dashboard for you (the administrator) to manage your WordPress website.
Now we will add some content to your site.

### Milestone 2.1: Publish 2 Posts
* One post with an image, a youtube video, and some ipsum text (categorize and tag your post)
* One post with a *featured image* and some ipsum text (categorize and tag your post)
You can also just grab some random posts from the internet for your content (try this http://catsinternational.org/articles/).
Right now, we only focus on the engineering side of WordPress.

### Milestone 2.2: Publish 2 Pages
* *About Me* page: content about yourself
* *Contact* page: how online people can reach you
(CoderSchool contact example:
Address: 12 Tôn Đản, Bến Nghé, Quận 4, Hồ Chí Minh 700000
Phone: 0122 474 2431)

### Milestone 2.3: Create a Main Menu
1. Go to Appearance and give the Menu Name `Main Menu`.
2. Add Contact, About Me, and Sample Page inside the Menu Structure. The Sample Page is a sub item of the About Me.
3. Tick 'Top Menu' in the *Display location* and then click `Save Menu`.

Your WordPress Home page now should look similar to this:
<img src="https://i.imgur.com/6tywpju.png" alt="WP Homepage">

### Milestone 2.4: Manage your database
All the content that you have created so far (pages and posts) are stored in the backend MySQL database. Now, let us take a look at these data
1. Open the MAMP WebStart page again and go to **phpMyAdmin**
2. Click on the `my-first-wp-site` database on the left panel. Notice that WordPress has created 12 tables with prefix "wp_" after the WordPress installation in `Milestone 1.3`
3. Locate the `wp_posts` table and click on `Browses`. Now, you can see all your posts' and pages' content are in the `post_content` column
<img src="https://i.imgur.com/tMk9eKD.png" alt="wp_posts">
Equivalently, you can also just run this sql script in the `SQL` tab to get the same result:
```sql
SELECT * FROM `wp_posts`
```
4. Now, let's do a bit of SQL while we are here. Sometimes, you need to check some data in the database to troubleshoot issues.
The list that we saw above contains all the Posts and Pages in your website. However, you only want to view *only* the Pages. To do that, run this SQL script:
```sql
SELECT * FROM `wp_posts` WHERE `post_type` = "page"
```
Bam! You have written your first SQL script, and the results return only the Pages. 
If you want the results to return onlt Posts, change the `post_type` to "post".

### Milestone 2.5: Manually install a new theme
1. Go to https://colorlib.com/wp/themes/ for free themes.
2. Pick [activello](https://colorlib.com/wp/themes/activello/) and download the zip file (you can pick a different one later).
You can upload the Theme by going to `Dashboard > Apperance > Themes > Add New > Upload Theme` and just upload the theme zip file there. However, I want to add the theme manually.
3. Unzip the zip file into a folder. The folder should be named `activello`.
4. Drop the folder into `../MAMP/htdocs/my-first-wp-site/wp-content/themes/`.
There are already 3 other theme folders inside the `themes` folder: **twentyfifteen**, **twentyseventeen**, and **twentysixteen**. Your default theme is **twentyseventeen**.
5. Go back to your admin Dashboard and you should see the new **Activello** theme appears in the `Themes` page. Activate the theme to use it.

### Milestone 2.6: Manually install a new plugin
This is similar to how you installed a theme in `milestone 2.5`. You just need to download the zip file, unzip it and drop the plugin folder into `../MAMP/htdocs/my-first-wp-site/wp-content/plugins/` folder. Then, activate the plugin in the `Plugin` page. 
See how every post has a comment section that anyone can just make a comment on. Now, let's disable all the comments by using a plugin. 
*Task:* Download `Disable Comments` plugin: https://wordpress.org/plugins/disable-comments/ to disable comments on all Posts

### Milestone 3: Register a free domain
There are many websites that give out free domains. In this exercise, we will use **freenom**.
1. Go to http://www.freenom.com/ and type in your desired domain name in the Check Availability box. I use `my-diy-wordpress-site` and you should pick a different name (the same name is probably already taken by me).
<img src="https://i.imgur.com/RuwGXkH.png" alt="freenom">
2. 


### Milestone 4: Register a free host


### Milestone 2.1: Upload a WordPress theme
    
1. Create 3 Posts: 1 post with a featured image and ipsum text, 1 post with 


