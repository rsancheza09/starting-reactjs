# starting-reactjs
This is how to set a React JS enviroment

## Steps:
* Install **[nodejs]** and **[npm]** in your machine.
* Initialize npm new project:
```sh
$ npm init
```
* Install react dependencies:
```sh
$ npm install react react-dom --save
```
* Install [babel] and [webpack]:
```sh
$ npm install babel webpack webpack-dev-server --save
```
* Install babel dependencies:
```sh
$ npm install babel-loader babel-core babel-preset-es2015 babel-preset-react --save
```
* Now we are going to create our initial files:
```sh
$ touch index.html App.js main.js webpack-config.js
```
* Then we are going to edit our **webpack-config.js**:
```
module.exports = {
  entry: './main.js',
  output: {
    path: './',
    filename: 'index.js'
  },
  devServer: {
    inline: true,
    port: 3333
  },
  module: {
    loaders: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        loader: 'babel',
        query: {
          presets: ['es2015', 'react']
        }
      }
    ]
  }
}
```
* After that we are going to setup our HTML file, index.html:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Setup</title>
</head>
<body>
  <div id="app"></div>
  <script src="index.js"></script>
</body>
</html>
```
* Now we are goig to edit *App.js*:
```
import React from 'react'
class App extends React.Component {
  render() {
    return <div>Hello buddy!!!</div>
  }
}
export default App
```
* Then we are going to edit *main.js*:
```
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

ReactDOM.render(<App />, document.getElementById('app'))
```
* Finally we just have to make a simple change in our *package.json*, specifically in **scripts**:
```
{
  "name": "es6-react-setup",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "./node_modules/.bin/webpack-dev-server --config ./webpack.config.js --progress --colors --inline --hot"
  }
}
```
* Run **npm start** and we are ready!!!

[nodejs]: https://nodejs.org/en/
[npm]: https://www.npmjs.com/
[babel]: https://babeljs.io/
[webpack]: http://webpack.github.io/docs/
