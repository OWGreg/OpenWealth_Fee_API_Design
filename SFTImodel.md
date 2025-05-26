**SFTI Payment API – Reference Entity Model for Comparison**

_This model serves as a simplified representation of the SFTI CA Payment API data structure. It is created solely for comparison purposes to assess whether the planned OpenWealth fee specification could be mapped to the SFTI Payment interface._

```mermaid
erDiagram

    BulkRequest {
        string bulkOrderId
        Transaction[] transactionList
    }

    Transaction {
        string externalReferenceNumber
        enum transactionType
        string bookingTextCreditor
        string bookingTextDebitor
        string transactionReasonCreditor
        string transactionReasonDebitor
        date valueDate
        date executionDate
        boolean performanceRelevance
        enum statementOption
        boolean namingClient
        string currency
        float currencyAmount
        Creditor creditor
        Debitor debitor
    }

    Creditor {
        string institutionName
        string institutionLocation
        string creditorIban
    }

    Debitor {
        string debitorName
        string debitorIban
        string debitorAccount
    }

    BulkResponse {
        string bulkOrderId
        HTMLCode htmlCode
    }

    StatusResponse {
        string bulkOrderId
        TransactionStatus[] transactionList
    }

    TransactionStatus {
        string transactionId
        string externalReferenceNumber
        string status
        date valueDate
        date executionDate
        string errorDetails
    }

    BulkRequest ||--o{ Transaction : contains
    Transaction ||--|| Creditor : paysTo
    Transaction ||--|| Debitor : paidBy
    StatusResponse ||--o{ TransactionStatus : tracks
