---
sidebar_position: 3
---

# Query String

Query parameters are not part of routing, they can be accessed in the `req.query` object.

## Get query / search paramater value

```javascript
// return page id for paths like /page?id=42
router.get("/page", (req, res) => {
    if("id" in req.query){
        res.send(`You are on page: ${req.query.id}`)
    }else{
        res.send("You didnt supply a id! Add one like this /page?id=123")
    }
})
```
