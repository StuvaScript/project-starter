# Project Starter

This is a file on how to start your projects using Webpack, linting, prettier, and hooks.<br>

## Github

Create a new repository in Github.<br>
Copy the new repo's SSH key.<br>
Open terminal, change directory to where you keep your project files.<br>
Type `git clone` and paste the key. <br>
Change to the new repo's directory.<br>
Type `code .` to open the project in VS Code.<br>
Hit 'ctrl + backtick ( \` )' to open the terminal in VS Code.<br>
<br>

### TL;DR
Copy pasta this in the terminal:

```
npm init -y
npm install webpack webpack-cli --save-dev
npm install --save-dev style-loader css-loader
npx webpack
npm install eslint --save-dev
./node_modules/.bin/eslint --init
npm install --save-dev --save-exact prettier
npm install --save-dev eslint-config-prettier
npm install --save-dev husky lint-staged
npx husky install
npm pkg set scripts.prepare="husky install"
npx husky add .husky/pre-commit "npx lint-staged"
mkdir src dist src/fonts src/images
echo "node_modules" >> .gitignore
echo "node_modules
main.js" >> .eslintignore 
echo "node_modules
main.js" >> .prettierignore 
echo "import './normalize.css';
import './style.css';" >> src/index.js
echo "{
  \"singleQuote\": true
}" >> .prettierrc.json
touch dist/index.html webpack.config.js src/style.css src/normalize.css

```

Choose the following:
- To check syntax, find problems, and enforce code style
- CommonJS
- None of these
- No
- Browser
- Use a popular style guide
- Airbnb
- JSON
- Yes
- npm

<br>

Inside 'dist/index.html', copy pasta and save this:

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="main.js" defer></script>
    <title>Gimme a title</title>
  </head>
  <body></body>
</html>
```

Inside 'webpack.config.js', copy pasta and save this:

```
const path = require('path');

module.exports = {
  mode: 'development',
  entry: './src/index.js',
  devtool: 'source-map',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
      },
      {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource',
      },
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource',
      },
    ],
  },
};
````

Go here https://github.com/StuvaScript/normalize.css/blob/master/normalize.css and in the upper right click the double square icon that says 'copy raw contents' on hover, paste this inside the 'src/normalize.css' file, then save. 

Go inside the file '.eslintrc.json' and add the following code to 'rules' then save:

```
"rules" : {
    "no-console": "off"
}
```

## Webpack

https://www.theodinproject.com/lessons/node-path-javascript-webpack<br>
https://www.theodinproject.com/lessons/node-path-javascript-restaurant-page<br>
https://webpack.js.org/guides/getting-started/<br>
<br>

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
<br>
https://webpack.js.org/guides/development/<br>
https://webpack.js.org/configuration/devtool/<br>
<br>
Go inside your 'webpack.config.js' file and update two parts of the code to have `mode: "development",` and `devtool: "eval",` like this and save:

```
const path = require("path");

module.exports = {
  mode: "development", // <-- Add this line
  entry: "./src/index.js",
  devtool: "source-map", // <-- Also add this line
  output: {
  
 // more code ...
  ```
  
To run everything, in the terminal type `npx webpack`.<br>
The 'source-map' devtool creates the 'dist/main.js.map' file. If I change to 'production' when project is finished should I delete this file?<br>

## Linting and Prettier

https://www.theodinproject.com/lessons/node-path-javascript-linting<br>
https://www.digitalocean.com/community/tutorials/linting-and-formatting-with-eslint-in-vs-code<br>

### ES Lint

In the terminal type `npm install eslint --save-dev`.<br>
Then type `./node_modules/.bin/eslint --init` which will be followed by prompts. Choose the following:
- To check syntax, find problems, and enforce code style
- CommonJS
- None of these
- No
- Browser
- Use a popular style guide
- Airbnb
- JSON
- Yes
- npm

<br>
If you haven't already, go into 'Extensions' in VS Code and download the 'ES Lint' extension.<br>
To format on save, go the VS Code settings and click 'Command Palette', then click 'Preferences: Open Workspace Settings (JSON)'.<br>
Paste the following code inside and save:

```
{
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.validate": ["javascript"]
}
```

Go inside the file '.eslintrc.json' and add the following code to 'rules' then save:

```
"rules" : {
    "no-console": "off"
}
```

### Prettier

https://prettier.io/docs/en/install.html<br>
<br>
To install Prettier, in the terminal type `npm install --save-dev --save-exact prettier`.<br>
Then type `echo {}> .prettierrc.json`.<br>
Inside the newly created '.prettierrc.json' file paste the following and save:

```
{
    "singleQuote": true
}
```

In the terminal type `touch .eslintignore .prettierignore`.<br>
Inside both newly created 'ignore' files, paste the following code and save:

```
node_modules
main.js
```

After creating the 'ignore' files, its safe to reformat all the files by pasting this code in the terminal `npx prettier --write .`<br>

### Getting ES Lint and Prettier to play nice

https://github.com/prettier/eslint-config-prettier#installation<br>
<br>
To allow ES Lint and Prettier to play nicely together, type this in the terminal:<br>
`npm install --save-dev eslint-config-prettier`<br>
Go inside the '.eslintrc.json' file and add 'prettier' to the 'extends' array. Make sure it goes last so it overrides the other configs. Don't forget to add square brackets, a comma, and save. Code will look like this:

```
{
  "env": {
    "browser": true,
    "commonjs": true,
    "es2021": true
  },
  "extends": ["airbnb-base", "prettier"], <-- Add 'prettier' here
  "overrides": [],
  
  // other code
```

### Git Hooks (Husky and Lint-Staged)

https://prettier.io/docs/en/install.html#git-hooks<br>
<br>
The following git hooks will allow your code to format on commit. Meaning even if you don't save a file (which at this point should automatically format on save), the files getting uploaded to Github will be formatted.
Install the required Husky and Lint-Staged stuff by copying and pasting this whole code block into the terminal:

```
npm install --save-dev husky lint-staged
npx husky install
npm pkg set scripts.prepare="husky install"
npx husky add .husky/pre-commit "npx lint-staged"
```

Go inside the 'package.json' file and add the 'lint-staged' code (I just added it before 'devDependencies') and save:

```
// Add the code thats between the dashes
// ----------------------------------

"lint-staged": {
    "**/*": "prettier --write --ignore-unknown"
  },
  
// ----------------------------------

"devDependencies": {
  "css-loader": "^6.7.3",
  "eslint": "^8.39.0",
    
 // more code
```

### Setting it all into motion

Type `npx webpack --watch` in the terminal for automatic changes on save. To get out of 'watch mode' type 'Ctrl + C'<br>
Go ahead and `git add .` then `git commit .` then `git push origin main`<br>

### Displaying from a subtree

https://gist.github.com/cobyism/4730490<br>
<br>
In order for Github to display your pages, you need to let Github know about your subtree. Type in the following:<br>
`git add dist && git commit -m "Initial dist subtree commit"`<br>
Then use the subtree push by typing the following:<br>
`git subtree push --prefix dist origin gh-pages`<br>
Every time you do a normal 'add commit push' you will need to do the subtree push as well to stay up to date.<br>
Remember when you're done with your project to go inside the 'webpack.config.js' file and change the mode to 'production' and change the devtool to a more production friendly source map.<br>
<br>
You're done!! 😄
