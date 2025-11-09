# processing state  diagram

````mermaid
stateDiagram-v2
%% Internal processing state machine of the SEF
    [*] --> Received
    Received: Event received
    Received --> Validated: Message parsed and basic checks passed
    Validated: Event syntactically valid
    Validated --> Classified: Diff computed and change classes identified
    Classified: Change set known
    Classified --> Planned: Impact analysis and policies applied
    Planned: Evolution plan constructed
    Planned --> Applying: Handlers executing operations
    Applying: Plan being executed
    Applying --> Verifying: Structural and semantic checks
    Verifying: Post-apply checks
    Verifying --> Published: Metadata updated and event emitted
    Verifying --> Rollback: Verification failed
    Rollback: Compensating actions
    Rollback --> Planned: Re-plan with adjusted constraints
    Published: Schema version accepted and communicated
    Published --> [*]


````
