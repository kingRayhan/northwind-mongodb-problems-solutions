# Northwind Problems Solutions

1. Select CategoryName and Description from the Categories table sorted by CategoryName.

```js
db.categories.find(null, { CategoryName: 1, Description: 1  }).sort({ CategoryName: 1 })
```
