# Node.js

* It is an open-source JavaScript runtime environment.
* It is a program that runs javascript on the server.
* It is built on Google's Chrome V8 open-source JavaScript engine and wrapped with a `C++` program.
* It is asynchronous by default.
* Codes for node.js is contained in `.js` file.
* node.js codes can be run in the command line using `node fileName.js`. console output of the js file will be shown in the terminal after execution.
* `jshint` command runs error check for the js file. It will output the summarized errors message for debugging.
* node.js does not have `window`, `document` objects.

## Installation

* Installer is available from [nodejs.org](https://github.com/Huegoxaga/notes/tree/adac879630f8c70996d8c91e0445523cafcdb81d/javascript/nodejs.org).
  * run `sudo n stable` to update node to the latest stable version
  * run `sudo n latest` to update node to the latest version

### NPM

* It is the package manager for `node.js`.
* `npm install -g npm` update npm.
  * `npm install -g npm@latest` update the npm to the last version.
* `npm install -g <package-name>` -g means install globally.
* `npm install` install packages listed in `package.json` file.
* `npm update` update packages listed in `package.json` file and update the `package.json` file.
* `npm list` see the installed non-global libraries for the current location
* `npm list -g --depth=0` list all globally installed package, only show the root folder name
* `npm root -g` returns the path to the node modules folder
  * use `npm root -g` to return the path to global modules
  * Set environment variable `NODE_PATH` to change the global module folder location
* `npm cache clean --force` delete cache in the `_cacache` folder
  * No recommanded, only do it to free storage space
* `npm cache verify` Verify the contents of the `_cacache` folder, garbage collecting any unneeded data, and verifying the integrity of the cache index and all cached data.
* `npm -g uninstall <package-name> --save` remove global package.
  * `-S` or `--save` will remove packages from `package.json`.

## Global object

* Global object is an object in node.js that contains all the global functions.
* global functions can be used anywhere in node.js code.
* In Browsers these objects belong to window object instead of global object.
* Common global objects
  * console.log\(\);
  * setTimeout\(\);
  * setTimeout\(\); It calls a function after a delay
  * clearTimeout\(\)
  * setInterval\(\); It repeatedly calls a function after a delay.
  * clearInterval\(\);

## Modules

* Every file in node.js is a module that has its own scope. it is private to other files.
* The module file that is run by the server is called the main module.
* Click here to see the [Docs](https://nodejs.org/api/modules.html) about modules
* Each module has a `module` object that stores the module's info.
* Every module file is wrapped by a wrapper function as follow:

```javascript
(function (exports, require, module, __filename, __dirname) {
  // Module code actually lives in here
});
```

* `__filename` is the file name of the current module.
* `__dirname` is the directory name of the current module.
* `module` is a reference to the current module

### Export Modules

* The `module.exports` is a special object which is included in every JavaScript file in the Node.js application by default. The module is a variable that represents the current module, and exports is an object that will be exposed as a module
* A module object has to be exported for other module to use:

```javascript
const getName = () => {
  return 'Tom';
};
exports.getAge = () => {
  return 18;
};
exports.getName = getName;
const exports.NAME = 'Tom';
// can also export class with default values in the constructor
// Optionally use the exports property of a module object
module.exports = {
  functionName: () => {
    return '123';
  },
  variableName: '123',
};
module.exports = {
    firstName: 'James',
    lastName: 'Bond'
}
module.exports = functionName
```

### Import Modules

* A module has to import an exported module object before using it
* `require("filePath")` will return the exports object of the target file

```javascript
const { NAME, getName, getAge } = require("filePath");
```

* extenstion is not required in the filePath

## Buildin Modules

* check the official docs for all builtin Modules.
* Any method name end with `Sync` is a synchronous method.
* Removing Sync from a Synchronous method will make it an asynchronous method, it has a second parameter as the call back function.
* Callback function will be called when the asynchronous operation is completed.
* Most of the callback functions have two parameters. first is the error, the second parameter is the result.

### Path Module

* `require('path');`
* Methods:
  * `.parse(variableName)` It returns the path of the file containing the variable as the argument.
  * `.extname(filename)` get the file extension with the dot
  * `.join(dir, filename)` join path with `/`

### OS Module

* `require('os');`
* Methods:
  * `.totalmem();` total memory
  * `.freemem();` free memory

### File System module

* `require('fs');`
* Methods:
  * `.readdir(folderPath,callBack);` return an array of string for fileNames
  * `.readdirSync(folderPath);` return an array of string for fileNames
  * `.readFileSync(filePath)` load file into file object
  * `const writeStream = fs.createWriteStream(targetFilePath);`, `await awaitWriteStream(file.pipe(writeStream));` write file to `targetFilePath` using write stream

### Events module

* `require('events');`
* This is a class, an object is needed.

  `js const EventEmitter = require('events'); const emitter = new EventEmitter();`

* Method:
  * `.on('eventName',function(eventArgs){//the listener callback function})`
    * add event, eventArgs is optional. it is a json style js object for pass data into the event.
    * same as using `.addListener`
  * `.emit('eventName',(eventObject))` raise an event.
    * eventObject can be `{name1:value1, name2:value2,…}`
    * In practice, Create a new class that extends the EventEmitter class with the defined event listener.`const EventEmitter = require('events'); class ClassName extends EventEmitter{ functionName(){ this.emit(…); } } }`

### HTTP module

* `require('fs');`
* `const server = http.createServer();` create server object, it is inherited from EventEmitter class.
* Methods:
  * `server.on('connection', (socket)=>{…})` add event handler for connection event.
  * `server.listen(portNumber)` make the server listen on certain port.

## Mocha Testing Framework

* It enable `npm test` CLI
* It works with buildin modules `assert`

### Usage

* run `npm install --save mocha` to install
* change the test value to `"mocha"` under `"script"` in the `package.json` file
* run `npm run test` to run test using `mocha`
  * all `*.test.js` files in the `test` folder will be executed from top to bottom, then print out result in each test method

### Method

* `it` method - it takes a test method name and a test method function
* `describe` method - it takes a test case name and a group of `it` methods
* `beforeEach` initial setup for all `it` methods placed after `beforeEach`
* Example:

  ```javascript
  const assert = require("assert");
  //make x global
  let y;
  beforeEach(() => {
    //setup variables here
    y = 3;
  });
  describe("TestCaseName", () => {
    // add async for async functions
    it("methodName1", async () => {
      assert.ok(x);
    });
    it("methodName2", () => {
      assert.equal(y, "2");
    });
  });
  ```

## web3

* It is used to connect to Ethereum network
* Almost all `web3` methods are `async`, it means methods should be followed by `.then()`or use `async/await`
* `web3` version `>1.X.X`supports promises and async/await

### Setup

* run `npm install --save web3` to install
* `const Web3 = require('web3');` to import `web3` constructor
* `const web3 = new Web(networkName.provider());` to connect to the network using the provider provided by various network

### Methods

* `web3.eth.getAccounts()` get a list of all accounts
* `result = await new web3.eth.Contract(JSON.parse(interfaceABIString)).deploy({data: bytecode, arguments: ['contract constructor initial values']}).send({ from: accountsID, gas: '1000000' });` deploy a contract and
  * It returns the contract object with address info in `result.options.address`
* `contractName.methods.functionName().call()` call a public contract function
  * `.send({ from: accountID });` specify the account to make the payment when modify data

## moment

* It parse and manipulate time data
* [Click Here](https://momentjs.com/) to view its official website
* [Click](https://devhints.io/moment) to know more about moment date objects date format
* `var moment = require('moment');`
* `var m = moment();` return current time as a moment object
* `m.format()` return datetime in string
* `var m = moment(timestamp);` convert timestamp to moment object
* `m.add(1, 'day')` get tomorrow as a moment object
* `m.subtract(2, 'days')` get the day before yesterday as a moment object
* `m.isSame(Moment|String|Number|Date|Array);` compoare time and return a boolean value
  * `m.isSameOrAfter('2010-10-21');` compoare time
  * `m.isBefore('2010-10-21', 'year');` compoare year only

### moment-timezone

* It is a package that contains the moment package, plus timezone database
* [Click Here](https://momentjs.com/timezone/) to view its official website
* After installation, `require('moment-timezone')` will have the momnet object with timezone feature enabled

## pm2

* Production manager 2 runs the npm app in the backgroud on a server
* `npm install pm2 -g` install
* In project folder `sudo pm2 start app.js` run the app
* `sudo pm2 startup` automatically start the app after reboot
* `sudo pm2 list` or `sudo pm2 show app` check the current running apps

