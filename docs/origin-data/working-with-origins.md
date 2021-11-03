---
sidebar_position: 1
---

# Working With Origins

Accessing data from origins is done via the standard fetch API available in C@E, [Try these docs.](https://developer.fastly.com/learning/compute/javascript/#communicating-with-backend-servers-and-the-fastly-cache)

## Being efficient

The most efficient way of proxying data from your origin to the client is to make sure you do not read the body in your code. Below is an example where we make a `fetch()` request to our origin and then pass the entire Response object to `res.send()` doing this allows us to avoid reading the content of the response which saves us processing time and memory usage.

```javascript
router.get("/origin", async (req, res) => {
  res.send(await fetch(
    "https://example.com", { backend: "my-origin" }
  ));
});
```

## Reading a Response

If you need to read the body of a response you can do so like this:

```javascript
router.get("/api", async (req, res) => {
  let originRequest = await fetch(
    "https://example.com", { backend: "my-origin" }
  );

  let body = await originRequest.text();

  res.send(`Body had a length of ${body.length}`);
});
```
