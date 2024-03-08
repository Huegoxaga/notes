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
3. `npx create-react-app <AppFolerName>` to create project folder with new project files
   - `--use-npm` make sure package is managed with `npm` with `package.json` instead of using `yarn`
4. In the app folder, run `npm start` to launch development server in port `localhost: 3000`.
5. `npm test` Launches the test runner in the interactive watch mode. See the section about running tests for more information.
6. `npm run build` Builds the app for production as static files to the `build` folder for static hosting. It correctly bundles React in production mode and optimizes the build for the best performance.
7. run `npm run eject`, to stop using the toolchain and configure everything manually(can not recover once the command is ran).

- [Click](https://create-react-app.dev/docs/getting-started) to see the full docs about this tool.

### Run Existing Project for Development

- Delete the node_modules folder and any 'lock' files such as `yarn.lock` or `package-lock.json` first, then run `npm install` and `npm start`.

## Project Structure

### `index.js`

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

### `manifest.json`

- The web app manifest is a JSON file is optional for a React App and created by CRA(create-react-app) by default

### `package.json`

- add a `proxy` value can enable proxy, this only has effect in development (with npm start)

### `.env`

- Optionally stores environment variables, for example `REACT_APP_VAR_NAME=value`
- Variables must have prefix `REACT_APP`
- Variables will be accessible under `process.env.REACT_APP_VAR_NAME`
- `.env` file is usually added in `.gitignore`, so it can keep confidential keys locally

### Component Files

- React app is made up by `components`.
- Based on the use of the components, they can be categorized into two type:
  - `presentational components` are concerned with how things look, they should be stateless. It has only `props` no `state`. These components can be written as functional components
  - `container components` are more concerned with how things work, they are stateful. It contains many presentational components and process state data and passes props to them. These components can be written as class components
- When importing packages, use `/` to import sepecific component file rather than using `{}` to import multiple component can reduce the bundle size
  - Install Babel plugin([babel-plugin-import](https://github.com/ant-design/babel-plugin-import), [babel-plugin-transform-imports](https://www.npmjs.com/package/babel-plugin-transform-imports)) can safely import multiple components in one line without incresaing the bundle size

#### App Component

- App component(`App.js`) is the root component and it contains other customized components in a tree.
- `app.js` usually is one component that contains all sub-components for the app then to be associated with DOM in index.js.
- Wrap the entire App component with `<React.StrictMode></React.StrictMode>` will enable the strict mode
  - StrictMode is a tool for highlighting potential problems in an application. It activates additional checks and warnings for its descendants.

## Class Components

- The component class has a `state` property to store internal temp data.
- It has `props` object that stores data, props are readonly. Every component has a `props` object. For data passed from outside use `props` instead of `state`.
- If certain properties from `props` is needed, instead of passing `props` to the components, it can be convenient to use `{property1, property2}`
- The component class has a render method that returns the component which will be associated with certain a DOM element.
- Component can be represented by JSX file, React html-like `jsx` code in render method will be converted by babel into JavaScript code.
- `<Component />` this is a self closing component.
- `<Component></Component>` it can be used to pass tags and data into its child component’s children props.
- must have exactly one outer element to return as a component.
- For a new customized component, create new `.jsx` files in the component folder.
- `createRef()` create a reference to a node that specified in the `ref` property of a component.
  - import, `import { createRef } from "react";`
  - then initialize, `refNode = createRef();`
  - create reference in the component props, `<div ref={this.refNode} />`
  - access the node by using the `current` property of the node reference, `this.textInput.current`

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
			// or simply <> and </>
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

### Life Cycle Hooks

- It works with class components
- There are life cycle hooks for every component.
- They are automatically called.
- Stateless functional component has no life cycle hook.

#### Mounting Phrase

##### constructor

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

##### render

- `render() { return (); }`
- It is called after the constructor is called.
- All its child component is also rendered recursively.

##### componentDidMount

```js
compoenetDidMount() {
}
```

- This is after the component is rendered and placed to the DOM
- It can be used for Ajax call, and use setState();

#### Updating Phrase

It is triggered whenever the state or props of a component changes.

##### Render

- `render() { return (); }`

##### componentDidUpdate

```js
componentDidUpdate(prevProps, prevState){
	//can compare the current and prev value,
	// can make Ajax call only when value changed.
}
```

- It can be used to see `prevProps` and `prevState`

#### Unmounting Phrase

##### componentWillUnmount

- It runs when the component is about to be deleted.
- It is a good place to do clean up.

## Functional Component

- when a component doesn’t have state data(it has everything inside the render function), it can be included inside a function, then the component is called a stateless functional component.
  ```js
  const ComponentName = (props) => {
    return <div>Hello</div>;
  };
  export default ComponentName;
  ```
  ```js
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }
  ```

### React Hooks

- New in React version 16.8
- It works with functional components. Hooks are called inside the body of a functional component
- It enables the use of React features in a functional component

#### State Hook

```js
import {useState}
import React, {useState} from ‘react’

// declare the array before return method.
const [currentValue, setFunction] = useState(initialValue)   //array destructing
// initialValue can be string num bool object array
return (
  <button conClick={() => setFunction(prevValue + 1)}>{currentValue}</button>
  //use variable prevValue to get the previous value.
  //work with objects or arrays use: setName({...objectName, propertyName: newValue})
);
```

- In return method, use `setFunction(newValue)` to update the currentValue.
  - It can also be `setFunction(prevValue => newValue)`, the arrow function take the original value and return a new value
  - For example, `setCountDown((i) => (i === 0 ? (i = 5) : i - 1));`
- `useState()` returns an array of values, the current state value and a function that is used to update values by pass new values in it.
- `useState()` can have an arrow function as its variable, and it will be only ran once when rander.
- `useState()` can have an object as variable.
- `useState()` cannot be placed inside if or loops
- When updating values for reference type values, make sure the reference(memeory address) of the values are changed, or React won't update its related component
- When update the key attribute of any component using state variables, the component will be re-rendered

#### Effect Hook

```js
// Similar to componentDidMount and componentDidUpdate:
useEffect(() => {
  console.log("rendered");
}, []);
```

- First parameter holds a function that will be called everything the component is rendered and rerendered.
- Second parameter holds an array of variables called dependency array. The function in the first parameter will then only be called when variables listed in the dependency array change.
  - All variables in the `useEffect()` are supposed be added to the dependency array, remove the entire dependency array will have the same effect
  - When the second parameter is an empty array, `[]`, The function in the first parameter will be only called once when the component is mounted.
- One component can have multiple `useEffect()` function and they will be executed in order.
- `useEffect` can have return, `return () => {}`. It will be called every time the component is unmounted
- Use the following way to clean a promise inside `useEffect()` hook. Clean up is required if use view another page before the first page is fully loaded.
  ```js
  React.useEffect(() => {
    let isSubscribed = true;
    fetchDATA().then((data) => {
      if (isSubscribed) {
        setData(data);
      }
    });
    return () => (isSubscribed = false);
  }, []);
  ```
- useEffect run in a set interval
  ```js
  useEffect(() => {
    const interval = setInterval(() => {
      console.log("This will run every second!");
    }, 1000);
    return () => clearInterval(interval);
  }, []);
  ```

#### Context Hook

- Makes component share common data across pages
- A component calling useContext will always re-render when the context value changes
- In a `context.js` create the context by using `export const ContextName = createContext(initialValue)`
  - `initialValue` can be null or empty
- In `App.js` use `{%raw%}<ContextName.Provider value={{value1, value2}}> <Toolbar /> </ContextName.Provider>{%endraw%}` to create context and assign values to the context.
- reload will clear all context
- In component class use `const {value1, value2} = useContext(ContextName);` to get values
- Put everything together
  ```js
  const themes = {
    light: {
      foreground: "#000000",
      background: "#eeeeee",
    },
    dark: {
      foreground: "#ffffff",
      background: "#222222",
    },
  };
  const ThemeContext = React.createContext(themes.light);
  function App() {
    return (
      <ThemeContext.Provider value={themes.dark}>
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
  function Toolbar(props) {
    return (
      <div>
        <ThemedButton />
      </div>
    );
  }
  function ThemedButton() {
    const theme = useContext(ThemeContext);
    return (
      <button style={%raw%}{{ background: theme.background, color: theme.foreground }}{%endraw%}>
        I am styled by theme context!
      </button>
    );
  }
  ```

#### Ref Hook

- Updating a `ref` object should be done only inside a useEffect (or useLayoutEffect) or inside an event handler.
- Initialize a `ref` object, `const refContainer = useRef(initialValue);`

##### Create a Node Object

```js
const node = useRef();

focusNode = () => node.current.focus();

return (
  <div>
    <input type="text" ref={node} />
    <button onClick={focusNode}>Focus the text input</button>
  </div>
);
```

##### Declare a Non-react Variable

- When the `.current` property of the `ref` object is assigned a value, it will not cause the component to re-render

#### Reducer Hook

- It changes variable values like `useState`
- It is good at handling complex state interactions

```js
// Set strings names for each action type
const ACTIONS = {
  INCREMENT: "increment",
  DECREMENT: "decrement",
  RESET: "reset",
  CHANGE_COUNT: "change-count",
};

// Modify value based on action type, action has properties type and payload
function reducer(count, action) {
  switch (action.type) {
    case ACTIONS.INCREMENT:
      return count + 1;
    case ACTIONS.DECREMENT:
      return count - 1;
    case ACTIONS.RESET:
      return 0;
    case ACTIONS.CHANGE_COUNT:
      return count + action.payload.amount;
    default:
      return count;
  }
}

function Counter() {
  // Declear reducer with default value and function contains action definition
  const [count, dispatch] = useReducer(reducer, 0);

  return (
    <>
      <span>{count}</span>
      <button onClick={() => dispatch({ type: ACTIONS.INCREMENT })}>+</button>
      <button onClick={() => dispatch({ type: ACTIONS.DECREMENT })}>-</button>
      <button
        onClick={() => {
          dispatch({
            type: ACTIONS.CHANGE_COUNT,
            payload: { amount: 5 },
          });
        }}
      >
        Add 5
      </button>
      <button onClick={() => dispatch({ type: ACTIONS.RESET })}>Reset</button>
    </>
  );
}
```

## Higher-order Component(HOC)

- A higher-order component is a function that takes a child component as an argument and returns a new, complete component wrapped with the child component
- Definition
  ```js
  import React from "react";
  const higherOrderComponentFunction = (WrappedComponent) => {
    class HOC extends React.Component {
      render() {
        // passes props from WrappedComponent in this.props, then add a newProp
        return <WrappedComponent {...this.props} newProp={123} />;
      }
    }
    return HOC;
  };
  export default higherOrderComponentFunction;
  ```
- Invoke - `const SimpleHOC = higherOrderComponentFunction(MyComponent);`

## React Router

- It works with URL links and redirection for single-page apps made by React.
- Typying new addresses and pressing enter key will reload the entire app, this is different from the SPA's way of routing pages.
- In the app folder, run `npm install react-router-dom` to install the module.

```jsx
import {
  BrowserRouter as Router,
  Route,
  Link,
  NavLink,
} from "react-router-dom";
// BrowserRouter uses HTML5 history API to keep track of URL, it requires additional setup when build
// Optionally, HashRouter uses a hash portion of the URL to keep track of URL
<Router>
  // Router Component can only have one child component
  // They use Link and Route Component to make routing work.
  // path that does not start with "/" will be a relative path
  <div>
    // create links and changed the path of the app when link is clicked.
    <Link to="/linkpage/table">About</Link>
    <Link to="/linkpage/list">List</Link>
    // render certain component when the current path matchs
    <Route path="/linkpage/table" component={TableComp} />
    <Route path="/linkpage/list" component={ListComp} />
    // simalar to Link component, plus any matched link will be style in a class
    called active, the active class should be defined in the css
    // multiple path can use regex path="/(home|users|widgets)/"
    // or use array path={["/home", "/users", "/widgets"]}
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
    // Switch will make will only first match will be rendered
    <Switch>
      // Move the root match to the last, since / will match all path
      // It cannot be nested and only work for components that are one level deeper
      <Route exact path="/other" component={Other} />
      <Route exact path="/" component={Home} />
    <Switch>
  </div>
</Router>;
```

- Components accessed through `<Route>` will have access to `this.props.history` and can use `history.push(path)` to redirect pages
  - When component is not included in a `Route` tag can also wants to use `history.push`, import `import { withRouter} from "react-router-dom";` and use `export default withRouter(ComponentName)` during exporting

## google-map-react

- The node package for google map component
- [Click Here](https://www.npmjs.com/package/google-map-react) to view the package site
- [Click Here](https://snazzymaps.com) to get more free map styles
  - to apply for styles add map props `{%raw%}options= {{styles: styleObject}}{%endraw%}`
- The container of the map component must have a width and a height

## Material UI

- The Bootstrap for React
- [Click](https://material-ui.com/getting-started/installation/) to see its Docs.
- It provide a quick way to implement UI specified by Material Design
  - Material Design is a design language(guilde) that Google developed in 2014
  - [Click Here](https://material.io/components) to see the UI compoenents examples from Material Design
- Recommanded responsive meta tag for React app using material UI `<meta name="viewport" content="minimum-scale=1, initial-scale=1 width=device-width"/>`

### Components

- Material UI provides predefined components, each with various `props` that can be used to modify the components' styles. Details are explained in the docs's API section
- [Click Here](https://material-ui.com/components/buttons/) to read the complete docs for all Material UI Components
- There are two CDN links for loading material components for quick prototyping
  - one for development: https://unpkg.com/@material-ui/core@latest/umd/material-ui.development.js
  - one for production: https://unpkg.com/@material-ui/core@latest/umd/material-ui.production.min.js
- For production, it is recommended to run `npm install @material-ui/core`
- Example
  ```js
  import React from "react";
  import ReactDOM from "react-dom";
  import Button from "@material-ui/core/Button";
  function App() {
    return (
      <Button variant="contained" color="primary">
        Hello World
      </Button>
    );
  }
  ```

#### CSS Baseline

- It is used to reset the pages' css
- `<CssBaseline />` will reset the CSS style globally
- `<ScopedCssBaseline></ScopedCssBaseline>` will reset CSS of components wrapped inside

#### Paper

- It provides a backgroud for all the components inside
- It has an `elevation` property value range from `0` to `24`(default `1`). It control the shade level below the `Paper`
- The `square` property takes a boolean value(default) when `true` the border radius will be set to 0

#### Drawer

- It is a side menu

#### Lists

- Lists are a continuous group of text or images. They are composed of items containing primary and supplemental actions, which are represented by icons and text.
  - The items can be any component specified in the props of the `<ListItem>` tag(like `button` in the example)

```js
<List>
  <ListItem button>
    <ListItemIcon>
      <Icon />
    </ListItemIcon>
    <ListItemText primary="First Item" />
  </ListItem>
  <ListItem button>
    <ListItemIcon>
      <Icon />
    </ListItemIcon>
    <ListItemText primary="Second Item" />
  </ListItem>
</List>
```

#### AppBar

- It is a top navigation bar
- It works with `<ToolBar>` component
- It has a `position` props that can be set to `static`, `fixed`

#### ToolBar

- It is a tool bar that can contain menu icons, search bar, text.
- It has a `variant` props that can be set to `dense`, `regular`(default)

#### Menu

- It has a `anchorEl` property to keep track of the event target location and use it as anchor for displaying menu

#### Table

```js
//<TableContainer> optional, it wraps the table
//the optional `component` props defines the table's root node component type(default `'div'`)
<TableContainer component={Paper}>
  // <Table> has style props minWidth: 650. it will create horizontal scroll bar when
  width smaller than min width(There is a built in min width)
  <Table style={{minWidth: 650}}>
    <TableHead>
      <TableRow>
        <TableCell>Dessert (100g serving)</TableCell>
        <TableCell align="right">Calories</TableCell>
        <TableCell align="right">Fat&nbsp;(g)</TableCell>
        <TableCell align="right">Carbs&nbsp;(g)</TableCell>
        <TableCell align="right">Protein&nbsp;(g)</TableCell>
      </TableRow>
    </TableHead>
    <TableBody>
      {rows.map((row) => (
        <TableRow key={row.name}>
          <TableCell component="th" scope="row">
            {row.name}
          </TableCell>
          <TableCell align="right">{row.calories}</TableCell>
          <TableCell align="right">{row.fat}</TableCell>
          <TableCell align="right">{row.carbs}</TableCell>
          <TableCell align="right">{row.protein}</TableCell>
        </TableRow>
      ))}
    </TableBody>
  </Table>
</TableContainer>
```

#### Grid

- It is used to control the layout of the entire web app
- Grid is a flexbox container
- It can be either `<Grid container></Grid>` or `<Grid item></Grid>`
  - Component's style property will only activated when the corresponding `container` or `item` type is specified
- Grid item can have width from `1` to `12`. `12` takes `100%` of the width
  - Width should be specified for a certain breakpoint. e.g. `xs=12`

#### Hidden

- Anything inside the `<Hidden>` tag will be hidden based on the breakpoint set in the props

#### Typography

- The default font is `Roboto`
  - It requires the link to load the font, `<link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" />`
  - optionally, it can be installed by running `npm install fontsource-roboto` and then imported by using `import 'fontsource-roboto';`
- `Typography` is a component and wrap around texts with `props` that controls the styles of the text

#### Menu

- Add `getContentAnchorEl={null}` to its props, so it won't block the menu button

#### Icons

##### Standardized Material Design

- Material Design has standardized over 1,100 official icons, each in five different "themes" (see below)
- run `npm install @material-ui/icons` to install prebuilt SVG icon package
  - The `core` package is required by the `icon` package
- `import { AccessAlarm, ThreeDRotation } from '@material-ui/icons';` import the selected icon component and use it directly
- Each icon also has a "theme": `Filled` (default), `Outlined`, `Rounded`, `TwoTone` and `Sharp`. If you want to import the icon component with a theme other than default, append the theme name to the icon name directly without any space. For example `@material-ui/icons/DeleteRounded` for `Delete` icon in `Rounded` theme
- [Click Here](https://material-ui.com/components/material-icons/) to see all icons

##### SvgIcon

##### Icon

- The font `Icon` component has the slowest performance
- It requires a link to the material icons font, `<link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons" />`

### Style

- Each material UI component has a global class name, these names can be used to define styles
- In `App.js` the web app can be wraped by `{%raw%}<Paper style={{ height: "100vh" }}> </Paper>{%endraw%}` to provide a backgroud

#### makeStyles Hook

```js
import React from "react";
import { makeStyles } from "@material-ui/core/styles";
import Button from "@material-ui/core/Button";

const useStyles = makeStyles({
  root: {
    background: "linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)",
    border: 0,
    borderRadius: 3,
    boxShadow: "0 3px 5px 2px rgba(255, 105, 135, .3)",
    color: "white",
    height: 48,
    padding: "0 30px",
    //use variables
    width: `calc(100% - ${SIDE_MENU_WIDTH}px)`,
    // css when mouse hover over the element
    "&:hover": {
      background: "#f00",
      border: "1px solid black",
    },
  },
});

export default function Hook() {
  const classes = useStyles({ variable });
  return <Button className={classes.root}>Hook</Button>;
}
```

- pass a variable into `useStyles()`, so CSS properties can be set based on that variable in``makeSytles`, e.g. `color: variable => (variable ? 'black' : 'red')`
- makeStyles can take theme as input and get theme objects values

```js
const useStyles = makeStyles((theme) => ({
  root: {
    flexGrow: 1,
  },
  menuButton: {
    marginRight: theme.spacing(2),
  },
  title: {
    flexGrow: 1,
  },
}));
```

- styles based breakpoints

```js
const useStyles = makeStyles((theme) => ({
  root: {
    backgroundColor: "blue",
    [theme.breakpoints.up("md")]: {
      backgroundColor: "red",
    },
    //or
    [theme.breakpoints.down("md")]: {
      backgroundColor: "red",
    },
  },
}));
```

#### Styled components

```js
import React from "react";
import { styled } from "@material-ui/core/styles";
import Button from "@material-ui/core/Button";

const MyButton = styled(Button)({
  background: "linear-gradient(45deg, #FE6B8B 30%, #FF8E53 90%)",
  border: 0,
  borderRadius: 3,
  boxShadow: "0 3px 5px 2px rgba(255, 105, 135, .3)",
  color: "white",
  height: 48,
  padding: "0 30px",
});

export default function StyledComponents() {
  return <MyButton>Styled Components</MyButton>;
}
```

### Theme

- It controls the global styles of all other components
- [Click Here](https://material-ui.com/customization/default-theme/) to check the default styles of all components
- Colors imported from Material UI packages include `dark`, `light`, and `main` properties

#### Customize Theme

- Create a theme `.js` file, define and export the new theme, everything else will still be set to default value
- `palette: {type: 'dark'}` will set the theme to be in dark mode
  - To allows the user to can theme mode dynamically, use a `darkMode` bool variable as `palette: {type: darkMode ? "dark" : "light"}`
  ```js
  import { createMuiTheme } from "@material-ui/core/styles";
  import purple from "@material-ui/core/colors/purple";
  import green from "@material-ui/core/colors/green";
  const theme = createMuiTheme({
    palette: {
      primary: {
        main: purple[500],
      },
      secondary: {
        main: green[500],
      },
    },
  });
  ```
- In `App.js` wrap the component that adapts themes with the theme provider components, e.g. `<ThemeProvider theme={newTheme}> <Component /> </ThemeProvider>`
- Similar to `useStyles()`, the `const theme = useTheme();` method will return a variable that contains all the current theme settings

### Related Packages

#### Material Tables

- It provides a pre-built table component based on Material UI
- run `npm install material-table --save` to install
- [Click Here](https://material-table.com/#/docs/all-props) to view all props for the table component

#### Material-UI pickers

- It provices a datetime picker component
- run `npm i @material-ui/pickers` to install
- run `npm i @date-io/date-fns@1.x date-fns` to install a date management library
- wrap the picker component with `<MuiPickersUtilsProvider utils={DateFnsUtils}></MuiPickersUtilsProvider>`
- [Click Here](https://material-ui-pickers.dev/api/DatePicker) to view all props for the date picker component

## Debug

- Install React Developer Tools Plugin
- React Tab will be shown in the browser inspector, all component tag will be shown.
- `open -n -a /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --args --user-data-dir=/tmp/chrome_dev_test --disable-web-security` open a Broswer with no security requirement.
- statement `debugger;` will trigger the debugger to run when the program reaches that particular line.
