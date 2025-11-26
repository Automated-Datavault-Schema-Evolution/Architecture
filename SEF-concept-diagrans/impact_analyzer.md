# impact analyzer  diagram

````mermaid
flowchart LR
  IN[Change Notification]
  PS[Prior Schema]
  subgraph IA[Impact Analyzer]
    DF[Schema Diff]
    LG[Lineage Lookup]
    SC[Scope Resolution]
  end
  OUT[Impact Set]

  IN --> DF
  PS --> DF
  DF --> LG --> SC --> OUT
  META[Metadata Repo] --> DF
  LINE[Lineage Store] --> LG
  OUT --> PE[Policy Engine]
  OUT --> PL[Migration Planner]

````
