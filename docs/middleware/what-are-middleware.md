---
sidebar_position: 1
---

# What Are Middleware?

Below is an example middleware:

```javascript
router.use((req, res) => {
  res.setHeader("x-powered-by", "FlightPath");
});
```

All middleware run on every request, can read the incoming request and also write to the response. They do not stop the appropriate route from being called. The above example adds the `x-powered-by` header to every response.
