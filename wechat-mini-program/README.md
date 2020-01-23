# Wechat Mini Program

# Introduction
* Wechat is the most popular messaging app in China developed by Tencent, with over 1.1 billion monthly active user (2019).
* Wechat has deployed unique features like Wechat Pay, Official accounts for articles posting, and Mini Programs for app hosting inside Wechat.
* Wechat Mini Program is like any other web apps, written in JavaScript with the help of its own APIs. It can obtains the user's Wechat account info easily. It can be hosted inside Wechat for free.

# Preparation

* [Register](https://mp.weixin.qq.com/cgi-bin/wx?token=&lang=en_US) a mini program account.
* [Login](https://mp.weixin.qq.com/?lang=en_US) to the account admin page.
* Fill in all required information about the mini program.
* Get the appID.
* [Download](https://developers.weixin.qq.com/miniprogram/en/dev/devtools/download.html) the development tool.
* Login the development tool.
* Create new project with appID and start.

>_**Notes**_:
* _To immediately start a project for learning or testing purpose, skips the steps for mini program registration. Download the development tool and create a new project with testing accounts. However, testing account does not have access to cloud services._
* _For newly created projects, Cloud Services will not be available within the first 10 min._


# Files

## Template Project Folder
* Pages folder contains 4 files for each page in one folder, each page folder has its own  .wxml, .wxss, .json, .js files.
* utils folder contain js files(util.js) that has global utility functions for code reuse purpose.
* app.js the JavaScript script file for the entire app.
* app.json this is the configuration file for the entire mini programs.
* app.wxss is the style sheet for the entire app.
* project.config.json this is the project configuration file for the development tool.

### json file
* It is the configuration files for the mini program.
* The properties set in the json file from each page folder overrides the properties set in the app.json file.
* All of the properties are enclosed by one set of curly brackets.
```json
{
  "property1": "value",
  "property2": true,
  "property3": {},
}
```

#### Global Configuration
[Click](https://developers.weixin.qq.com/miniprogram/en/dev/reference/configuration/app.html) to see a complete list of Global Configuration.

##### pages
```json
  "pages": [
    "folderPath/pageName"
 ]
 ```
 * The pages property stores an array of the wxml file path for each page.
 * The file extension is not required.

##### window
```json
"window": {
  "backgroundTextStyle": "light",
  "navigationBarBackgroundColor": "#620933",
  "navigationBarTitleText": "Page Title",
  "navigationBarTextStyle": "white",
  "enablePullDownRefresh": true
}
```
* window property set the page's general property like background color and text styles.

##### tabBar
```json
"tabBar": {
  "color": "#626567",
  "selectedColor": "#620933",
  "backgroundColor": "#FBFBFB",
  "borderStyle": "white",
  "list": [
    {
      "pagePath": "pages/discovery/discovery",
      "text": "",
      "iconPath": "images/discovery.png",
      "selectedIconPath": "images/discovery_focus.png"
    },
    {
      "pagePath": "pages/index/index",
      "text": "",
      "iconPath": "images/index.png",
      "selectedIconPath": "images/index_focus.png"
    },
    {
      "pagePath": "pages/more/more",
      "text": "",
      "iconPath": "images/user.png",
      "selectedIconPath": "images/user_focus.png"
    }
  ]
},
```

* tabBar property is used to set the tab bar of the mini program.
* It should be set in the app.json file.

##### networkTimeout
```json
"networkTimeout": {
  "request": 10000,
  "downloadFile": 10000
},
```

* It is used to setup the connection property of the program.
* It should be set in the app.json file.

#### Page Configuration
* Most of the properties inside the global window property can be used directly as Page Configuration in page.json file, inside ``{}``.
  ```json
  {
    "navigationBarTitleText": "Page Title"
  }
  ```
* [Click](https://developers.weixin.qq.com/miniprogram/en/dev/reference/configuration/page.html) to see a complete list of Page Configuration.

### js file
* .js contains the JavaScript codes for the mini program.
* For ```app.js```, all data and function are enclosed as properties of ```APP({ })```.
* For ```pageName.js``` in each page folder, all data and function are enclosed as properties of ```Page({ })```.
* ```APP({ })``` or ```Page({ })``` is used to register an App or Page to the program. It is mandatory, even if no data or function is needed for the page.
* For js file of each page, before ```Page({ })```, ```var app = getApp()``` is used to access data and function from ```app.js```.
* Use ```var util = require('../../utils/util.js')``` in the first line of js file, to access util functions.
* There is a data object in ```APP({ })``` or ```Page({ })``` in js file. The data object stores data for the current app or page.
* ``this.getData``, ``this.setData`` are used to access the ``data`` object in the ``.js`` file.

#### wx API
[Click](https://developers.weixin.qq.com/miniprogram/en/dev/api/open-api/login/wx.login.html) to see complete list of wx methods.

#### Program Life Cycle
* ``onLaunch``, environment setup is done in this phrase.
```js
onLaunch: function () {
  //clear globalData
  this.globalData = {}
}
```


### wxml file
* ``.wxml``, or WeiXin Markup Language File controls the layout of the mini program with its own component tags and attributes.
* [Click](https://developers.weixin.qq.com/miniprogram/en/dev/reference/wxml/) to see the basic syntax.

#### Attributes


id
class
style
hidden   //set true to hide, set false to show
data-dataName   //store data information
bind-Anyname    //bind with an event handler
cache-Anyname	 //bind with an event handler


#### Components
[Click](https://developers.weixin.qq.com/miniprogram/en/dev/component/) to see a list of basic components.

view tag  //
block tag // contain data setting

button tag
	bindtag: use this outside the form
	form-type: use this when button is inside the form


form tag
	bindsubmit


input tag
	name
	placeholder

### wxss file
* ``.wxss`` file is the style sheet for the mini program.
* wxss file uses rpx, the responsive pixel, the total width is 750rpx for all screen.
* In wxss, use ``@import 'filePath.wxss'`` to import style sheet from other wxss file.


## Create a New Page
There are two ways to create a new page. Either way works, relevant settings will be auto completed.
* Right click Pages folder to create new directory, then right click the new folder and select New Page.
* Add the new page path and name in the pages property in app.json file.

## Cloud Services
### Initialize
1. Open Cloud Base and Enter a preferred environment name, an environment ID will be auto generated.
2. Create new collection in cloud base console.
3. Initialize the Cloud Services in the ``app.js``'s ``onLaunch`` function.
  ```js
  if (!wx.cloud) {
    console.error('Please lib version 2.2.3 or above.')
  } else {
    wx.cloud.init({
      // enter the cloud environment id here.
      // It can be found in the cloud base panel/Setting.
      env: 'env-id',
      traceUser: true,
    })
  }
  ```

### Usage
##### Create
* Template, the cloud function returns an async function with the following implementation.
  ```js
  // get sdk
  const cloud = require('wx-server-sdk')
  cloud.init()
  // get ref
  const db = cloud.database();
  // cloud function goes inside.
  exports.main = async (event, context) => {
    // return a function here.
    return await db.collection("posts").where({}).get();
  }
  ```
* Read Data
  * Return the following function to read data from cloud database(collection).
  ```js
  return await db.collection("posts").where({}).get();
  ```
* Update Data
  * Return the following function to update data on cloud database(collection).
  ```js
  return await db.collection("posts").doc(event.id).update({
    data: {
      votes: db.command.inc(1)
    }
  })
  ```
* Write Data
  * Return the following function to insert data to cloud database(collection).
  ```js
  return await db.collection("posts").add({
      data: {
        content: event.content,
        votes: 0
      }
    })
  ```

##### Upload
* Right click on the cloud function and upload it.
##### Call
* in the js file for all pages, use ``wx.cloud.callFunction()`` to call a cloud function.
  ```js
  wx.cloud.callFunction({
      name: "cloudFunctionName",
      data: {
        //pass function parameters
        id: this.data.id
      },
      success: (res) => {
        //callback after
      },
      fail: console.error
    })
  ```

  
## Preview and Publish the App
* Click upload button in the IDE to upload the trial version.
* In the mini-program console, select review, the publish it.
