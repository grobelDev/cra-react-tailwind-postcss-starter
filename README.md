## Installation Instructions

### 1. Create-React-App

`npx create-react-app PROJECT_NAME`
`cd PROJECT_NAME`

### 2. Install Dependencies

```
npm install tailwindcss postcss-cli autoprefixer --save-dev
```

### 3. Create Postcss config file

`touch postcss.config.js`
Put this code in it:

```
module.exports = {
  plugins: [
    require("tailwindcss"),
    require("autoprefixer")
  ]
};
```

### 4. Create Tailwind config file

`npx tailwind init`

### 5. Create tailwind.css file.

- NOTE: Postcss will use this tailwind.css file to generate the actual .css file used in the project. In this example, this file will be placed a bit out of the way in src/styles/tailwind.css.

`mkdir -p ./src/styles && touch ./src/styles/tailwind.css`

Put this code inside:

```
/* src/styles/tailwind.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 6. Add additional scripts to 'package.json'.

- Go to 'package.json' and locate the 'scripts' section.
  It should look like this:

```
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
  }
```

Add this code to the end so that the end result looks like this:

```
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "build:styles": "postcss src/styles/tailwind.css -o src/styles.css",
    "prebuild": "npm run build:styles",
    "prestart": "npm run build:styles"
  }
```

- NOTE: The 'src/styles.css' is what the OUTPUT css file is going to look like.

### 7. Import our the styles.css into the Index.js.

Index.js:

```
import React from 'react';
import ReactDOM from 'react-dom';
import './styles.css'
import App from './App';
import * as serviceWorker from './serviceWorker';

ReactDOM.render(<App />, document.getElementById('root'));
serviceWorker.unregister();
```

### 8. Done! Here is some example App.js code to see a tailwind styled button.

App.js:

```
import React from "react";

function App() {
  return (
    <div className="text-4xl font-bold text-center text-blue-500">
      Hello World!
    </div>
  );
}

export default App;
```

---

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `yarn start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `yarn test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `yarn build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `yarn eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `yarn build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
