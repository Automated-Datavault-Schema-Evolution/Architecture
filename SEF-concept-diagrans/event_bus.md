# metadata and lineage

````mermaid
flowchart LR
    FW[Ingest Service]
    TIN[Topic schema.events]
    SEF[Schema Evolution Framework Core]
    TOUT[Topic schema.evolved]
    ORC[Orchestrators]
    CONS[Consumers]
    FW --> TIN --> SEF --> TOUT --> ORC --> CONS

    subgraph Semantics
        K[Keyed by dataset]
        A[At-least-once delivery]
        P[Partitions for scale]
        R[Retention for replay]
    end
````
