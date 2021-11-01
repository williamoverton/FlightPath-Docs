---
sidebar_position: 1
---

# Into to FlightPath

Let's discover **Flight Path in less than 5 minutes**.

## Getting Started

Firslty follow the docs on [developer.fastly.com](https://developer.fastly.com) for getting started with Javascript in C@E:

Getting started with C@E: [https://developer.fastly.com/learning/compute/](https://developer.fastly.com/learning/compute/)

Creating your first JS app: [https://developer.fastly.com/learning/compute/javascript/](https://developer.fastly.com/learning/compute/javascript/)

## Installing Flight Path

Install Flight Path from the NPM repository:

NPM:

```shell
npm i flight-path
```

Yarn:

```shell
yarn add flight-path
```

## Setting up routing

Replace the contents of your `index.js` file with the following:

```javascript
import { Router } from "flight-path";

const router = new Router();

router.get("/", async (req, res) => {
  return res.send("Hello World!");
});

router.listen();
```

## Try it out

Start you app locally:

```shell
fastly compute serve
```

This will start your service on `http://localhost:7676`.

### Live reloading for development

You can use a tool called `nodemon` to automatically reload your app when you make a change.

```shell
npx nodemon --exec "npm run build && fastly compute serve --skip-build"
```
