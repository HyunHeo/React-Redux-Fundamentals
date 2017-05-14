# React-Redux Fundamentals
<a href='https://facebook.github.io/react/'><img src="https://react-etc.net/files/2016-07/logo-578x270.png" alt="React Logo" height="50"></a> 
<a href='https://jsx.github.io/'><img src="https://camo.githubusercontent.com/2b0b2c776d6cba46731b722570bdef902dd213d2/687474703a2f2f692e696d6775722e636f6d2f58636637692e706e67" alt="JSX's proposed logo" height="50"></a> 
<a href='https://jsx.github.io/'><img src="https://frontendmasters.com/assets/es6-logo.png" alt="JSX's proposed logo" height="50"></a> 

Notes on the fundamentals of React and  handing state in Redux. Created in my free time for the benefit of my team at TD and me to more easily adopt React.


## Introduction

### What is React?

"React is a declarative, efficient, and flexible JavaScript library for building user interfaces." It is the View in the MVC model.


#### How does it compare to Angular?

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

### What is JS6?

EMCAScript 6, a particular newer specification of JavaScript that changed a lot of things for the better, is often referred to as JS6. If you're used to 'regular old' JavaScript, you're probably thinking of ES5 or an older specification. ES6 is also mandatory while using React because React relies on classes and other new features. Many people who share sample code in React will use ES6 liberally -- for good reason!

If you're unfamiliar with JS6, it's highly recommended you at least learn about classes, fat arrows, let, and const before you start with React. [Babel has a great summary of what ES6 offers.](https://babeljs.io/learn-es2015/)

If you're worried about browser compatibility, don't sweat it. That's why [Babel](https://babeljs.io/) works so closely with React, ensuring your code, whether it be ES6, ES7, or JSX,  gets transpiled to ye old ES5. Babel is an essential part of your build process when using React.

You may use TypeScript instead, which also has many key features of ES6, but you're going to have a hard time while learning. Assuming you don't also know ES6, having to rely on tutorials that only teach React and TypeScript tgoether will significantly limit the resources you have to learn from. It is recommended you learn React with ES6 first, and then once you're comfortable with how React and ES6 fundamentally works, start using TypeScript. That way you can still learn from the vast resources and examples that use ES6, while avoiding any errors where you're confused if you're using React or TypeScript incorrectly.
