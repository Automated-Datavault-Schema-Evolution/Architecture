# Level 1  diagram

````mermaid
flowchart LR
    SOURCES["Changing Data Sources (evolving file schemas)"]
    SEF["Schema Evolution Framework (SEF)"]
    LAKE["Data Lake"]
    VAULT["Data Vault 2.0"]
    ANALYTICS["Analytics and Data Products"]
    SOURCES --> SEF
    SEF --> LAKE
    SEF --> VAULT
    LAKE --> ANALYTICS
    VAULT --> ANALYTICS

````
