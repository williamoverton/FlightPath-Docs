---
sidebar_position: 1
---

# Simple Routing

Flight Path provides the `Router` object which is where all configuration for your routing lives. Create a new router like this:

```javascript
import { Router } from "flight-path";

const router = new Router();
```

## Creating a Route

Then add a route by calling `router.METHOD(PATTERN, HANDLER)`. For example, adding a route for `GET` requests to `/hello-world` would look like this:

```javascript
router.get("/hello-world", (req, res) => {
  res.send("Hello world!");
})
```

Now if a request is made to `https://app.example/hello-world` our handler will run and return "Hello world!"

### But what is a handler?

A handler is the function Flight Path will call to get a response to send back to the client. It is passed two arguments, the **req**uest and the **res**ponse.

```javascript
router.get("/", (req, res) => {
  res.send("<h1>This is the response!</h1>");
})
```

## Listening for requests

Once you have added all your routes, you **must** call `router.listen()` in order for the router to bind to incoming requests.

## Hello World Example

```javascript
import { Router } from "flight-path";

const router = new Router();

router.get("/", async (req, res) => {
  return res.send("Welcome to Flight Path!");
});

router.get("/my-page", async (req, res) => {
  return res.send("This is my page!");
});

router.post("/my-page", async (req, res) => {
  return res.send("You made a POST request to my page!");
});

router.listen();
```
