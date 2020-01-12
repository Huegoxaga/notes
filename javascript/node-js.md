Node.js
It is an open-source JavaScript runtime environment.
It is a program that runs javascript on the server.
It is built on Google's Chrome V8 open-source JavaScript engine, and wrapped with a C++ program.
It is asynchronous by default.
Codes for node.js is contained in .js file.
node.js codes can be run in the command line using node fileName.js. console output of the js file will be shown in the terminal after execution.

jshint command runs error check for the js file. It will output the summarized errors message for debugging.
node.js doesn’t not have window, document objects.
Installer is available for download from nodejs.org.
node --version to check version


global object
global object is an object in node.js that contains all the global functions.
global functions can be used any where in node.js code.
In Browsers these objects belong to window object instead of global object
console.log();
setTimeout();
setTimeout();  //call a function after a delay
clearTimeout()
setInterval();   //repeatedly call a function after a delay.
clearInterval();

Modules
Every file in node.js is a module that has its own scope. it is private to other files.
The module file that is run by the server is called the main module.
each module has a module object that stores the module’s info.
every module has a wrapper function with the following arguments: exports, require, module, __dirname, __filename

A module object has to be exported for other module to use:
const module,exports.objectExportName = objectName;
To export a function
module.exports = functionName

A module has to import an exported module object in order to use it:
const objectName = require(‘filePath’);   (extenstion is not required in the filePath)


Buildin modules
check the official docs for all builtin Modules.

import modules
const modulesName =require(‘moduleName’);

Any method name end with Sync is a synchronous method.
Removing Sync from a Synchronous method will make it an asynchronous method, it has a second parameter as the call back function.
callback function will be called when the asynchronous operation is completed.
Most of the callback functions have two parameters. first is the error, the second parameter is the result.

Path module
require(‘path’);

methods
.parse(variableName)   //return the path of the file containing the variable as the argument.

OS module
require(‘os’);
methods
.totalmem();   	//total memory
.freemem();	//free memory


File System module
require(‘fs’);
.readdir(folderPath,callBack);  return an array of string for fileNames
.readdirSync(folderPath);  return an array of string for fileNames

Events module
require(‘events’);
This is a class, an object is needed.

import and define class
const EventEmitter = require(‘events’);
instantiate an instance of the class
const emitter = new EventEmitter();

.on(‘eventName’,function(eventArgs){//the listener callback function})   
					//add event, eventArgs is optional. it is a json style js object for pass data into the event.
					//same as .addListener

.emit(‘eventName’,(eventObject))   //raise an event.
eventObject can be {name1:value1, name2:value2,…}

In practice, Create a new class that extends the EventEmitter class with the defined event listener.
const EventEmitter = require(‘events’);
class ClassName extends EventEmitter {
	functionName() {
		this.emit(…);
	}
}


HTTP module
require(‘fs’);

const server = http.createServer();   create server object, it is inherited from EventEmitter class.
for server object

server.on(‘connection’, (socket)=>{…})  //add event handler for connection event.
server.listen(portNumber)  //make the server listen on certain port.
