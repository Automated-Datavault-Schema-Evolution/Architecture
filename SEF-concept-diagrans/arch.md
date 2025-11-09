# Architecutre diagram

````mermaid
flowchart LR
%% Detailed logical architecture of the Schema Evolution Framework (SEF)

%% --- Producers and downstream ---
    subgraph PRODUCERS["Producers"]
        FW["File-Watching Ingest Service (announces tabular file changes)"]
    end

    EB["Event Bus"]

    subgraph DOWN["Downstream"]
        ORCH["Pipeline Orchestrator"]
        CON["Consumers and Semantic Views"]
    end

%% --- SEF core ---

    subgraph SEF["Schema Evolution Framework"]
        DIR["Change Director (classify and orchestrate)"]
        IM["Impact Analyzer (lineage and dependency scan)"]
        PP["Policy Engine (rules and approvals)"]
        MP["Migration Planner (plan operations per layer)"]
        EX["Executor (idempotent apply)"]
        VR["Verifier (post-apply checks)"]
        MD["Metadata and Lineage Store"]
        AU["Audit Log and Metrics"]
    end

%% --- Handlers as aggregation points ---

    subgraph HANDLERS["Schema Handlers"]
        LH["Data Lake Handler"]
        DVH["Data Vault Handler"]
    end

%% --- Platform layers ---

    subgraph LAKE["Data Lake Layer"]
        LC["Logical Catalog"]
        LS["Storage Objects"]
    end

    subgraph DV["Data Vault 2.0 Layer"]
        HV["Hubs"]
        LV["Links"]
        SV["Satellites"]
    end

%% ========== Flows ==========

%% Ingestion into SEF
    FW --> EB --> DIR
%% SEF internal flow
    DIR --> IM --> MP --> EX --> VR
    DIR --> PP
    DIR <--> MD
    VR --> MD
    VR --> AU
%% SEF -> handlers
    MP --> LH
    MP --> DVH
    EX --> LH
    EX --> DVH
%% Handlers -> platform objects
    LH --> LC
    LH --> LS
    DVH --> HV
    DVH --> LV
    DVH --> SV
%% SEF publication to downstream
    DIR -->|" publish schema-evolved "| EB
    EB --> ORCH --> CON


````
