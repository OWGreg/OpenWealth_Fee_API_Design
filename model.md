**Entity Relationships of a Payment Order**

```mermaid
erDiagram

    PaymentOrder {
        string paymentOrderId
        date creationDate
        enum status
        object assetManager
        Transaction[] transactions
    }

    AssetManager {
        string amId
        string amName
        string amLocation
        string amAddress
    }

    Transaction {
        string transactionId
        string externalRef
        enum type
        boolean performanceRelevant
        enum statementOption
        boolean nameClientInStatement
        object dates
        Creditor creditor
        Debitor debitor
        Amount amount
    }

    Dates {
        date valueDate
        date executionDate
    }

    Creditor {
        string creditorIban
        string creditorAccountRef
        string bookingTextCreditor
        string reasonCreditor
    }

    Debitor {
        string debtorName
        string debtorIban
        string debtorAccountRef
        string bookingTextDebitor
        string reasonDebitor
    }

    Amount {
        string currency
        float amount
    }

    PaymentOrder ||--|| AssetManager : hasOne
    PaymentOrder ||--o{ Transaction : hasMany
    Transaction ||--|| Dates : hasOne
    Transaction ||--|| Creditor : hasOne
    Transaction ||--|| Debitor : hasOne
    Transaction ||--|| Amount : hasOne
```

---

### 🛑 Out-of-Scope Fields

| Field                  | Reason for Exclusion                                                                 |
|------------------------|--------------------------------------------------------------------------------------|
| `creditorIbanCurrency` | The target account's currency is determined by the IBAN itself; value is redundant.  |
