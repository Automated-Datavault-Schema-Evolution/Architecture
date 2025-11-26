# executor diagram

````mermaid
flowchart LR
  PLAN[Ordered Plan]
  subgraph EX[Executor]
    N[Fetch Next Operation]
    H[Call Handler]
    P[Persist Checkpoint]
    R[Retry or Compensate]
  end
  LH[Lake Handler]
  VH[Vault Handler]
  OUT[Applied Operations]

  PLAN --> N --> H
  H --> LH
  H --> VH
  LH --> P
  VH --> P
  P --> N
  P --> OUT
````
