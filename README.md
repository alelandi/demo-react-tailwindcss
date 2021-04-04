# A simple React App integrated with TailwindCSS

## Description

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

React App that shows a sample text "Hello World" using some TW classes.

## Steps I have followed

### Create a new React App project

````cmd
npm init react-app my-project
cd my-project
````

### Setting up Tailwind CSS

````cmd
npm install -D tailwindcss@npm:@tailwindcss/postcss7-compat @tailwindcss/postcss7-compat postcss@^7 autoprefixer@^9
````

This because Create React App doesn't support PostCSS 8.

### Install and configure CRACO

#### Installing CRACO

Since CRA doesn't let us override the PostCSS configuration natively, we also need to install CRACO to be able to configure Tailwind.

````cmd
npm install @craco/craco
````

#### Configuring CRACO

Now update our "scripts" section in the `package.json` file:

````json
{
    // ...
    "scripts": {
     "start": "react-scripts start",
     "build": "react-scripts build",
     "test": "react-scripts test",
     "start": "craco start",
     "build": "craco build",
     "test": "craco test",
     "eject": "react-scripts eject"
    },
    // ...
  }
````

Next, create a `craco.config.js` at the root of the project and add the tailwindcss and autoprefixer as PostCSS plugins:

````json
module.exports = {
  style: {
    postcss: {
      plugins: [
        require('tailwindcss'),
        require('autoprefixer'),
      ],
    },
  },
}
````

### Create a Tailwind config file

To do this, type the following line of code in your prompt:

````cmd
npx tailwindcss init
````

At the end, this will create a default `tailwind.config.js` file at the root of the project, like this:

````json
module.exports = {
  purge: [],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
````

### Include Tailwind in our project

Into the `./src/index.css` file, replacing the original file contents using the `@tailwind` directives:

````postcss
@tailwind base;
@tailwind components;
@tailwind utilities;
````

### Conclusion

And that's the end.
Now when we run `npm run start`, the App starts and Tailwind CSS will be ready to use in our project.

Learn more in the [TailwindCSS official documentation](https://tailwindcss.com/docs/guides/create-react-app)
