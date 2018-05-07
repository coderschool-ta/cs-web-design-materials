# Week 4 Lab: Set up website with WordPress software

## Overview:
This is your final lab, and you will be learning all the *nuts and bolts* of a running website application in the internet. We will use WordPress software as the platform and the engine for our website. We will also register a free domain name and a free hosting server for your website. Besides HTML, CSS, and JavaScript on the client side, WordPress works with PHP and MySQL on the server side. We will also get to understand a bit of these technology terms. 

A domain name is an easy-to-spell, easy-to-remember name for your website (eg. WordPress.org). Without a domain name, your website online address will just be an IP address (eg. 151.101.129.121), which is hard to remember. A webhost server is a machine that hosts your websites. It is where your websites live. When a person wants to visit a website from a browser, the browser (Safari, Chrome, Firefox, etc.) makes GET requests to the webhost server to retrieve the website information. A domain name and a webhost server works together i.e. they have to point to each other. 

PHP is the language that is used to send data back and forth between the browser (client) and the web-host (server). PHP interacts with both front-end and back-end. MySQL is a back-end language that talks to the database and manage all the data of a website. 

A webhost server nowsadays always comes with the AMP (Apache, MySQL, PHP) stack which is a solution stack for running a website. WordPress needs to have the AMP stack to be able to start.

In today lab, we will get to learn these technology stacks in details. You will be pair programming with a person sitting next to you. The goal of today lab is {INSERT HERE}

## Milestone 1: Install and run WordPress locally
The WordPress.org website has [detailed instructions](https://codex.wordpress.org/Installing_WordPress) on how to install WordPress and run it locally. However, the guide is too long and has too much information which you do not need to know all. I will provide a quick and easy way to get it running locally in your computer.

### Install WordPress
1. Head over to https://wordpress.org/download/ and dowload the lastest stable version of WordPress (v 4.9.5)
2. Unzip the WordPress package in a desire position. The directory contains the unzip file is a WordPress software for your website. Your WordPress directory should have the following files:
<img src="https://i.imgur.com/Ke3Kcbn.png" alt="WP files">
Each website requires a seperate WordPress software i.e. if you want to make 3 different websites then you will have to install 3 seperate WordPress software locally. 

### Install MAMP 
Now, you will need a local server (environment) for the WordPress to run on. WordPress.org has a [list of recommended servers](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/). I will use MAMP since it's easy and will help you understand the science "behind the scence". 
There is a new tool called [Flywheel](https://local.getflywheel.com/) that's gaining a lot of traction lately. I actually like this tool more than MAMP because of its intuitive UI and user-friendly. However, I'll recommend you to use one other tool first before getting started on Flywheel.

3. Go to https://www.mamp.info/en/ and download the MAMP free version. MAMP comes with PHP, Apache server, and MySQL server.
4. Open MAMP and click on 'Start Server'
5. When the Apache server and MySQL server are all set up (green light), click on 'Open WebStart page' to start the local server
<img src="https://i.imgur.com/9pnBnX0.png" alt="MAMP">
    It will open a new tab on your web browser. The url is either http://localhost:8888/MAMP/?language=English (on Mac) or http://localhost/MAMP/?language=English (on Windows)

6. This is a **Start** page, where you intereact with your local server. Click on **phpInfo** to be taken to the information page of PHP and Apache. Click on **Tools > phpMyAdmin** to be takend to the MySQL databases that contain all data of your websites.
7. We will need a database for your new website (if there are 3 websites, there will be 3 different databases).
Go to phpMyAdmin and click on `New` in the left panel. On the right panel, type "my-first-wp-site" in the database name. *Collation* is a set of rules that determine how data is sorted and compared. Pick "utf8_general_ci" as it is the most common collation. Then click `Create`.
You will be taken to the Structure tab of your database. The database is empty because there is no table. 
<img src="https://i.imgur.com/iANKTtK.png" alt="phpMyAdmin">
When WordPress is set up with this database, there will be additional 12 tables added by WordPress.
You can also create an additonal custom table for your custom plugins but we won't go into that now. 

### Set up WordPress in MAMP 
8. Remember the unzip *wordpress* package that we did in step 2? Change the folder name from *wordpress* to *my-first-wp-site* (same name as database name).
9. Manually move (copy-paste or drag-drop) the *my-first-wp-site* folder to inside the /MAMP/htdocs folder. `htdocs` folder is where all your wordpresses (websites) live.
<img src="https://i.imgur.com/vWCyeQV.png" alt="htdocs">
10. Now, go back to your MAMP `Start` page by click on the "Open WebStart page" on MAMP. Then, click on the `My Website` tab. You will be taken to http://localhost:8888/ or http://localhost/ depends on your Operation System
11. You should see something like this:

# Index of /
* [my-first-wp-site](#)/
Click on the `my-first-wp-site` hyperlink to start the WordPress set up.
12. Going through the instructions and click on `Let's go!` button to be taken to the **database connection details** page.
13. Make changes to your database connection details so it looks like below:
    Database Name:      my-first-wp-site
    Username:           root
    Password:           root
    Database Host:      localhost:8888 (or localhost for Windows)
    Table Prefix:       wp_
Click 'Submit'
14. Awesome! WordPress is all set up for the local server. Now, we can start the installation on the server. Click on `Run the installation` to be taken to the installation page.
15. Fill the information as below (use your email address):
<img src="https://i.imgur.com/gzMIRKZ.png" alt="WP installation details">
We use `root` for default username and password. You can change it later when you are more familar with WordPress.
Click on `Install WordPress`.
Success! WordPress has been installed.
16. Now you can log in the newly set up WordPress website (locally) using the default username and password.
<img src="https://i.imgur.com/tFUL9fW.png" alt="WP Dashboard">





## (BONUS) Milestone 4: PICTURE
* You can edit your products’ picture using this: https://www.picmonkey.com/photo-editor/photo-filters 
* Need some quality pictures related to the theme of your landing page? Go here: https://unsplash.com
