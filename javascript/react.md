# React.js

- A JavaScript library for building fast and interactive user interfaces.
- Developed by Jordan Walke software engineer at Facebook in 2011 for newsfeed. Open-sourced in May 2013 at JavaScript Conference.
- Whenever the app files are saved the webpage will be reloaded(hot reloaded).

## Setup

- For a quick start, optionally code can be written directly in the `.html` with the following scripts without installation for learning purposes.

```html
<head>
  <script
    src="https://unpkg.com/react@16/umd/react.development.js"
    crossorigin
  ></script>
  <script
    src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"
    crossorigin
  ></script>
  <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
</head>
<body>
  <!-- basic layout here -->
  <div class="container"></div>
  <!-- React code -->
  <script type="text/babel">
    // Everything goes here in one place
  </script>
  <body></body>
</body>
```

### Using create-react-app Toolchain

1. Download and Install node.js from its official website
2. Use `Visual Studio Code` with `Simple React Snippets`(enable shortcuts) and `Prettier Plugins` etc.
3. `npx create-react-app <AppFolerName>` to create new project
4. In the app folder, run `npm start` to launch development server in port `localhost: 3000`.
5. `npm test` Launches the test runner in the interactive watch mode. See the section about running tests for more information.
6. `npm run build` Builds the app for production to the `build` folder for hosting. It correctly bundles React in production mode and optimizes the build for the best performance.
7. run `npm run eject`, to stop using the toolchain and configure everything manually(can not recover once the command is ran).

- [Click](https://create-react-app.dev/docs/getting-started) to see the full docs about this tool.

## `index.js`

- `index.js` is the entry point of the react app, it is used to import and associate components and `html` `DOM` elements .

```js
import React from "react"; //get the React library for creating elements and components using jsx syntax.
import ReactDOM from "react-dom"; //Get DOM for component association
import componentName from "./components/componentName";
//import css
import "./cssFile.css";

const element = <h1>Hello World!</h1>; //create new element.
ReactDOM.render(element, document.getElementById("id1")); //associate components with DOM
ReactDOM.render(<ComponentName />, document.getElementById("id2"));
// The elements can also be created using React.createElement() instead of jsx html tags.
ReactDOM.render(
  React.createElement("h1", null, "Hello, World!"),
  document.getElementById("id3")
); // This is what bible does to the jsx code after compiling.
```

## Component

- React app is made up by `components`.
- Based on the use of the components, they can be categorized into two type:
  - `presentational components` are concerned with how things look, they should be stateless. It has only `props` no `state`.
  - `container components` are more concerned with how things work, they are stateful. It contains many presentational components and process state data and passes props to them.

### App Component

- App component(`App.js`) is the root component and it contains other customized components in a tree.
- `app.js` usually is one component that contains all sub-components for the app then to be associated with DOM in index.js.

### Customized Component

- The component class has a `state` property to store internal temp data.
- It has `props` object that stores data, props are readonly. Every component has a `props` object. For data passed from outside use `props` instead of `state`.
- The component class has a render method that returns the component which will be associated with certain a DOM element.
- Component can be represented by JSX file, React html-like `jsx` code in render method will be converted by babel into JavaScript code.
- `<Component />` this is a self closing component.
- `<Component></Component>` it can be used to pass tags and data into its child component’s children props.
- must have exactly one outer element to return as a component.
- For a new customized component, create new `.jsx` files in the component folder.

```js
import React, { Component } from ‘react’;
//import other component that will be used.
import componentName from "./componentName";
// import image if logo.svg is found in /src
import logo from './logo.svg';
// can use css directly here instead of html file
import "./App.css";

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
	};// set default props value here
	Counter.defaultProps = {
		myProp : "Default Text"
	};
	render() {
		//if statement can be used here(after render() and outside return()) for conditional rendering
		let component;
		if(this.state.isGood){
			component = <h1>hi</h1>
		}else{
			component = <h1>bye</h1>
		}
		return (
			//it is used to used to wrap all elements without using parents element like div.
			<React.Fragment>
				<img style={this.styles} src={someURL} className="className1 className2">
				<p style={ {fontSize: 30} }>{this.functionName()}{this.state.data2}</p>
				// map() foreach loop for an array data, each item needs an unique key.
				<ul>{this.state.tags.map(tag=><li key={tag}>{tag}</li>)}</ul>
				//or can be pass into a method which take one element and return a <li>{element}</li>
				<ul> {this.state.comments.map(this.listmethod.bind(this))} </ul>
				//handling events, only pass reference, () is not needed.
				<button onClick={this.handlerMethod}></button>
				// use arrow function to pass argument in the handler function.
				<button onClick={()=>this.handlerWithArg(id)}></button>
				// or pass argument as the second parameter of the bind method.
				<button onClick={this.deleteRow.bind(this, id)}>Delete Row</button>
				// can put any other component in this component
				<ComponentName />
				//any component object has a props object, access by:
				console.log(this.props);
				// access the properties in all scope of this class block, read-only
				console.log(this.block.value);
        		//pass an element to the child Component.
        		//then the element p will be the children property of the <childComponent>
				<childComponent><p>Hello</p></childComponent>
        		//in child component class use {this.props.children} to show the passed element
		      	// pass event handler to child component, in parent component file, declare the event handler. The following child component will have the onClick event as attribute:
				<childComponent commentClicked={this.methodName.bind(this)} />
		      	//child component will have access of this event handler from its parent component as this.this.props.onClick
				<childComponent onClick={this.props.methodName.bind(this)} ><p>Hello</p></childComponent>
				// or if arrow function passed as props
				<childComponent onClick={this.props.methodName}><p>Hello</p></childComponent>
				// input component always work with onChange handler that update a related state variable constantly.
				<input type="text" onChange={this.props.inputStateChange.bind(this)}/>
				// add image
				<img src={logo} className="App-logo" alt="logo" />
			</React.Fragment>
		);
	}
	funtionName() {
		let {data1} = this.state;  //get direct access to data1.
		return <h1>{data1}<h1>;
	}
	handlerMethod() {
		//‘this’ object is not available here, need to bind this to the function by putting this.functionName = this.functionName.bind(this);  in the constructor.
		//or use arrow funciton instead as follows
	}
	handlerMethod = () => {
		//it explicitly ask React to check and pass changed values and refresh the pages.
		// can't be called in render() directly, because whenever page is refreshed setState inside render will be called and refresh the page again.
		this.setState({data1: this.state.data1+1});
	};
	handlerWithArgs = id => {
		//when pass argument is needed, use inline arrow functions
	};
	inputStateChange(x, event) {
		// for a event hanlder the last parameter is always the event object implicitly.
		// input value can be obtained from event.target.value
		this.setState({ input: { name: event.target.value } });
	}


}
export default Counter;
```

- when a component doesn’t have state data(it has everything inside the render function), it can be included inside a function, then the component is called a stateless functional component.

```js
const ComponentName = () => {
  return <div>Hello</div>;
};
export default ComponentName;
```

## React Router

- It works with URL links and redirection for single-page apps made by React.
- In the app folder, run `npm install react-router-dom` to install the module.

```js
import {
  BrowserRouter as Router,
  Route,
  Link,
  NavLink,
} from "react-router-dom";
// BrowserRouter uses HTML5 history API to keep track of URL
// Optionally, HashRouter uses a hash portion of the URL to keep track of URL
<Router>
  // Router Component can only have one child component // They use Link and
  Route Component to make routing work.
  <div>
    // create links and changed the path of the app when link is clicked.
    <Link to="/linkpage/table">About</Link>
    <Link to="/linkpage/list">List</Link>
    // render certain component when the current path matchs
    <Route path="/linkpage/table" component={TableComp} />
    <Route path="/linkpage/list" component={ListComp} />
    // simalar to Link component, plus any matched link will be style in a class
    called active, the active class should be defined in the css
    <NavLink to="/contact">Contact</NavLink>
    // root path will always be in active class, use exact to fix this.
    <NavLink exact to="/">
      Home
    </NavLink>
    // use exact for root path, otherwise it always got renderred.
    <Route exact path="/" component={Home} />
    // to pass variables using in URL
    <Route path="/urlparm/:varName" component={ChildComponent} />
    // In the child component accesss the variable using
    this.props.match.params.varName
  </div>
</Router>;
```

## Life Cycle Hooks

- There are life cycle hooks for every component.
- They are automatically called.
- Stateless functional component has no life cycle hook.

### Mounting Phrase

#### constructor

```js
constrctor(props) {
	super(props);
	//intialize the props and state of the instance
	this.state = {
	name: "world"
	};
}
```

- This is when the component start to render and place to the DOM
- It is called once
- can’t use setState, assign the state directly instead.

#### render

```js
render() {}
```

- It is called after the constructor is called.
- All its child component is also rendered recursively.

#### componentDidMount

```js
compoenetDidMount() {
}
```

- This is after the component is rendered and placed to the DOM
- It can be used for Ajax call, and use setState();

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

- It can be used to see `prevProps` and `prevState`

### Unmounting Phrase

#### componentWillUnmount

- It runs when the component is about to be deleted.
- It is a good place to do clean up.

## React Hooks

- New in React version 16.8
- It enables the use of React features in a functional component.

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
return (
  <button conClick={() => setFunction(prevValue + 1)}>{currentValue}</button>
  //use variable prevValue to get the previous value.
  //work with objects or arrays use: setName({…objectName, propertyName: newValue})
);
```

### Effect Hook

## Debug

- Install React Developer Tools Plugin
- React Tab will be shown in the browser inspector, all component tag will be shown.
