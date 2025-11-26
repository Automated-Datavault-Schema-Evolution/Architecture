# change director diagram

````mermaid
flowchart LR
  EB[Event Bus]
  subgraph CD[Change Director]
    V[Validation]
    D[Deduplication]
    L[Dataset Lock]
    Q[Backpressure Queue]
  end
  NEXT[To Impact Analyzer]

  EB --> V --> D --> L --> Q --> NEXT


````
