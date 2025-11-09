# Level 3  diagram

````mermaid
flowchart LR
    UPSTREAM["Operational Systems\n(source applications)"]
    FW["File-Watching Ingest Service"]
    EVT["Schema Change Notifications"]

    subgraph SEF["Schema Evolution Framework (SEF)"]
        INT["Interpret and Plan"]
        EXEC["Apply and Verify"]
    end

    LAKE["Data Lake"]
    VAULT["Data Vault 2.0"]
    ANALYTICS["Analytics and Data Products"]
    UPSTREAM --> FW
    FW --> EVT --> SEF
    EVT --> INT
    INT --> EXEC
    EXEC --> LAKE
    EXEC --> VAULT
    LAKE --> ANALYTICS
    VAULT --> ANALYTICS
````
