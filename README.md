# React-Redux Fundamentals
<a href='https://facebook.github.io/react/'><img src="https://react-etc.net/files/2016-07/logo-578x270.png" alt="React Logo" height="50"></a> 
<a href='https://jsx.github.io/'><img src="https://camo.githubusercontent.com/2b0b2c776d6cba46731b722570bdef902dd213d2/687474703a2f2f692e696d6775722e636f6d2f58636637692e706e67" alt="JSX's proposed logo" height="50"></a> 
<a href='https://jsx.github.io/'><img src="https://frontendmasters.com/assets/es6-logo.png" alt="ES6" height="50"></a> 

Notes on the fundamentals of React and  handing state in Redux. Created in my free time for the benefit of my team at TD and me to more easily adopt React.

## Table of Contents

- [Introduction](#introduction)
	- [What is React?](#what-is-react)
	- [How does it compare to Angular?](#how-does-it-compare-to-angular)
	- [What is JSX?](what-is-jsx)
	- [What is ES6?](#what-is-es6)
- [React Basics](#react-basics)
	- [Components](#components)
	- [React and ReactDOM](#react-and-reactdom)
	- [Creating an Application and Adding a Component](#creating-an-application-and-adding-a-component)
	- [Kinds of Components](#kinds-of-components)

## Introduction

### What is React?

"React is a declarative, efficient, and flexible JavaScript library for building user interfaces." It is the View in the MVC model.


### How does React compare to Angular?

When directly contrasting React to a framework like Angular, many people really mean "React + Redux (or any state container) + related technologies." 

Compared to Angular 1, it's almost contest. Many argue that learning React is easier than Angular as it doesn't require reading jargon-full documentation that leaves you chasing a confusing rabbit hole of new terms and patterns that seemingly never end. (It does end eventually, sometime after you're done comparing providers, factories, and services.) In terms of performance, with Angular 1's poorer dirty checking, React blows Angular 1 out of the water.

But clearly its competitor as a framework in 2017 is Angular >2 (which I'll refer to as simply Angular henceforth), right? In terms of performance, it performs just as well as React v15. React v16, React Fiber, is looking to be significantly more performant however, so its debatable if it'll stay that way after this summer. Angular also requires TypeScript, which some people love for its typing, and other diehard ES6 fans may dislike. 

Most importantly however, many developers groan that the Angular team changes syntax and APIs 'too much' between major versions, making it difficult/annoying to port over older Angular applications. Many enterprises don't have the luxury/budget to port each Angular 1 application to 2 or 4, and either stay stuck in Angular 1, or have to learn what functionally is two different frameworks. On the other hand, perhaps Facebook noted this concern or is just really happy with their APIs, but their up and coming React Fiber,  will use >99% of the same APIs! To developers already using React, this is great news that there's little to no migration needs with all the benefit of performance increases.

If you're interested in [performance specifics or nitty-gritty details](https://medium.com/javascript-scene/angular-2-vs-react-the-ultimate-dance-off-60e7dfbc379c), there are plenty of articles that would do a better job than me in explaining.

### What is JSX?

JSX is a preprocessor language that adds XML (cough, HTML) syntax to JavaScript. Most React developers use JSX. Before you groan about another language you'll have to learn, you're actually free to use React without JSX! But trust me, you'll want to anyways.

Compare React with JSX:

```
let groceries = () => <div>
  <ul>
    <li>Campbell Soup</li>
     <li>Instant Ramen</li>
      <li>Kimchi</li>
  </ul>
</div> // Beautiful! It's like HTML! 
```
React without JSX:
```
let groceries = () => React.createElement(
  "div",
  null,
  React.createElement(
    "ul",
    null,
    React.createElement(
      "li",
      null,
      "Campbell Soup"
    ),
    React.createElement(
      "li",
      null,
      "CookInstant Ramenies"
    ),
    React.createElement(
      "li",
      null,
      "Kimchi"
    ) // Kill...
  )   // Me...
);    // Now...
```

Without even knowing React or its syntax, that convinced you pretty quick to use JSX, didn't it?

### What is ES6?

EMCAScript 6, a particular newer specification of JavaScript that changed a lot of things for the better, is often referred to as ES6. If you're used to 'regular old' JavaScript, you're probably thinking of ES5 or an older specification. ES6 is also mandatory while using React because React relies on classes and other new features. Many people who share sample code in React will use ES6 liberally -- for good reason!

If you're unfamiliar with JS6, it's highly recommended you at least learn about classes, fat arrows, let, and const before you start with React. [Babel has a great summary of what ES6 offers.](https://babeljs.io/learn-es2015/)

If you're worried about browser compatibility, don't sweat it. That's why [Babel](https://babeljs.io/) works so closely with React, ensuring your code, whether it be ES6, ES7, or JSX,  gets transpiled to ye old ES5. Babel is an essential part of your build process when using React.

You may use TypeScript instead, which also has many key features of ES6, but you're going to have a hard time while learning. Assuming you don't also know ES6, having to rely on tutorials that only teach React and TypeScript tgoether will significantly limit the resources you have to learn from. It is recommended you learn React with ES6 first, and then once you're comfortable with how React and ES6 fundamentally works, start using TypeScript. That way you can still learn from the vast resources and examples that use ES6, while avoiding any errors where you're confused if you're using React or TypeScript incorrectly.


## React Basics

Note that there are more ways than the ones specified here to implement components. These are suggestions.

### Components

React relies on the concept that many "components" aggregate together to make a whole application. Those components may be comprised of smaller components and so on! [Facebook's tutorial](https://facebook.github.io/react/tutorial/tutorial.html) is a great way to understand this basic principle. 

For every component, there should be a different JavaScript file. This encourages modularity and ensures things don't get messy. Your application's directory structure should look something like:
```
my-first-react-application
	components
    	introduction.js
        about.js
        projects.js
        contact.js
	index.js
    README.md
```

Once you understand the concept of containers, actions, and reducers, you'll want to create seperate directories for those too.

Your index file should have a component that has child components from the 'components' directory! 

### React and ReactDOM

After its inception, React got split into two libraries:

- React: React functionalities utilized in web and mobile apps
- React DOM: React functionalities utilized for 'gluing' React with the DOM

Why the distinction? The creators hope to use the React library for mobile development while excluding React DOM. At this point in time however, that's more of an aspiration with React Native, a framework for mobile development, being very different from React in implementation. 


### Creating an Application and Adding a Component

React first needs to know where you want to put your application on the DOM. So let's create a a specific div just for the application, under the ID, 'container'.
```
<html>
  <header>
  	<title>Hyun's Awesome Demo</title>
  </header>
  <body>
  	<h1>The new application!</h1>
    <div id='container'></div>
  </body>
</html>

```

Then let's create an index.js file that imports the necessary libraries, and sets a new component to 'container'. The 'import' statement and fat arrows are part of ES6, not React, so remember to learn ES6 before React to understand what is going on.
```
// Import the two necessary React libraries
import React from 'react';
import ReactDOM from 'react-dom';

// Create a functional component
const App = () => {return (
	<div>
    	<p>Hello there!</p>
    </div>
)}

// Tell React where to render the functional component!
ReactDOM.render(<App />, document.querySelect('#container'));

```

What if it's a more complex application that is comprised of several components? Then you'll want to import the components you made  from the components directory!

Let's say you created components/projects.js. In order to export your projects, you'll create something like:

```
import React from 'react';
// We aren't importing ReactDOM because we're rendering this component in index.js

let projects = () => <div>Lets pretend my projects are listed here</div>
export default projects;
```

Then in index.js, you'll import projects.js and then include it.

```
// Import the two necessary React libraries
import React from 'react';
import ReactDOM from 'react-dom';
import projects from './components/projects.js';

const App = () => {return (
	<div>
    	<p>Hello there!</p>
        <projects /> // Ta-da! We added a component to our application! Go modularity!
    </div>
)}

ReactDOM.render(<App />, document.querySelect('#container'));

```


### Kinds of Components
	
Functional Component: Literally a function; some input goes in, JSX comes out. Consider that these components will never change in what they initially look like.
```
const title = () => <h2>This component will never change!</h2>
```

Class-based Component: A component that has state (ie. some internal record keeping) and/or wants to communicate with other components.
```
// Define a new class, and give it all the functionality of React.Component
class FirstName extends React.Component{
	render() {
		return <input />
	}
}
let nameInstance = new FirstName;
```

If you're not sure which to use, start with a functional component, and then use a class-based component when you need the additional functionality.


### Event Handling

Class-based Component: Whenever we want a component to have some internal record keeping and/or communicate to other components.
```
	// Define a new class, and give it all the functionality of React.Component
	class FirstName extends React.Component{
		render() {
			return <input onChange={event => console.log(event.target.value)} />
		}

	}
	let nameInstance = new name; // New Instance of the class
```

### States

Essentially, state is a component's object that if changed, forces the component to re-render. This also forces the component's children to get re-rendered. State is an object that should be set in the constructor of the class-based component.

```
	// Define a new class, and give it all the functionality of React.Component
	class FirstName extends React.Component{
    	constructor(props) {
        	super(props);
            this.state = { name: '' };
        }
		render() {
			return <input onChange={event => this.setState({ name: event.target.value })} />
		}

	}
	let nameInstance = new FirstName;
```

#### Use setState when Changing the state value!

Note how when I changed the value of this.state, I used 'this.setState()'. It is critical that you use this method WHENEVER you change the state value. Why? When you use setState, you're telling React, "hey, I'm changing the value of the state! Do whatever you do need to do knowing that." If you simply assign the value of state to something without setState, React has no way of knowing the state has changed.
```
// BAD!!! Do not do this.
render() {
	return <input onChange={event => this.state = { name: event.target.value } />
}

// The proper way to change state. 
render() {
	return <input onChange={event => this.setState({ name: event.target.value })} />
}
```

### Controlled Field

A controlled field is a field that is controlled by the state. This is in direct contrast to the previous section where the state is controlled by the input field. 

```
	// Define a new class, and give it all the functionality of React.Component
	class FirstName extends React.Component{
    	constructor(props) {
        	super(props);
            this.state = { name: '' };
        }
		render() {
			return (
              <input 
              	value={this.state.term}
              />
            )
		}

	}
	let nameInstance = new FirstName;
```

### Concept: Down-wards Data Flow and Passing Props

Let's say we're creating a Broken Links Report. We have an input component that takes in the website domain you want to search for broken links, a table component that shows a subset of 100 broken links in the domain at a time, and a pagination component to show how many subsets of 100 broken links exist. 

However, which component should be the one fetching the data? Should it be the input component or the table component? Actually, no. React follows a concept of "Down-wards Data Flow", in which the parent-most component should be the one fetching and distributing data. In many cases, this may be the application component in index.js. 

If we go back to using the example we made in the section "Creating an Application and Adding a Component", we may want to pass a filter string from our parent App component to our child 'projects' component to filter the relevant projects. Note that we'll have to change App from a functional component to a class-based component because we're trying to pass state property of App to 'projects'. 

```
import React from 'react';
import ReactDOM from 'react-dom';
import projects from './components/projects.js';

class App extends React.Component {
	constructor(props){
    	super(props);
        this.state = { filter: ""};
    }
    render(){
    	<div>
          <p>Hello there!</p>
          
          <input onChange={event => this.setState({ filter: event.target.value }) />
          <projects filter = {this.state.filter} />
        </div>
    }
}

ReactDOM.render(<App />, document.querySelect('#container'));

```




### Adding CSS to JSX

When adding a CSS class to some JSX, you must refer to it as 'className'. React chose this particular keyword to not conflict with JavaScript ES6's 'class' keyword. 

```
class FirstName extends React.Component{
  render() {
    return <input className="col-xs-6 blue-form" />
  }
}
```


### Changing State Best Practice

[Immutability is important](https://facebook.github.io/react/tutorial/tutorial.html#why-immutability-is-important), and Redux
requires you avoid mutations. In fact, many packages used alongside Redux assume you never mutate the state. While adapting to
immutability, you may want to use the dev-only package, [redux-immutable-state-invariant](https://github.com/leoasis/redux-immutable-state-invariant),
to keep yourself and your teammates in check. 

I suggest you use Object.assign. Not that this is not supported by IE11, so you may need the npm package, [object-assign](https://www.npmjs.com/package/object-assign).

```
this.state = { a : 0, b: 0 }

...

var change1 = { a: 1, b: 1 };
var change2 = { b: 2 };
var change3 = { c: 3 };

var newState = Object.assign({}, JSON.parse(JSON.stringify(state)), change1, change2, change3);
this.setState(newState) // { a : 1, b : 2, c : 3 }
```

Or, using TypeScript 2.1 or higher, Object spread syntax is possible. Not as performant, but gets the job done just as well.
```
let obj1 = { a: 0, b: 0 };
var obj2 = {...obj, b: 1, c: 2}; // { a: 0, b: 1, c: 2 }
```


### Pass down Functions from Parent Components 

As you know, variables can be passed down from parent components to child components. However, functions, as first-class citizens, also can.

Take the below example in which you have a component two levels within a parent component that has a button that if clicked will change the 
state of the parent component. 

```
// Parent Component
class PickBestMovie extends React.Component {
	constructor(){
		this.state = {
			username : 'Hyun Heo',
			favMovie : null,
		}
	}
	render(){
		return(
			<div>
				<movie
				 movieName="Finding Nemo"
				 changeFavMovie={favMovie => this.setState({favMovie})} />
			</div>		
		)

	}
}

// Child Component
var movie = props => {
	return(
		<div>
			<h2>{{props.movieName}} is the Best?</h2>
			<movieSelect
			 movieName={props.movieName}
			 changeFavMovie={props.changeFavMovie} />
		</div>
	)
}

// Child's child Component 
var movieSelect = props => {
	return(
		<button onClick={props.changeFavMovie(props.movieName)} >Hell yeah, man.</button>
	)
}

```

When you click the child's child's component, a button, the state in the parent component will be set. 

NOTE: Passing callbacks like this should be done to two levels down MAX. Redux allows you to cut down 
on the number of call backs you keep passing, but this method is still important to know as it's a great
lightweight way of parent-child communication without bloating use of Redux. 


### Multiple Child Components

Going off the last section's example, we can't just have Finding Nemo be the only movie our users can select,
though we know such art is peerless. Let's use ES6's 'Map'. Know that you may need Babel, or a polyfill to get
the below example working. You could use a for loop too... but that's not in the spirit of React. 

```
// Parent Component
class PickBestMovie extends React.Component {
	constructor(){
		this.state = {
			movies : {'Finding Nemo', 'Finding Nemo 2', 'Finding Dory'}
			favMovie : null,
		}
	}
	render(){
	
		const movieItems = this.state.movies.map(movie => {
			return (
				<movie 
				 movieName={movie}
				 changeFavMovie={(favMovie) => this.setState({favMovie})}
			)
		})
	
		return (
			<div>
				<ul>
					{movieItems}
				</ul>
			</div>
		)
	}
}

// Child Component
var movie = props => {
	return(
		<li>
			<h2>{{props.movieName}} is one of the Choices!</h2>
			<button onClick={props.changeFavMovie(props.movieName)}>Pick Me!</button>
		</li>
	)
}
```

