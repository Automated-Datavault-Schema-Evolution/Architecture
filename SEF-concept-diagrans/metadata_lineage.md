# metadata and lineage

````mermaid
flowchart LR
    SEF[Schema Evolution Framework Core]
    subgraph META[Metadata Repository]
        VERS[Schema Versions]
        PLANS[Plans and Checkpoints]
        PUB[Publications]
    end
    subgraph LIN[Lineage Store]
        DEP[Dependencies Graph]
    end

    SEF --> VERS
    SEF --> PLANS
    SEF --> PUB
    SEF --> DEP
    META --> SEF
    LIN --> SEF
````
