---
sidebar_position: 1
---

# What Are Middleware?

Middleware allows you to run code on a request before any routes are run. This is useful for things like authentication, controlling headers, or other things that need to happen before your routes are run. 

The below example shows how to use middleware to add a header to all requests:

```javascript
router.use((req, res) => {
  res.setHeader("x-powered-by", "FlightPath");
});
```

If you only want middleware to run on specific routes, you can pass a path to the middleware:

```javascript
router.use("/api/*", (req, res) => {
  console.log("Got a request to the api!");
});
```
