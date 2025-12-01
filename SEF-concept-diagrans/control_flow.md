# control flow diagram

````mermaid
sequenceDiagram
    participant FW as File‑Watch Ingest
    participant EB as Event Bus
    participant CD as Change Director
    participant IA as Impact Analyzer
    participant PE as Policy Engine
    participant PL as Migration Planner
    participant EX as Executor
    participant LH as Lake Handler
    participant VH as Vault Handler
    participant VR as Verifier
    participant PUB as Publisher
    participant OR as Orchestrator
    FW ->> EB: ChangeDetected(dataset, header, change_hint)
    EB ->> CD: Deliver(event)
    CD ->> CD: Validate, deduplicate, acquire dataset lock
    CD ->> IA: Load prior schema, compute diff
    IA ->> PE: Impact set (with lineage)
    PE ->> PL: Policy outcome (decisions, obligations)
    PL ->> EX: Ordered, checkpointed plan (idempotency keys)
    EX ->> LH: Apply lake operations (idempotent)
    EX ->> VH: Apply vault operations (idempotent)
    EX ->> VR: Notify completion at checkpoint
    VR ->> VR: Structural + semantic checks, lineage recheck
    VR ->> PUB: Verification passed → publish SchemaEvolved
    PUB ->> EB: Emit(schema.evolved)
    EB ->> OR: Trigger downstream pipelines

````
