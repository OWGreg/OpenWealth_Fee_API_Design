erDiagram

    %% Anpassungen an Customer
    Customer {
        string id
        string status
        string name
        string referenceCurrency
        string segment
        string[] personList
        string purposeOfRelationship
    }

    %% Neue Box: Wealth
    Wealth {
        object fundFlows
        object sourceOfWealthInformation
        object totalWealth
        object totalIncome
    }

    %% Neue Box: Risk
    Risk {
        enum politicalStatus
        boolean fatcaStatus
        boolean fatcaDomicile
        boolean fatcaBirthplace
        boolean fatcaGreenCard
        boolean fatcaSubstantialPresenceTest
        boolean fatcaOtherReasons
        object[] corporateInsiderList
        object[] majorShareholderList
    }

    %% Verbindungen
    Person ||--o| Wealth : hasOne
    Person ||--o| Risk : hasOne

    %% Entitäten, die nun zu Wealth gehören
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

    SourceOfWealth {
        string id
        string type
        object amount
        object[] countriesOfOrigin
        object additionalProperties "type specific properties"
    }

    TotalWealth {
        object amountTotalNetAssets
        object referenceYear
        object[] assetAllocation
    }

    TotalIncome {
        object amountYearlyIncome
        object referenceYear
        object[] sourceOfIncomeList
    }

    %% Entitäten, die nun zu Risk gehören
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

    %% Beziehungen von Wealth und Risk zu Subobjekten
    Wealth ||--o| FundFlows : hasOne
    Wealth ||--o| SourceOfWealth : hasOne
    Wealth ||--o| TotalWealth : hasOne
    Wealth ||--o| TotalIncome : hasOne

    Risk ||--o{ CorporateInsider : hasMultiple
    Risk ||--o{ MajorShareholder : hasMultiple
