**Entity Relationships of a Fee Payment Order**

```mermaid
erDiagram

    PaymentOrder {
        string paymentOrderId
        date creationDate
        enum status "PENDING, SENT, EXECUTED, FAILED"
        object assetManager
        Transaction[] transactions
    }

    AssetManager {
        string amId "LEI, UID or internal ID"
        string amName
        string amLocation
    }

    Transaction {
        string transactionId
        object details
        Creditor creditor
        Debtor debtor
        Amount amount
    }

    Details {
        string externalRef
        enum type "e.g. Management Fee"
        string bookingTextCreditor
        string bookingTextDebitor
        string reasonCreditor
        string reasonDebtor
        date valueDate
        date executionDate
        boolean performanceRelevant
        enum statementOption "Standard, yes, no"
        boolean nameClientInStatement
    }

    Creditor {
        string creditorName
        string creditorLocation
    }

    Debtor {
        string debtorName
        string debtorIban
        string debtorAccountRef
    }

    Amount {
        string currency "ISO 4217"
        float amount
    }

    PaymentOrder ||--|| AssetManager : belongsTo
    PaymentOrder ||--o{ Transaction : includes
    Transaction ||--|| Details : has
    Transaction ||--|| Creditor : paysTo
    Transaction ||--|| Debtor : paidBy
    Transaction ||--|| Amount : involves
