---
sidebar_position: 1
---

# The Response Object

The **res**ponse object is the primary way to send data back to the client. It has a number of methods that allow you to set the response status, headers, and body.

## res.send()

The easiest way to deliver a response is to use the **res.send()** method. This method takes a single argument, which is the response body.
The response body can be a `string`, a `ReadableStream`, or a `Response`.

Here is an example of sending a `string`:

```javascript
router.get('/', (req, res) => {
  res.send('Hello World!');
});
```

Here is an example of sending a `ReadableStream`:

```javascript
router.get("/api", async (req, res) => {
  let originRequest = await fetch(
    "https://example.com", { backend: "my-origin" }
  );

  res.send(res.body);
});
```

Here is an example of sending a `Response`:

```javascript
router.get("/origin", async (req, res) => {
  res.send(await fetch(
    "https://example.com", { backend: "my-origin" }
  ));
});
```
