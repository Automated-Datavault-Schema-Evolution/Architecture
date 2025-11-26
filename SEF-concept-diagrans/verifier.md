# verifier diagram

````mermaid
flowchart LR
  INT[Intended State]
  OBS[Observed State]
  subgraph VR[Verifier]
    ST[Structural Checks]
    SM[Semantic Probes]
    LN[Lineage Recheck]
  end
  OK[Publish]
  NOK[Replan]

  INT --> ST
  OBS --> ST --> SM --> LN
  LN -->|pass| OK
  LN -->|fail| NOK
````
