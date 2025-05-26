**Entity Relationships of a Payment Order**

_Column 3 = SFTI compatibility: YES = compatible, NO = not supported_

```mermaid
erDiagram

    PaymentOrder {
        string paymentOrderId YES
        date creationDate NO
        enum status NO
        object assetManager NO
        Transaction[] transactions NO
    }
    AssetManager {
        string amId NO
        string amName YES
        string amLocation YES
        string amAddress NO
    }
    Transaction {
        string transactionId YES
        string externalRef YES
        enum type YES
        boolean performanceRelevant YES
        enum statementOption YES
        boolean nameClientInStatement YES
        object dates NO
        Creditor creditor YES
        Debitor debitor YES
        Amount amount YES
    }
    Dates {
        date valueDate YES
        date executionDate YES
    }
    Creditor {
        string creditorIban YES
        string creditorAccountRef NO
        string bookingTextCreditor YES
        string reasonCreditor YES
    }
    Debitor {
        string debtorName YES
        string debtorIban YES
        string debtorAccountRef YES
        string bookingTextDebitor YES
        string reasonDebitor YES
    }
    Amount {
        string currency YES
        float amount YES
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

