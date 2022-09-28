# ReactJS Sandbox

## Create new project from scratch

1. Initialize new npm project

```shell
npm init
```

2. Create file `public/index.html`; with following content:

```html
<!-- sourced from https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html -->
<!DOCTYPE html>
<html>

<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <title>React Starter</title>
</head>

<body>
  <div id="root"></div>
  <noscript>
    You need to enable JavaScript to run this app.
  </noscript>
  <script src="../dist/bundle.js"></script>
</body>

</html>
```
3. Setup `Babel` by adding dependencies:

```shell
 npm install --save-dev @babel/core@7.19.3 @babel/cli@7.19.3 @babel/preset-env@7.19.3 @babel/preset-react@7.18.6
```

4. Create file `.babelrc`; with following content:

```json
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

5. Setup `Webpack` dependencies:

```shell
 npm install --save-dev webpack@5.74.0 webpack-cli@4.10.0 webpack-dev-server@4.11.1 style-loader@3.3.1 css-loader@6.7.1 babel-loader@8.2.5
```

6. Create `webpack.config.js`

```javascript
const path = require("path");
const webpack = require("webpack");

module.exports = {
  entry: "./src/index.js",
  mode: "development",
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /(node_modules|bower_components)/,
        loader: "babel-loader",
        options: { presets: ["@babel/env"] }
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  resolve: { extensions: ["*", ".js", ".jsx"] },
  output: {
    path: path.resolve(__dirname, "dist/"),
    publicPath: "/dist/",
    filename: "bundle.js"
  },
  devServer: {
    static: {
      directory: path.join(__dirname, 'public'),
    },
    port: 3000
  },
  plugins: [new webpack.HotModuleReplacementPlugin()]
};
```

7. Install latest React dependencies
```shell
npm i react react-dom
```

## Usefull links
- [npm packages browser](https://www.npmjs.com/package/package)
- [webpack devServer options](https://webpack.js.org/configuration/dev-server/#devserver)