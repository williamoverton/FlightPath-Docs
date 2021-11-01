---
sidebar_position: 2
---

# Advanced Routing

Flight Path offers some more advanced routing options which as explained below.

## Wildcards

You can use wildcards in order to match multiple URLs with one route.

```javascript
router.get("/assets/*", (req, res) => {
    let path = req.url.pathname;
    res.send(`You are at this asset path: ${path}`)
})
```

The above route will match any GET request to `/assets/[ANYTHING]` such as `/assets/logo.png` or `/assets/file.csv`.

## Parameters

Parameters can be specified in route patterns which are then made available in the `req.params` object.

```javascript
router.get("/profile/:userId", (req, res) => {
    let userId = req.params.userId;
    res.send(`This is the profile for user ${userId}`);
})
```

## Wildcard HTTP Method

If you want to handle all HTTP methods in one route you can use `router.route(METHOD, PATTERN, HANDLER)` to create your route.

```javascript
router.route("*", "/api/profile", (req, res) => {
    let method = req.method;
    res.send(`You made a ${method} request`);
})
```
