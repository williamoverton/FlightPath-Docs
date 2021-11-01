---
sidebar_position: 1
---

# Headers

## Get Headers

You can retrieve the headers send by the client by accessing the `req.headers` object.
Note: **All header names are lowercase**

```javascript
router.get("/", (req, res) => {
    res.json({
        userAgent: req.headers["user-agent"],
        host: req.headers["host"]
    })
})
```

## Set Headers

Setting headers is done by calling `res.setHeader(key, value)`.

```javascript
router.get("/", (req, res) => {
    res.setHeader("Content-Type", "text/html");
    res.send("<html><body><h1>This is HTML!</h1></body></html>")
})
```
