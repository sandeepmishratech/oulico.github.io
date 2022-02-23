---
layout: post
title: "How to use Babel for Node.JS"
date: 2022-02-23 17:36:50 +0300
categories: Notes-JavaScript
tags: Notes JavaScript babel npm node.js
---

# How to use Babel for Node.JS



## 1. Install Babel

### Installation

https://babeljs.io/setup#installation

```shell
npm i --save-dev @babel/core
```

### Create `babel.config.json`

```shell
npm i @babel/preset --save-dev		
```

Define it in the `babel.config.json`, like this:

```json
{
  "preset": ["@babel/preset-env"]
}
```

## 2. Use babel-node to write latest JScode

### Installation

```shell
npm i --save-dev @babel/node    
```



## 3.Use nodemon to execute  automatically

### Installation

```shell
npm i nodemon --save-dev
```

Make `script` in `package.json`

```js
 "scripts":{
    "dev": "nodemon --exec babel-node src/app.js"
 }
```



Now you can simply execute node by typing this command in terminal:

```shell
npm run dev
```

