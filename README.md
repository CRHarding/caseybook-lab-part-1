# CaseyBook Lab Part 1

## Initialize React Application

To initialize a bare bones React application we're going to use our good friend create-react-app.

```bash
npx create-react-app caseybook
```

This will take care of downloading all initial dependencies. When this command finishes running
(you should see something along the lines of `Happy Hacking`) go ahead and:

```bash
cd caseybook
code .
```

This will move you into the newly created caseybook folder and then open up that folder in VSCode.
Alternatively, if you use Atom you can run `atom .`, or if you use Sublime you can run `subl .`
The dot just says to open up all files and folders in the text editor of choice.

Take a minute to glance around the various files and folders. The `index.js` file is the glue connecting
your React application to your `/public/index.html` file. On line 11 in `index.js` you'll notice 
our good friend, `document.getElementById`, this is grabbing the element with an id of `root`
(if you look in your `/public/index.html` file you'll see a `div` element with an id of `root`!)
and using that as the entry point for our React code. Remembering that React eventually resolves
down to `HTML`, `CSS`, and `JS`, this file is used to take that generated code and put it into
the DOM. Neato, right?

In between the `<React.StrictMode>` tags you'll also notice an `<App />` element. On line 4 you'll
also see an import. Following the breadcrumbs, we can navigate to the `App.js` file in the same `src`
folder as our `index.js` file and....drum roll...we can see our first, very own, bonified React
component!

Before we get ahead of ourselves, let's go back to the terminal and type in `ls`. What you're looking
for is your `package.json` file. The following command will look for the `package.json` and use that
to know what to do!

If you see a `package.json` file you're all good to go! If not, try running `cd caseybook` if you
forgot to do that or missed it above.

Once you see it, it's time to get hacking, still in your terminal, run this command:

```bash
npm run start
```

Aaaaaaaaaaaaand you're ready to go! React will take care of an initial compilation step and will start
a hot reloading server for you. It's not perfect, but if you make changes to a file and save,
React will stop the server, re-compile, and restart the server for you.

Now that we've covered the setup, let's get going with part 1! Before we dive in, let's take a minute to talk about class (or stateful) components and function (or stateless) components. 

> As an aside: Hooks are very much in use, but I believe that when first learning React it's important to learn React without hooks first, and once you grasp the concepts to introduce hooks and talk through the problems that hooks solve. We are going to start this application by introducing class components, state, lifecycle methods, all of the good stuff, and then in a future lab refactor it to use hooks. That way you'll have experience with both and no matter what you use at work you'll have enough knowledge to recognize the patterns!

Before we introduce the concept of class components, let's spend a minute talking about what state is. State is not a React concept, rather it is a concept in programming that applies to, well, everything. State is data, specifically state is the data that controls what the program is doing. If you have a modal, state could be set as `open` or `closed`, if you have a friends list state could be `friend` or `not friend`, etc, etc.

React manages state by using a JavaScript object that contains key value pairs which describe the current status of our application. Before we can use state, however, we have to bring in a class component. Let's go back to our `App.js` file and refactor it to be able to use state!

First things first, let's bring in some React dependencies which allow us to utilize state (and, later on, lifecycle methods!).

At the top of your file, let's clean up our imports and include the React dependencies we'll need:

```javascript
import React, { Component } from 'react';
import './App.css';
```

We're bringing in `Component` to give us access to state. We have access, but we're not using it yet! Let's begin our refactor by changing our `App` function into a class, including a constructor, and bringing in a `render` method (and deleting the boilerplate JSX). Your `App.js` should now look like this:

```javascript
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  constructor() {
    super();

    this.state = {}
  }

  render() {
    return (
      <div className="App">
      
      </div>
    );
  }
}

export default App;
```

We're extending Component (and calling `super()`) to loop in Component's functionality. We'll dive into `render()` a little later when we talk through a component's lifecycle.

As a quick sanity check let's update our return to include some text and verify that our application is running correctly! In between the `<div className="App">` let's add in an `<h1>` element:

```javascript
render() {
  return (
    <div className="App">
      <h1>Hello, world!</h1>
    </div>
  )
}
```

After saving the file, react will automatically reload your browser tab and you should see your heading! Exciting, right?

Let's spend a minute talking about `JSX`. It looks like `HTML`, but in reality `JSX` is `JavaScript`! What that means is that we can insert data, run virtually any JavaScript code that we want (including ternaries, map / filter / reduce, etc, etc!), all within HTML like syntax! Instead of having separate JS and HTML files, we can combine the two which really helps us manage the various pieces. We're now moving towards the data (or state) of our application managing the UI of our application. Onwards and upwards!

Let's now really get the juices flowing and introduce state. To start with, let's initialize a `profile` object in state and render it in our JSX!

In your constructor, after the `this.state =` let's add in our data!

```javascript
constructor() {
  super();
  
  this.state = {
    profile: {
      username: "CRHarding",
      image: "http://images6.fanpop.com/image/photos/32800000/Thor-thor-32844898-1024-768.jpg",
      about: "Lorem ipsum dolor sit amet..."
    }
  }
}
```

Now that we have our profile data set, let's render out a profile page!

In your render method, let's add in some JSX:

```javascript
render() {
  return (
    <div className="App">
      <h1>Profile page!</h1>
      <p>{this.state.profile.username}</p>
      <img src={this.state.profile.image} alt="user" />
      <p>{this.state.profile.about}</p>
    </div>
  );
}
```

Those strange curly brackets are what tell JSX to interpret the code as JavaScript rather than HTML. It feels weird at first but eventually it will be second nature (especially if you're coming from another templating system like handlebars or ejs).

That image is a bit large, eh? Let's add in a minimal amount of CSS to make it a bit smaller, in yuour App.css file add in this:

```css
img {
  width: 250px;
}
```

There we go, much better! We now have a bare bones profile page set up, with our profile data in state dictating the structure of our UI. How neat! So far, so good, but, eventually our `App.js` file will get a bit...bloated, so let's start Part 2 by separating our UI out into a separate component, which is going to introduce the concept of presentational components, or components whose sole job is to take in data and display the data. Let's keep this party moving!
