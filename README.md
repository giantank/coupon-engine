CLI prototype for a coupon engine driven by [easy rules](https://github.com/j-easy/easy-rules)
---

### Build & Usage
```
mvn package
java -cp target/coupon-prototype-1.0-SNAPSHOT.jar de.delinero.copt.App cart.json coupons/coupon-5.json ABC
```

### CLI & Parameters
java -cp *classpath* de.delinero.copt.App *cart* *coupon* *code* *[silent]*

Parameter | Description
--- | ---
cart | JSON file defining a cart
coupon | JSON file defining a coupon
code | A coupon code
silent | Optional boolean for silencing easy rules

### JSON Input Files
#### Carts
```json
{
  "value": 100,
  "items": [
    {
      "sku": "E1000-001",
      "category": "Cheese",
      "price": 50
    },
    {
      "sku": "E1000-010",
      "category": "Cheese",
      "price": 50
    }
  ]
}
```

#### Coupons
```json
{
  "discount": 20,
  "type": "percentage",
  "rules": [
    {
      "rule": "ValidCode",
      "option": "ABC"
    },
    {
      "rule": "MinimumCartValue",
      "option": "35"
    },
    {
      "rule": "Expiration",
      "option": "2018-01-01"
    },
    {
      "rule": "Category",
      "option": "Cheese"
    },
    {
      "rule": "Exclude",
      "option": "E1000-020"
    }
  ]
}
```