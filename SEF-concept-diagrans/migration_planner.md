# processing state  diagram

````mermaid
flowchart LR
  IN[Policy Outcome + Change Atoms]
  subgraph PL[Migration Planner]
    G[Build Dependency Graph]
    S[Topological Sort]
    C[Insert Checkpoints]
    K[Assign Idempotency Keys]
  end
  PLAN[Ordered Plan]

  IN --> G --> S --> C --> K --> PLAN
  PLAN --> EX[Executor]
````
