# Sales order erd


```mermaid
erDiagram
    SalesOrder {
        guid id PK
        string sourceApp
        salesstatus status
        deliverystatus deliverystatus
        datetime deliverydate
        deliverymethod deliverymethod
        paymentstatus paymentstatus
        table table
        customer customer
        address deliveryaddress
    }
    SalesOrder |o--o| Customer : has
    SalesOrder |o--o| Table has
    SalesOrder ||--o{ SalesOrderDetail : has
    SalesOrderDetail {
        guid id PK
        salesorderdetailtype type
        salesitem salesitem
        decimal orderquantity
        decimal deliveryquantity
    }
    SalesOrder }|--o| SalesOrderPayment : has
    SalesOrderPayment {
        guid id PK 
        paymentmethod paymentmethod
        decimal amount
    }
```
