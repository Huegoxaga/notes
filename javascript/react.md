# React.js
* A JavaScript library for building fast and interactive user interfaces.
* It is developed by facebook.
* Whenever the app files are saved the webpage will be reloaded(hot reloaded).

## Setup
### Installation
1. Download and Install node.js from its official website
2. ``run sudo npm i -g create-react-app``
3. Use Visual Studio Code with Simple React Snippets(enable shortcuts) and Prettier Plugins etc.

### Create an React App
1. create-react-app appFolderName
2. in app folder, run ``npm start`` to launch development server in port localhost: 3000.

### Configuration for production Environment
``npm run eject``

## ``index.js``
``index.js`` is the entry point of the react app, it is used to import and associate components and html DOM elements .
```js
import React from "react";  //get the React library for creating elements and components using jsx syntax.
import ReactDOM from "react-dom";//Get DOM for component association
import componentName from "./components/componentName";
//import css
import "./cssFile.css";

const element = <h1>Hello World!</h1>  //create new element.
ReactDOM.render(element, document.getElementById("id1"));  //associate components with DOM
ReactDOM.render(<ComponentName />, document.getElementById("id2"));
```

## Component
* React app is made up by UI component.
### App Component
* App component(``App.js``) is the root component and it contains other customized components in a tree.
* app.js usually is one component that contains all sub-components for the app then to be associated with DOM in index.js.
### Customized Component
* Component class has a ``state`` property to store temp data.
* It has ``props`` object that stores data, props is readonly. every component has a ``props`` object. For single source data use props instead.
* Component class has a render method that returns component that associated with certain DOM element.
* Component can be represented by JSX file, React html like jsx code in render method will be converted by babel into JavaScript code.
* ``<Component />`` this is a self closing component.
* ``<Component></Component>``  it can be used to pass tags and data into its child component’s children props.
* Only one parent element is allowed to return as a component.
* For a new customized component, create new jsx files in the component folder.
```js
import React, { Component } from ‘react’;
import componentName from "./componentName";
 //import other component that will be used.
class Counter extends Component {
	//its local variable, only initiated when instance of the component is created.
	state = {
		data1: 0,
		data2: "hi" ,
		someURL: "https//google.com",
		tags: [‘tag1’,’tag2’,’tag3’]
	};
	styles = {
		fontWeight: ‘bold’,  //use camel case css attributes.
		fontSize: 10
	};
	render() {
		return (
	//it is used to used to wrap all elements without using parents element like div.
			<React.Fragment>
				<img style={this.styles} src={someURL} className="className1 className2">
				<p style={{fontSize: 30}} >{this.functionName()}{this.state.data2}</p>
				//map() foreach loop for an array data, each item needs a key.
				<ul>{this.state.tages.map(tag=><li key={tag}>{tag}</li>)}</ul>
				//handling events, only pass reference, () is not needed.
				<button onClick={this.handlerMethod}></button>
				// or
				// use arrow function to pass argument in the handler function.
				<button onClick={( )=>this.handlerWithArg(id)}></button>
				// can put any other component in this component
				<ComponentName />
				//any component object has a props object, to get it								console.log(this.props);
				// access of properties in all scope of this class block, read-only
				console.log(this.block.value);
        //pass an element to the child Component.
        //then the element p will be the children property of the <childComponent>
				<childComponent><p>Hello</p></childComponent>
        //in child component class use {this.props.children} to show the passed element
		      // pass event handler to child component, in parent component file, declare event handler and return, the following child component with eventName(like onClick) as attribute:

        <childComponent eventName={this.eventHandler}><p>Hello</p></childComponent>
		      //child component will have access of this event handler from its parent component as this.props.eventName
			</React.Fragment>
		);
	}

	funtionName() {
		let {data1} = this.state;  //get direct access to data1.
		return <h1>{data1}<h1>;
	}
	handlerMethod() {
		//‘this’ object is not available here, need to bind this to the function by putting this.functionName = this.functionName.bind(this);  in the constructor.
		//or use => instead as follows
	}
	handlerMethod = ( ) => {
		this.setState({data1: this.state.data1+1});
//it explicitly ask React to check and pass changed values and refresh the pages.
//when pass argument is needed, use inline arrow functions
};
	handlerWithArgs = id => {
};
}
export default Counter;
```

* when a component doesn’t have state data(it has everything inside the render function), it can be included inside a function, then the component is called a stateless functional component.
```js
const ComponentName = ( ) => {
	return <div>Hello</div>;
}
export default ComponentName;
```

## Life Cycle Hooks
* There is a life cycle hooks for every components
* They are automatically called.
* Stateless functional component has no life cycle hook.

### Mounting Phrase

#### constructor
```js
constrctor(props) {
	super(props);
	//intialize the props and state of the instance
}
```
* This is when the component start to render and place to the DOM
* It is called once
* can’t use setState, assign the state directly instead.
```js
this.state = {
        name: 'world'
      }
```

#### render
```js
render() {}
```
* It is called after constructor is called.
* All its child component is also rendered recursively.

#### componentDidMount
```js
compoenetDidMount() {
}
```
* This is after the component is rendered and placed to the DOM
* It can be used for Ajax call, and use setState();

### Updating Phrase
It is triggered whenever the state or props of a component changes.

#### Render
#### componentDidUpdate
```js
componentDidUpdate(prevProps,prevState){
	//can compare the current and prev value,
	// can make Ajax call only when value changed.
}
```
* It can be used to see prevProps and prevState

### Unmounting Phrase
#### componentWillUnmount
* It runs when the component is about to be deleted.
* It is good place to do clean up.

## React Hooks
* New in React version 16.8
* It enable the use of React features in a functional component.

### State Hook
```js
import {useState}
import React, {useState} from ‘react’

// declare the array before return method.
const [currentValue, setFunction] = useState(initialValue)   //array destructing
// initialValue can be string num bool object array
```

In return method, use setFunction(newValue) to update the currentValue.
```js
return(
	<button conClick={( ) => setFunction(prevValue+1)}>{currentValue}</button>
//use variable prevValue to get the previous value.
//work with objects or arrays use: setName({…objectName, propertyName: newValue})
)
```

### Effect Hook

## Debug
* Install React Developer Tools Plugin
* React Tab will be shown in the browser inspector, all component tag will be shown.
