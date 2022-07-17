# Northwind Problems Solutions

## Questions
1. Select CategoryName and Description from the Categories table sorted by CategoryName.
2. Select ContactName, CompanyName, ContactTitle, and Phone from the Customers table sorted by Phone.
3. Create a report showing employees' first and last names and hire dates sorted from newest to oldest employee.
4. Create a report showing Northwind's orders sorted by Freight from most expensive to cheapest. Show OrderID, OrderDate, ShippedDate, CustomerID, and Freight.
5. Select CompanyName, Fax, Phone, HomePage and Country from the Suppliers table sorted by Country in descending order and then by CompanyName in ascending order.
6. Create a report showing all the company names and contact names of Northwind's customers in Buenos Aires.
7. Create a report showing the product name, unit price and quantity per unit of all products that are out of stock.
8. Create a report showing the order date, shipped date, customer id, and freight of all orders placed on May 19, 1997.
9. Create a report showing the first name, last name, and country of all employees not in the United States.
10. Create a report that shows the employee id, order id, customer id, required date, and shipped date of all orders that were shipped later than they were required.
11. Create a report that shows the city, company name, and contact name of all customers who are in cities that begin with "A" or "B."
12. Create a report that shows all orders that have a freight cost of more than $500.00.
13. Create a report that shows the product name, units in stock, units on order, and reorder level of all products that are up for reorder
14. Create a report that shows the company name, contact name and fax number of all customers that have a fax number.
15. Create a report that shows the first and last name of all employees who do not report to anybody
16. Create a report that shows the company name, contact name and fax number of all customers that have a fax number. Sort by company name.
17. Create a report that shows the city, company name, and contact name of all customers who are in cities that begin with "A" or "B." Sort by contact name in descending order
18. Create a report that shows the first and last names and birth date of all employees born in the 1950s.
19. Create a report that shows the product name and supplier id for all products supplied by Exotic Liquids, Grandma Kelly's Homestead, and Tokyo Traders. Hint: you will need to first do a separate SELECT on the Suppliers table to find the supplier ids of these three companies.
20. Create a report that shows the shipping postal code, order id, and order date for all orders with a ship postal code beginning with "02389".
21. Create a report that shows the contact name and title and the company name for all customers whose contact title does not contain the word "Sales".
22. Create a report that shows the first and last names and cities of employees from cities other than Seattle in the state of Washington.
23. Create a report that shows the company name, contact title, city and country of all customers in Mexico or in any city in Spain except Madrid.
24. Write a SELECT statement that outputs the following.

![image](https://user-images.githubusercontent.com/7611746/179338477-be0611e7-ae65-4fe1-b908-eeec08146077.png)


25. Create a report that shows the units in stock, unit price, the total price value of all units in stock, the total price value of all units in stock rounded down, and the total price value of all units in stock rounded up. Sort by the total price value descending.
26. SQL SERVER AND MYSQL USERS ONLY: In an earlier demo, you saw a report that returned the age of each employee when hired. That report was not entirely accurate as it didn't account for the month and day the employee was born. Fix that report, showing both the original (inaccurate) hire age and the actual hire age. The result will look like this.

![image](https://user-images.githubusercontent.com/7611746/179338494-a51dd093-5fc1-447f-a821-b03e8fe1f184.png)



27. Create a report that shows the first and last names and birth month (as a string) for each employee born in the current month.
28. Create a report that shows the contact title in all lowercase letters of each customer contact.
29. The above SELECT statement will return the following results

![image](https://user-images.githubusercontent.com/7611746/179338512-be2ced53-5289-48ea-86af-df3d2c75d540.png)



30. Create a report that shows all products by name that are in the Seafood category.
31. Create a report that shows all companies by name that sell products in CategoryID 8.
32. Create a report that shows all companies by name that sell products in the Seafood category.
33. Create a report that shows the order ids and the associated employee names for orders that shipped after the required date. It should return the following. There should be 37 rows returned.

![image](https://user-images.githubusercontent.com/7611746/179338518-0acf2de1-360e-4e51-9061-2209d43f3bd8.png)



34. Create a report that shows the total quantity of products (from the Order_Details table) ordered. Only show records for products for which the quantity ordered is fewer than 200. The report should return the following 5 rows.

![image](https://user-images.githubusercontent.com/7611746/179338521-3e3d4f62-0fdb-45be-93cf-d5a139913d86.png)



35. Create a report that shows the total number of orders by Customer since December 31, 1996. The report should only return rows for which the NumOrders is greater than 15. The report should return the following 5 rows.

![image](https://user-images.githubusercontent.com/7611746/179338526-c97a5cc6-d221-4965-aafe-facf56191afe.png)



36. Create a report that shows the company name, order id, and total price of all products of which Northwind has sold more than $10,000 worth. There is no need for a GROUP BY clause in this report.


![image](https://user-images.githubusercontent.com/7611746/179338531-f0cc1426-1c75-4a63-8ae4-ec236e767319.png)





























## Solutions


#### 1. Select CategoryName and Description from the Categories table sorted by CategoryName.

```js
db.categories.find(null, { CategoryName: 1, Description: 1  }).sort({ CategoryName: 1 })
```

#### 2. Select ContactName, CompanyName, ContactTitle, and Phone from the Customers table sorted by Phone.

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

#### 3. Create a report showing employees' first and last names and hire dates sorted from newest to oldest employee

```js
db.employees.find(null, {
    FirstName: 1,
    LastName: 1,
    HireDate: 1
}).sort({
    HireDate: 1
})
```

#### 4. Create a report showing Northwind's orders sorted by Freight from most expensive to cheapest. Show OrderID, OrderDate, ShippedDate, CustomerID, and Freight.

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

#### 6. Create a report showing all the company names and contact names of Northwind's customers in Buenos Aires.

```js
db.customers.find({
    City: {
        $eq: "Buenos Aires"
    }
}, {
    CompanyName: 1,
    ContactName: 1
})
```
![image](https://user-images.githubusercontent.com/7611746/179337845-6c1eaa2a-103c-45a6-90a4-c65908fef8e5.png)


#### 7. Create a report showing the product name, unit price and quantity per unit of all products that are out of stock

```js
db.products.find({
    UnitsInStock: {
        $eq: '0'
    }
}, {
    ProductName: 1,
    UnitPrice: 1,
    QuantityPerUnit: 1
})
```

![image](https://user-images.githubusercontent.com/7611746/179338000-24cfb973-3c61-4910-8162-b9dc64970681.png)


#### 8. Create a report showing the order date, shipped date, customer id, and freight of all orders placed on May 19, 1997

```js
db.orders.aggregate([
  {
    '$match': {
      '$or': [
        {
          'OrderDate': {
            '$exists': true
          }
        }, {
          'OrderDate': {
            '$ne': null
          }
        }
      ]
    }
  }, {
    '$project': {
      'OrderID': 1, 
      'OrderDate': {
        '$toDate': '$OrderDate'
      }, 
      'ShippedDate': {
        '$toDate': '$ShippedDate'
      }
    }
  }, {
    '$project': {
      'OrderID': 1, 
      'OrderDate': 1, 
      'ShippedDate': 1, 
      'order_year': {
        '$year': '$OrderDate'
      }, 
      'order_day': {
        '$dayOfMonth': '$OrderDate'
      }, 
      'order_month': {
        '$month': '$OrderDate'
      }
    }
  }, {
    '$limit': 5
  }, {
    '$match': {
      '$and': [
        {
          'order_year': 1996
        }, {
          'order_day': 14
        }, {
          'order_month': 4
        }
      ]
    }
  }, {
    '$project': {
      'order_year': 0, 
      'order_day': 0, 
      'order_month': 0
    }
  }
])
```

### 8. Create a report showing the product name, unit price and quantity per unit of all products that are out of stock

```js
db.products.aggregate([{
 $project: {
  ProductName: 1,
  UnitPrice: 1,
  QuantityPerUnit: 1,
  UnitsInStock: {
   $toInt: '$UnitsInStock'
  }
 }
}, {
 $match: {
  UnitsInStock: 0
 }
}])
```
