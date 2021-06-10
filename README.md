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
