---
layout: post
title: Export and Import
date: 2022-03-09 08:00:50 +0900
categories: Node.Js
tags: Notes JavaScript Node.Js
---



# Export and Import

## 2 ways of export



When we use `app.use()`, we are bringing functions from else where, another `.js` file.

We call it **importing**.

And if you want to import something from somewhere, you should export first. 

And to **export**, there are two ways.

`export default` and normal `export`.



## export default

First of all, let's see how to export default:

```js
const globalRouter = express.Router();
export default globalRouter;
```



## export 

And the normal export is like this:

```js
export const globalRouter = express.Router()
```





## Difference

Default export has only one function to export.

So, when you export more than one function from another `file`, you cannot use Default export. 

But as there's always only one function exported, name of the function doesn't matter. You can type anything when you import this. 

But conventionally, we don't change the name though.



## How to import

There are 2 ways to import.



Import default 

```js
import globalRouter from "./routers/globalRouter"
```

Import more than 1

```js
import { upload, download } from "./router/videoRouter"
```



