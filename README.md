This is a file on how to start your projects using Webpack, linting, prettier, and hooks. All info can be found here:
https://www.theodinproject.com/lessons/node-path-javascript-webpack
https://www.theodinproject.com/lessons/node-path-javascript-restaurant-page
https://webpack.js.org/guides/getting-started/
https://gist.github.com/cobyism/4730490


TL;DR

Instructions:

Create a new repository in Github.<br>
Copy the new repo's SSH key.<br>
Open terminal, change directory to where you keep your project files.<br>
Type `git clone` and paste the key. <br>
Change to the new repo's directory.<br>
Type `code .` to open the project in VS Code.<br>
Hit 'ctrl + backtick ( \` )' to open the terminal in VS Code.<br>
Initialize node package manager by typing `npm init -y`. This will create a package.json file in your project.<br>
Type `npm install webpack webpack-cli --save-dev` to install webpack to the node_modules directory of your project.<br>
Create a '.gitignore' file by typing `touch .gitignore`.<br>
Inside '.gitignore' type `node_modules` and save. That way this huge file doesn't save on Github.<br>
Create 'src' and 'dist' folders by typing `mkdir src dist`.<br>
Create two necessary files in those folders by typing `touch src/index.js dist/index.html`.<br>
Inside the 'index.html' file, go ahead and create your boilerplate and type `<script src="main.js" defer></script>` in the head then save.<br>
Create the webpack config file back in the terminal below by typing `touch webpack.config.js`.<br>
Inside the webpack config file, copy pasta this whole code then save:

```
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

For asset management, in your terminal type `npm install --save-dev style-loader css-loader`.<br>
Inside your 'webpack.config.js' file, update the code to look like this and save:

```
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  output: {
    filename: "main.js",
    path: path.resolve(__dirname, "dist"),
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ["style-loader", "css-loader"],
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: "asset/resource",
      },
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: "asset/resource",
      },
    ],
  },
};
 ```
 
 In the terminal type `touch src/style.css src/normalize.css`.<br>
 Head into my Github repositories online, find my 'normalize.css' repo, hit the 'copy raw contents' button in the upper right, paste them inside the 'normalize.css' file you just made, then save. (I'll have to find a better way to do this in the future)<br>
Head inside your 'src/index.js' file and type `import './style.css';` at the top of the page then save.<br>
In the terminal type `mkdir src/fonts src/images`<br>
Go inside your 'webpack.config.js' file and update two parts of the code to have `mode: "development",` and `devtool: "eval",` like this and save:

```
const path = require("path");

module.exports = {
  mode: "development", // <-- Add this line
  entry: "./src/index.js",
  devtool: "eval", // <-- Also add this line
  output: {
  
 // more code ...
  ```
  



Need to write the shit about pushing a subfolder so you can see your project live on Github.<br>

Type `npx webpack --watch` in the terminal for automatic changes on save.
