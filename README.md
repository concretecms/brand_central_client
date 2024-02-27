
# BrandCentral Client Site

BrandCentral is a little difficult to set up as a standard Concrete package. Unless installed via Composer, some of its dependencies may not be reliably installed. With that in mind, here is a sample client project that should do the following.

1. Install Concrete CMS
2. Install BrandCentral
3. Install our Drop Box Add-On (works well with BrandCentral)

This installs via Composer, which is why this repository is fairly small.

## What is BrandCentral

BrandCentral is a digital asset manager, built on Concrete CMS. It can be found at https://github.com/concretecms/brand_central

## Installation Instructions

### npm and Laravel Mix

(Note: This is not strictly necessary to get BrandCentral to run, but if you think you'll need to ship custom CSS and JS as part of your BrandCentral project, you might want to do this now.)

First, install NPM Packages. You might not use these unless you want to add your custom theme or CSS/JS assets to this repo, but better to have than now than be sorry later. From the root of the project directory, run

    npm i

In the future, if you do make changes to the CSS and JS files within the `resources/` directory, you can build them using `npm run prod` and `npm run dev`. This will be familiar to you if you're used to modern theme development with Concrete CMS and Bedrock. These files will go into `application/css`. The `webpack.mix.js` file can be modified to add new assets, new built asset locations, etc...

### Composer Dependencies

To install Concrete CMS, BrandCentral and its various dependencies, run the following command from the project root directory:

    composer install

This will install all PHP dependencies necessary to run a BrandCentral site.

### Setup public/ as a web root

BrandCentral Client's web root is served out of the `public/` directory in this repository. Ensure that your web server is configured to serve your BrandCentral client website from this directory.

### Install Concrete CMS in public/

Next, install Concrete CMS. You can do this from the web interface via whatever domain you set up to serve content from `public/` or you can do it from the command line found at `public/concrete/bin/concrete`

    public/concrete/bin/concrete c5:install --interactive

This will take you through the process of installing Concrete CMS in an interactive manner:

**Important: While not strictly required, it's recommended that you install a blank starting point like `atomik_blank` when setting up BrandCentral, since you're going to need to remove its content anyway.**

    Checking required preconditions:
      - PHP 7.3... passed (you are running PHP version 8.2.15).
      - MySQL PDO Extension Enabled... passed.
      - JSON Extension Enabled... passed.
      - DOM Extension Enabled... passed.
      - ASP Style Tags Disabled... passed.
      - Fileinfo Extension Enabled... passed.
      - Image Manipulation Available... passed.
      - XML Support... passed.
      - Writable Files and Configuration Directories... passed.
      - Internationalization Support... passed.
      - PHP Comments Preserved... passed.
      - Tokenizer Extension Enabled... passed.
      - Memory limit 64.00 MB.... passed (current memory limit: 512.00 MB).
      Checking optional preconditions:
      - Remote File Importing... passed.
      - Zip Support... passed.
      Location of database server? [127.0.0.1]: localhost
      Database name?: brandcentralclient
      Database username?: root
      Database password?: 
      The system time zone, compatible with the database one? [UTC]: UTC
      Name of the site? [Concrete Site]: BrandCentral Client
      Canonical URL?: http://brandcentralclient.test/
      Alternative canonical URL?: 
      Starting point to use? [atomik_blank]: 
        [0] atomik_full
        [1] elemental_full
        [2] atomik_blank
     > 2
    Email of the admin user of the install? [admin@example.com]: noone@concretecms.com
    Password of the admin user of the install?: 
    Additional user username?: 
    The default interface language (eg en_US)? [en_US]: 
    The default site locale (eg en_US)? [en_US]: 

Once you step through this process, you should see installation commencing:

    5%: Starting installation and creating directories.
    19%: Creating database tables.
    etc...

## Install BrandCentral and its Add-Ons

Next, we need to install BrandCentral and the Drop Box add-on. This can be done most easily from the command line:

    public/concrete/bin/concrete c5:package:install brand_central --full-content-swap

and

    public/concrete/bin/concrete c5:package:install drop_box

Results in:

    ✦ ❯ public/concrete/bin/concrete c5:package:install brand_central --full-content-swap
        Looking for package 'brand_central'... found (Brand Central).
        Checking preconditions... passed.
        Installing... installed.
        Performing full content swap... done.
        
    ✦ ❯ public/concrete/bin/concrete c5:package:install drop_box                         
        Looking for package 'drop_box'... found (Drop Box).
        Checking preconditions... passed.
        Installing... installed.

# Installation Complete

At this point, BrandCentral should be installed, along with the Drop Box add-on.