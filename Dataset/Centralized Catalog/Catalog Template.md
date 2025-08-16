### Example: Centralized Data Catalog

**1. Dataset Information**

* Dataset Name: `Customer_Transactions`
* Business Owner: Eg., `Sales Department`
* Technical Owner: `Data Engineering Team`
* Description: E.g., `Records of all customer transactions including sales, returns, and payments.`

**2. Metadata**

* Source System: 
* Storage Location: 
* Database: 
* File Format: 
* Refresh Frequency: 

**3. Schema (Columns)**

| Column Name       | Data Type | Description                          | Example Value       | Sensitive (Y/N) |
| ----------------- | --------- | ------------------------------------ | ------------------- | --------------- |
| `TransactionID`   | INT       | Unique transaction identifier        | 100234              | N               |
| `CustomerID`      | INT       | Unique customer identifier           | 56789               | Y               |
| `TransactionDate` | DATETIME  | Date and time of transaction         | 2025-08-15 10:35:22 | N               |
| `Amount`          | DECIMAL   | Total transaction amount             | 150.75              | N               |
| `PaymentMethod`   | STRING    | Payment type used (card, cash, etc.) | Credit Card         | N               |

**4. Data Quality Rules**

* `TransactionID` must be unique.
* `Amount` cannot be negative.
* `TransactionDate` must be within the last 10 years.

**5. Access and Security**

* Access Level: Restricted to Sales Analysts and Finance Team
* Data Sensitivity: Contains PII (CustomerID)
* Compliance: GDPR, PCI-DSS

**6. Lineage **

* Source: 
* Downstream Usage: Power BI dashboards, Finance reports

