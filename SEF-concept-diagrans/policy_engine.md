# policy engine diagram

````mermaid
flowchart LR
  CH[Change Atoms]
  IMP[Impact Set]
  CTX[Context]
  subgraph PE[Policy Engine]
    EV[Rules Evaluation]
    DEC[Decisions]
    OBL[Obligations]
  end
  APR[Approval]
  OUT[Policy Outcome]

  CH --> EV
  IMP --> EV
  CTX --> EV
  EV --> DEC --> OUT
  EV --> OBL --> OUT
  DEC --> APR --> OUT


````
