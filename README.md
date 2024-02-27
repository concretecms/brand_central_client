
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