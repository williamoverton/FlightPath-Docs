---
sidebar_position: 4
---

# Request Body

The body of a request can be accessed in multiple ways

## As Text

```javascript
router.post("/submit", async (req, res) => {
    let body = await req.text();

    res.send(`You posted: "${body}"`)
})
```

## As JSON

```javascript
router.post("/submit", async (req, res) => {
    // Parse body as json
    let body = await req.json();

    // Check if the body contained the key "item"
    if("item" in body){
        res.send(`item: ${body.item}`)
    }else{
        res.send("You must include item in your body!")
    }
})
```
