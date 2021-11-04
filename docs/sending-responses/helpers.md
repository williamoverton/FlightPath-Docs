---
sidebar_position: 2
---

# Response Helpers

The res object has a number of helper methods to make working with the response easier. The following are available:

## res.json()

If you have an object that you want to return as JSON, you can use the `res.json()` method. It will serialize the object and set the content type to `application/json`.

```javascript
router.get('/', function(req, res) {
  res.json({
    message: 'Hello World'
  });
});
```

## res.redirect()

When you want to redirect the user to another page, you can use the `res.redirect()` method. It will set the status code to `301` and set the `Location` header to the URL you want to redirect to.

```javascript
router.get('/', function(req, res) {
  res.redirect('/about');
});
```

```javascript
router.get("/redirect", async (req, res) => {
  res.redirect("https://fastly.com");
});
```