# metadata and lineage

````mermaid
flowchart LR
    APPLY[Apply Operation]
    OK[Success]
    TRANS[Transient Failure]
    PERM[Permanent Failure]
    RETRY[Retry with Backoff]
    COMP[Compensate and Replan]
    APPLY --> OK
    APPLY --> TRANS --> RETRY --> APPLY
    APPLY --> PERM --> COMP --> APPLY
````
