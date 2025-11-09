# control flow diagram

````mermaid
sequenceDiagram
%% Control flow from schema change detection to publication
    participant FW as File-Watch Ingest
    participant EB as Event Bus
    participant SEF as SEF Core
    participant LH as Lake Handler
    participant DV as Vault Handler
    participant ORC as Orchestrator
    FW ->> EB: ChangeDetected(dataset, header, change_hint)
    EB ->> SEF: Deliver change event
    SEF ->> SEF: Validate and deduplicate
    SEF ->> SEF: Load prior schema from Metadata Store
    SEF ->> SEF: Compute diff and classify changes
    SEF ->> SEF: Perform impact analysis<br/>and evaluate policies
    SEF ->> LH: Generate lake evolution plan
    SEF ->> DV: Generate vault evolution plan
    SEF ->> LH: Execute lake operations (idempotent)
    SEF ->> DV: Execute vault operations (idempotent)
    SEF ->> SEF: Verify structural and semantic integrity
    SEF ->> SEF: Update Metadata and Audit Log
    SEF ->> EB: Publish SchemaEvolved(dataset, new_version, compatibility)
    EB ->> ORC: Trigger dependent pipelines

````
