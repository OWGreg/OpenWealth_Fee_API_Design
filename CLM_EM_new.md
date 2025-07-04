```mermaid
erDiagram

    Customer {
        string id
        string status
        string name
        string referenceCurrency
        string segment
        string[] personList
        string purposeOfRelationship
        object externalAssetManager
    }

    Person {
        string id
        enum type "natural, legal or joint"
        string externalReference
    }

    CustomerPersonRelation {
        string id
        enum type
        string cardinality
        string personId
        string relatedCustomerId
        string purposeOfRelationship
        boolean soleBeneficialOwner
    }

    PersonPersonRelation {
        string id
        enum type
        string personId
        string relatedPersonId
    }

    Address {
        string id
        enum type
        string personId
        string address
    }

    Contact {
        string id
        enum medium
        enum prio
        string content
    }

    Document {
        string id
        string customerId
        enum group
        enum type
        enum status
        date issueDate
        string content
    }

    Education {
        string highestDiploma
        integer graduationYear
        string institute
        string studyProgramme
        object educationInformation
    }

    Employment {
        string companyName
        object companyDomicile
        object[] companyCountriesOfBusinessList
        string companyDetail
        integer companyNumberOfEmployees
        number companyAnnualTurnover
        string industry
        object roleOrPosition
        profession profession
        string domicile
        number shareholdingInPercent
        object period
        integer yearOfRetirement
        integer sharedholderSinceYear
        string mandate
        string additionalInformation
        object employmentInformation
    }

    Wealth {
        string sourceOfWealth_type
        object sourceOfWealth_amount
        object[] sourceOfWealth_countriesOfOrigin
        object sourceOfWealth_additionalProperties

        object totalWealth_amountTotalNetAssets
        object totalWealth_referenceYear
        object[] totalWealth_assetAllocation

        object totalIncome_amountYearlyIncome
        object totalIncome_referenceYear
        object[] totalIncome_sourceOfIncomeList
    }

    FundFlows {
        object amountExpectedInflows
        object amountPlannedTotalAssets
        object amountExpectedTurnover
        integer numberOfInflows
        integer numberOfOutflows
        object[] recurringCounterpartyList
        object[] initialAmountList
        object[] expectedFundFlowList
    }

    CorporateInsider {
        string corporateInsiderAssociation
        string relation
        object position
        string companyName
        string isin
    }

    MajorShareholder {
        string majorShareholderAssociation
        string relation
        string companyName
        string isin
    }

    Risk {
        enum politicalStatus
        boolean fatcaStatus
        boolean fatcaDomicile
        boolean fatcaBirthplace
        boolean fatcaGreenCard
        boolean fatcaSubstantialPresenceTest
        boolean fatcaOtherReasons
        object countryOfDomicile
        object[] taxDomicileList
    }

    %% Beziehungen

    Customer ||--|{ CustomerPersonRelation : hasMultiple
    Customer ||--o{ Document : hasMultiple
    CustomerPersonRelation }o--|| Person : hasMultiple
    PersonPersonRelation }o--|| Person : hasMultiple
    PersonPersonRelation }o--|| Person : isRelatedPerson

    Person ||--o{ Address : hasMultiple
    Person ||--o{ Contact : hasMultiple
    Person ||--o| Employment : hasOne
    Person ||--o| Education : hasOne
    Person ||--o| Wealth : hasOne
    Person ||--o| Risk : hasOne
    Person ||--o{ FundFlows : hasMultiple
    
    Risk ||--o{ CorporateInsider : hasMultiple
    Risk ||--o{ MajorShareholder : hasMultiple
