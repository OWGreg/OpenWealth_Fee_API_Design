**Entity Relationships of a Payment Order**

_Third column "SFTI" = field is part of SFTI CA Payment API_

```mermaid
classDiagram

class PaymentOrder {
    +string paymentOrderId SFTI
    +date creationDate
    +enum status
    +object assetManager
    +Transaction[] transactions
}

class AssetManager {
    +string amId
    +string amName SFTI
    +string amLocation SFTI
    +string amAddress
}

class Transaction {
    +string transactionId SFTI
    +string externalRef SFTI
    +enum type SFTI
    +boolean performanceRelevant SFTI
    +enum statementOption SFTI
    +boolean nameClientInStatement SFTI
    +object dates
    +Creditor creditor SFTI
    +Debitor debitor SFTI
    +Amount amount SFTI
}

class Dates {
    +date valueDate SFTI
    +date executionDate SFTI
}

class Creditor {
    +string creditorIban SFTI
    +string creditorAccountRef
    +string bookingTextCreditor SFTI
    +string reasonCreditor SFTI
}

class Debitor {
    +string debtorName SFTI
    +string debtorIban SFTI
    +string debtorAccountRef SFTI
    +string bookingTextDebitor SFTI
    +string reasonDebitor SFTI
}

class Amount {
    +string currency SFTI
    +float amount SFTI
}

PaymentOrder --> AssetManager : hasOne
PaymentOrder --> Transaction : hasMany
Transaction --> Dates : hasOne
Transaction --> Creditor : hasOne
Transaction --> Debitor : hasOne
Transaction --> Amount : hasOne
```

---

### 🛑 Out-of-Scope Fields

| Field                  | Reason for Exclusion                                                                 |
|------------------------|--------------------------------------------------------------------------------------|
| `creditorIbanCurrency` | The target account's currency is determined by the IBAN itself; value is redundant.  |
