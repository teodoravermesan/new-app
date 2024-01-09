# new-app

- create a new git repo: test
- check Add a README file
- Add .gitignore (Node template)
- clone it on the computer
- create a new branch: git checkout -b test
- open folder in VS
- create index.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

</body>
</html>
```

- create style.css

```
h1 {
  color: red;
}
```

- create index.js

```

import "./style.css";
console.log("start app");

```

- init project to use npm

```

npm init -y

```

- config project to use webpack

```
  npm install --save-dev webpack webpack-cli
  npm i -D webpack-dev-server
  npm i -D html-webpack-plugin
  npm i -D html-loader style-loader css-loader

```

- start project with

```

npm start

```

- change webpack config roots

```

const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = (env) => {
const isProduction = !!env.WEBPACK_BUILD;
return {
mode: isProduction ? "production" : "development",
entry: ["./index.js"],
devtool: isProduction ? false : "inline-source-map",
plugins: [
new HtmlWebpackPlugin({
template: "./index.html",
}),
],
module: {
rules: [
{
test: /\.html$/i,
         loader: "html-loader",
       },
       {
         test: /\.css$/i,
use: ["style-loader", "css-loader"],
},
],
},
output: {
filename: "index.js",
path: path.resolve(\_\_dirname, "docs"),
publicPath: "",
},
};
};

```

- packaje.json

```

{
"name": "new-app",
"version": "1.0.0",
"description": "",
"main": "index.js",
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1",
"clean": "rimraf docs",
"clear": "npm run clean && rimraf node_modules",
"prebuild": "npm run clean",
"build": "webpack --mode production",
"start": "webpack serve --open",
"demo": "set PORT=8080 && serve docs"
},
"keywords": [],
"author": "Teodora Vermesan",
"license": "ISC",
"devDependencies": {
"css-loader": "^6.8.1",
"html-loader": "^4.2.0",
"html-webpack-plugin": "^5.6.0",
"style-loader": "^3.3.3",
"webpack": "^5.89.0",
"webpack-cli": "^5.1.4",
"webpack-dev-server": "^4.15.1"
}
}

```

- git add .
- git commit -m "commit message"
- git push

```

```

GitHub Pages

- change in Settings > Pages > Build & deployment to deploy from a branch: test /root

```

```
