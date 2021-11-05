---
sidebar_position: 2
---

# Controlling Flow

If you wish to edit the flow of a request with middleware you can edit the req object, for example:

```javascript
router.use((req, res) => {
  if (req.url.pathname == "/") {
    req.url.pathname = "/home";
  }
});
```

This will **not** redirect the user, it instead changes how routes will be selected. In this case, `router.get("/")` would not match but `router.get("/home")` would.

## Stopping the request

If you need to stop requests for example blocking unauthenticated requests, you can call `res.end()` which is like `req.send()` but will cause the request to end without triggering any routes.

```javascript
router.use("/account/", (req, res) => {
  if(!("userId" in req.cookies)){
    res.end("You must be logged in to view this page");
  }
});
```

You can also stop requests by redirecting them to a different page:

```javascript
router.use("/account/", (req, res) => {
  if(!("userId" in req.cookies)){
    res.redirect("/login");
  }
});
```
