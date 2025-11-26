# handler diagram

````mermaid
flowchart LR
  EX[Executor]
  subgraph HANDLERS[Handlers]
    LH[Lake Handler]
    DVH[Data Vault Handler]
  end
  subgraph LAKE[Data Lake]
    LC[Logical Catalog]
    STO[Storage Objects]
  end
  subgraph VAULT[Data Vault 2.0]
    HUB[Hubs]
    LINK[Links]
    SAT[Satellites]
  end

  EX --> LH
  EX --> DVH
  LH --> LC
  LH --> STO
  DVH --> HUB
  DVH --> LINK
  DVH --> SAT
````
