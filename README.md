# WordPress Ninja Turtles Practice

## Installation Instructions For Local Development with WordPress

### 1. Clone Repo 

```
$ git clone https://github.com/kingluddite/tmnt-wp-bs-theme.git wp-ninja-turtles
```

### 2. Install WP-CLI

Install WP-CLI so you can install WordPress from the Terminal. You should have this installed. If not, read the [wp-cli.md](https://github.com/kingluddite/web-dev-notes/blob/master/wordpress/wp-cli.md)

### 3. Install WordPress Core

```
$ wp core download
```

That will install WordPress core but you will still have your wp-content folder with your themes folder nested inside and with your custom theme nested inside the themes folder.

### 4. Start MAMP

Make sure your local server and mysql are running. For this example I'll assume you are using MAMP. Make sure Apache and MySQL are running.

* I like to change my DocumentRoot to `~/Sites`
* I like to remove port `8888` and use default http port so I only have to use `localhost` instead of ``localhost:8888``

### 5. Create Empty Database

Use MAMP's phpMyAdmin to create an empty database.

* please use underscores and not dashes when naming your database.
    - my-database-name (bad database name)
    - my_database_name (good database name)

WordPress will use this database for it's installation.

### 6. Create wp-config.php

Use WP-CLI to create your wp-config.php.

This is your important WordPress configuration file with your database connection information (and other important configuration settings).

```
$ wp core config --dbuser=root --dbpass=root --dbname=ninja_turtles_wp
```

**note:** For MAMP the default user and password is `root`
Make sure to change the database name to the name of your empty database you just created using phpMyAdmin.

If you get a successful message, you should now see a `wp-config.php` file in the root of your WordPress project.

## If you get an Error

You will have to trouble shoot. The following is a common solution if you get this error:

![A common error:](https://i.imgur.com/9Jth4BU.png)

This usually is caused because MAMP can't find mysql or php.

Open your `~/.bash_profile` and put this code at top if it is not there:

`~/.bash_profile`

```
# Use MAMP version of PHP
PHP_VERSION=`ls /Applications/MAMP/bin/php/ | sort -n | tail -1`
export PATH=/Applications/MAMP/bin/php/${PHP_VERSION}/bin:$PATH
export PATH=/Applications/MAMP/Library/bin:$PATH
```

When I work with MAMP I use the `bash` shell and when I'm not working with MAMP I use the `zsh` shell. So I usually jump out of the `zsh` shell with this command:

```
$ exec bash
```

Then I refresh my `.bash_profile` with this command

```
$ source ~/.bash_profile
```

note: If you need to go back to the zsh

```
$ exec zsh
```

and refresh zsh with

```
$ source ~/.zshrc
```

### 7. Finish up WordPress Install

```
$ wp core install --url=http://localhost/folder-name-here --title=YourSiteNameNoSpaces --admin_user=admin --admin_password=password --admin_email=youremail@someemail.com
wp core install --url=http://localhost/wp-ninja-turtles --title=YourSiteNameNoSpaces --admin_user=admin --admin_password=password --admin_email=howley.phil@gmail.com
```

This will create the tables and content of your WordPress install.
* I use `admin` as default user login
* I use `password` as default user password
* Make sure the folder you cloned from github is inside the `Sites` folder and you add this folder name to the end of `http://localhost/PUTHERE`

### 8. Change Theme to your custom WordPress theme

```
$ wp theme activate your-theme-name-here
```

Congratulations. If you get here and you can view your custom theme using Twitter Bootstrap, you have completed the assignment.





