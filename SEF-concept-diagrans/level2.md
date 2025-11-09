# Level 2  diagram

````mermaid
flowchart LR
    SOURCES["Changing Data Sources (evolving file schemas)"]

    subgraph SEF["Schema Evolution Framework (SEF)"]
        INT["Interpret and Plan\n(schema change detection, classification, policy)"]
        EXEC["Apply and Verify\n(evolution execution, checks, versioning)"]
    end

    LAKE["Data Lake"]
    VAULT["Data Vault 2.0"]
    ANALYTICS["Analytics and Data Products"]
    SOURCES --> SEF
    SOURCES --> INT
    INT --> EXEC
    EXEC --> LAKE
    EXEC --> VAULT
    LAKE --> ANALYTICS
    VAULT --> ANALYTICS
````
