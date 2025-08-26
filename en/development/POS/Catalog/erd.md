# Sales item
The sales items are the most important data from the cash register. In this first version, we are assuming an MVP cash register in which we only record minimal basic data from the cash register.

## ERD Diagram



```mermaid
erDiagram
    SalesItem {
        guid id PK 
        string name FK "Unique name"
        string sku  FK "Unique sku code"      
        SalesTurnovergroup turnovergroup
        decimal baseprice
        boolean disabled
    }
    SalesItem ||--o{ SalesTurnovergroup : has
    SalesTurnovergroup {
        guid id PK 
        string name
    }
    SalesItem }o--|{ SalesItemCategory : has
    SalesItemCategory {
        guid id PK 
        string name
        string seqgno
        boolean disabled
    }

```
