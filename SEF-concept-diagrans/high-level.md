# High level diagram

````mermaid
flowchart LR
%% Ultra high-level view of the Schema Evolution Framework (SEF)
    SOURCES["Changing Data Sources<br/>(evolving file schemas)"]
    SEF["Schema Evolution Framework"]
    PLATFORM["Data Platform Core"]
    ANALYTICS["Analytics and Data Products"]
    SOURCES --> SEF --> PLATFORM --> ANALYTICS
````
