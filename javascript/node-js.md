# Node.js

- It is an open-source JavaScript runtime environment.
- It is a program that runs javascript on the server.
- It is built on Google's Chrome V8 open-source JavaScript engine and wrapped with a `C++` program.
- It is asynchronous by default.
- Codes for node.js is contained in `.js` file.
- node.js codes can be run in the command line using `node fileName.js`. console output of the js file will be shown in the terminal after execution.
- `jshint` command runs error check for the js file. It will output the summarized errors message for debugging.
- node.js does not have `window`, `document` objects.

## Installation

- Installer is available from [nodejs.org](nodejs.org).

## Global object

- Global object is an object in node.js that contains all the global functions.
- global functions can be used anywhere in node.js code.
- In Browsers these objects belong to window object instead of global object.
- Common global objects
  - console.log();
  - setTimeout();
  - setTimeout(); It calls a function after a delay
  - clearTimeout()
  - setInterval(); It repeatedly calls a function after a delay.
  - clearInterval();

## Modules

- Every file in node.js is a module that has its own scope. it is private to other files.
- The module file that is run by the server is called the main module.
- Click here to see the [Docs](https://nodejs.org/api/modules.html) about modules
- Each module has a `module` object that stores the module's info.
- Every module file is wrapped by a wrapper function as follow:

```js
(function(exports, require, module, __filename, __dirname) {
  // Module code actually lives in here
});
```

- `__filename` is the file name of the current module.
- `__dirname` is the directory name of the current module.
- `module` is a reference to the current module

### Export Modules

A module object has to be exported for other module to use:

```js
const module,exports.objectExportName = objectName;
```

- To export a function: `module.exports = functionName`

### Import Modules

A module has to import an exported module object before using it:

```js
const moduleObjectName = require("filePath");
```

- extenstion is not required in the filePath

## Buildin Modules

- check the official docs for all builtin Modules.
- Any method name end with `Sync` is a synchronous method.
- Removing Sync from a Synchronous method will make it an asynchronous method, it has a second parameter as the call back function.
- Callback function will be called when the asynchronous operation is completed.
- Most of the callback functions have two parameters. first is the error, the second parameter is the result.

### Path Module

- `require('path');`
- Methods:
  - `.parse(variableName)` It returns the path of the file containing the variable as the argument.

### OS Module

- `require('os');`
- Methods:
  - `.totalmem();` total memory
  - `.freemem();` free memory

### File System module

- `require('fs');`
- Methods:
  - `.readdir(folderPath,callBack);` return an array of string for fileNames
  - `.readdirSync(folderPath);` return an array of string for fileNames

### Events module

- `require('events');`
- This is a class, an object is needed.
  `js const EventEmitter = require('events'); const emitter = new EventEmitter();`
- Method:
  - `.on('eventName',function(eventArgs){//the listener callback function})`
    - add event, eventArgs is optional. it is a json style js object for pass data into the event.
    - same as using `.addListener`
  - `.emit('eventName',(eventObject))` raise an event.
    - eventObject can be `{name1:value1, name2:value2,…}`
    - In practice, Create a new class that extends the EventEmitter class with the defined event listener.`const EventEmitter = require('events'); class ClassName extends EventEmitter{ functionName(){ this.emit(…); } } }`

### HTTP module

- `require('fs');`
- `const server = http.createServer();` create server object, it is inherited from EventEmitter class.
- Methods:
  - `server.on('connection', (socket)=>{…})` add event handler for connection event.
  - `server.listen(portNumber)` make the server listen on certain port.
