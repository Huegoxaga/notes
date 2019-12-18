# Wechat Mini Program

# Introduction
* Wechat is the most popular messaging app in China developed by Tencent, with over 1.1 billion monthly active user.
* Wechat has deployed unique features like Wechat Pay, Official accounts for articles posting, and Mini Programs for app hosting inside Wechat.
* Wechat Mini Program is like any other web apps, written in JavaScript with its own APIs. It can obtains the user's Wechat account info easily. It can be hosted inside Wechat for free.

# Preparation
To immediately start a project for learning or testing purpose, skips the steps for mini program registration. Download the development tool and create a new project with testing accounts. However, testing account does not have access to cloud services.
* [Register](https://mp.weixin.qq.com/cgi-bin/wx?token=&lang=en_US) a mini program account.
* [Login](https://mp.weixin.qq.com/?lang=en_US) to the account admin page.
* Fill in all required information about the mini program.
* Get the appID.
* [Download](https://developers.weixin.qq.com/miniprogram/en/dev/devtools/download.html) the development tool.
* Login the development tool.
* Create new project with appID and start.

# Files

## Basic File Types
* .json is the configuration files for the mini program.
* .wxml is like html file for the mini program with its own component tags and attributes.
* .wxss is like css file for the mini program with some unique features.
* .js contains the JavaScript codes for the mini program.

## Template Project Files
* Pages folder contains one folder for each page, each page folder has its own  .wxml, .wxss, .json, .js files.
* utils folder contain util.js that contains global utility function for code reuse purpose.
* app.js the JavaScript script file for the entire app.
* app.json this is the configuration file for the mini programs.
* app.wxss is the style sheet for the entire app.
* project.config.json this is the project configuration file for the development tool.

## Create a New Page
There are two ways to create a new page. Either way works, relevant settings will be auto completed.
* Right click Pages folder to create new directory, then right click the new folder and select New Page.
* Add the new page path and name in the pages property in app.json file.
