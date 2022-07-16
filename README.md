# Northwind Problems Solutions

1. Select CategoryName and Description from the Categories table sorted by CategoryName.

```js
db.categories.find(null, { CategoryName: 1, Description: 1  }).sort({ CategoryName: 1 })
```

2. Select ContactName, CompanyName, ContactTitle, and Phone from the Customers table sorted by Phone.

```js
db.customers.find(null, {
    ContactName: 1,
    CompanyName: 1,
    ContactTitle: 1,
    Phone: 1
}).sort({
    Phone: 1
})
```
