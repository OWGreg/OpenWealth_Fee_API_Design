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
