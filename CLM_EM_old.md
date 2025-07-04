```mermaid
erDiagram
    CUSTOMER {
        string customerId PK
        string name
    }
    PERSON {
        string personId PK
        string givenName
        string lastName
    }
    DOCUMENT {
        string documentId PK
        string type
        string mimeType
    }
    ADDRESS {
        string addressId PK
        string streetName
        string townName
    }
    CONTACT {
        string contactId PK
        string medium
        string content
    }
    KYC {
        string purposeOfRelationship
        boolean soleBeneficialOwner
    }
    SOURCEOFWEALTH {
        string sourceType
        int amount
    }
    TOTALWEALTH {
        int amountTotalNetAssets
        string currency
    }
    TOTALINCOME {
        int amountYearlyIncome
        string currency
    }
    EMPLOYMENT {
        string employmentStatus
    }
    POLITICALSTATUS {
        boolean pepStatus
        boolean sanctions
    }
    FATCA {
        boolean status
    }
    EXTERNALASSETMANAGER {
        boolean eamCustomer
    }

    CUSTOMER ||--o{ PERSON2CUSTOMERRELATION : has
    CUSTOMER ||--o{ DOCUMENT : has
    PERSON2CUSTOMERRELATION }o--|| PERSON : relates_to
    PERSON ||--o{ ADDRESS : has
    PERSON ||--o{ CONTACT : has
    PERSON ||--o{ KYC : has
    KYC ||--o{ SOURCEOFWEALTH : includes
    KYC ||--|| TOTALWEALTH : describes
    KYC ||--|| TOTALINCOME : describes
    KYC ||--|| EMPLOYMENT : describes
    KYC ||--|| POLITICALSTATUS : includes
    KYC ||--|| FATCA : includes
    KYC ||--|| EXTERNALASSETMANAGER : includes
