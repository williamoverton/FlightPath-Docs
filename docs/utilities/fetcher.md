---
sidebar_position: 1
---

# Fetcher

Fetcher is a high level abstraction for fetching data from origins in parallel. If you need fine grained control over the process, use the `fetch()` function directly.

```javascript
import { Router, Fetcher } from "flight-path";

// Bind to any get request
router.get("*", async (req, res) => {

  // Create a Fetcher instance
  // This will fetch data from multiple origins in parallel
  // and return a promise that resolves to an object
  // with the data from each origin
  const fetcher = new Fetcher({
    header: {
      url: "https://header.example.com/make-header",
      backend: "header_service",
      headers: {
        "x-api-key": "12345"
      }
    },
    page: {
      url: "https://content.example.com/make-store-page",
      backend: "page_service"
    }
  })

  // Wait for all fetches to complete
  let data = await fetcher.fetch();

  // Render the page with the data
  res.send(`
    <html>
      <head>
        <title>Content Stitching</title>
        <link rel="stylesheet" href="/assets/style.css" />
      </head>
      <body>
        ${data.header.data}
        <hr />
        ${data.page.data}
      </body>
    </html>
  `)
});
```