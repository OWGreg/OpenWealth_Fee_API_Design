**Entity Relationships of a Payment Order (color-coded)**

_🟢 Green = SFTI-compatible field_  
_🔴 Red = Not part of current SFTI CA Payment API_

```mermaid
classDiagram

class PaymentOrder {
    +string paymentOrderId
    +date creationDate
    +enum status
    +object assetManager
    +Transaction[] transactions
}

class AssetManager {
    +string amId
    +string amName
    +string amLocation
    +string amAddress
}

class Transaction {
    +string transactionId
    +string externalRef
    +enum type
    +boolean performanceRelevant
    +enum statementOption
    +boolean nameClientInStatement
    +object dates
    +Creditor creditor
    +Debitor debitor
    +Amount amount
}

class Dates {
    +date valueDate
    +date executionDate
}

class Creditor {
    +string creditorIban
    +string creditorAccountRef
    +string bookingTextCreditor
    +string reasonCreditor
}

class Debitor {
    +string debtorName
    +string debtorIban
    +string debtorAccountRef
    +string bookingTextDebitor
    +string reasonDebitor
}

class Amount {
    +string currency
    +float amount
}

PaymentOrder --> AssetManager : hasOne
PaymentOrder --> Transaction : hasMany
Transaction --> Dates : hasOne
Transaction --> Creditor : hasOne
Transaction --> Debitor : hasOne
Transaction --> Amount : hasOne

class paymentOrderId,amName,amLocation,transactionId,externalRef,type,performanceRelevant,statementOption,nameClientInStatement,valueDate,executionDate,creditorIban,bookingTextCreditor,reasonCreditor,debtorName,debtorIban,debtorAccountRef,bookingTextDebitor,reasonDebitor,currency,amount SFTI

class amId,amAddress,creationDate,status,assetManager,transactions,creditorAccountRef nonSFTI

classDef SFTI fill:#cfc,stroke:#0c0,color:#000;
classDef nonSFTI fill:#fcc,stroke:#900,color:#000;
```

---

### 🛑 Out-of-Scope Fields

| Field                  | Reason for Exclusion                                                                 |
|------------------------|--------------------------------------------------------------------------------------|
| `creditorIbanCurrency` | The target account's currency is determined by the IBAN itself; value is redundant.  |
