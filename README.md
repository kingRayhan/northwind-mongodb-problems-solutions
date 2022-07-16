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

3. Create a report showing employees' first and last names and hire dates sorted from newest to oldest employee

```js
db.employees.find(null, {
    FirstName: 1,
    LastName: 1,
    HireDate: 1
}).sort({
    HireDate: 1
})
```

4. Create a report showing Northwind's orders sorted by Freight from most expensive to cheapest. Show OrderID, OrderDate, ShippedDate, CustomerID, and Freight.

```js
db.orders.find(null, {
    OrderID: 1,
    OrderDate: 1,
    ShippedDate: 1,
    CustomerID: 1,
    Freight: 1
}).sort({
    Freight: -1
})
```
![image](https://user-images.githubusercontent.com/7611746/179337560-2bfe467e-c3d2-4d1a-9b3a-4bb9110f3ff4.png)
