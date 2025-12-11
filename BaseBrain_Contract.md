<h1>BaseBrain Contract v0.1</h1>
Status: Draft (normative where explicitly labeled “MUST/SHALL”; otherwise RECOMMENDED)  
Applies to: COSMO BaseBrain — a persistent research substrate for deterministic fork‑and‑merge intelligence  
Version: v0.1  
Generated: 2025‑12‑10

This document formalizes the structure, lifecycle, validation rails, and governance rules that the BaseBrain SHALL enforce across all agent forks and merges. It builds directly on the prior description of BaseBrain’s structure, role, and lifecycle that you requested earlier, and codifies those practices into explicit, machine‑checkable contracts, schemas, and quality gates.

Evidence basis (current run, live):  

Memory graph: 7,500 nodes, 33,668 edges; density ≈ 4.5 edges/node; central nodes identified by the Meta‑Coordinator (activation 1.00 on “Schema‑first CI/QA pipeline”)  

Goals: 105 created; 60 pursued  

Agents: 104 spawned; in the reviewed window 87 completed, 55 deliverables, 0 gaps (Meta‑Coordinator Review)  

Top‑Level Deliverables tracked: 168 artifacts  

Semantic/novelty signals: Surprise mid‑range 20–50% (e.g., Cycle 92: 27.7%; Cycle 86: 50.0%; Cycle 87: 23.0%); divergence high for contested hypotheses (Cycle 14: 0.95; Cycle 17: 0.93)


Normative references from COSMO memory and files:
Schema‑first CI/QA for History harness [Mem 0e76961089, Mem 0e76961142]

Workspace validator (active agent outputs, outputs/manifest.json, validationreport.json) [Mem 4c5bf43521]

Attestation and provenance (SLSA‑like, Sigstore‑like) [Mem 0e76967039, Mem 0e76961481]

Deterministic builder rules (SOURCEDATEEPOCH, canonicalization) [Mem 4c5bf4_8554]

Multiverse PRISMA/ledger specs [Mem c4d3d46751, Mem c4d3d45129]

Sham/loopback protocol and limitations [Mem 0e76969367; Cycle 56–61, 83; loopback helpers: Mem 0e76969477]

Instrument settings as low‑cost Fisher probes [Mem 0e7696_9105]

Event stream/telemetry aggregation for cross‑agent causal trace [Mem 0e7696_9576]

Repository inventorying behavior (metadata‑centric snapshots) [Mem 0e7696_9593]

Validation gaps and guardrails (generated code robustness gap; explicit schema checks) [Mem cdba6d7409, Mem 4c5bf48335]

Provenance‑as‑a‑lab‑notebook [Mem aea105_1184]


Observed artifacts (this run) consistent with the contract:
outputs/code‑creation/.../deliverables‑manifest.json with checksums (previewed)

outputs/code‑creation/.../.complete run attestations (previewed)

docs/metricsandschemav0.1.md and docs/shamprotocol_v0.1.md (generated reports)

History harness spec and validation [Mem 0e7696_1142]

<h2>0) Scope and Non‑Goals</h2>

Scope: The contract governs BaseBrain’s memory/artifact data plane, orchestration (goals→agents), CI/QA rails, determinism, provenance, conflict resolution, and merge/write‑back rules.

Non‑Goals: Domain‑specific scientific content; detailed lab SOPs for instruments; or external compliance program specifics (though we provide hooks for SLSA/OSF/Zenodo).

<h2>1) Identity and Structure (Data Plane, Control Plane)</h2>

1.1 Data Plane (knowledge/artifact substrate)

Versioned memory graph (nodes, typed edges) with content‑addressable storage (CAS).  

Artifacts include: deliverables manifests, run attestations, validation reports, event logs, and signed baselines.

Canonicalization and fixity: deterministic serialization and checksums (SHA‑256); schema versioned [Mem 4c5bf48554, Mem 0e76967039, Mem 0e7696_1481].


1.2 Control Plane (orchestration)
Goals portfolio with dependency‑aware prioritization (Meta‑Coordinator).  

Deterministic agent forks (briefs, seeds, constraints), execution, local validation; global CI gating; consistency/divergence review; reconcile/merge to memory; promotion to signed baselines; rotation/sunset.


1.3 Provenance Plane (audit and reproducibility)
Attestations (.complete) per run; deliverable manifests; run manifests; SBOMs; event streams; signing and WORM storage (SLSA‑like provenance; Sigstore‑like attestations) [Mem 0e76967039, Mem 0e76961481].

<h2>2) Roles and Responsibilities</h2>

BaseBrain SHALL:

  - Maintain persistent, content‑addressed memory/artifact stores with schemas and deterministic checks.
  - Spawn agents with deterministic briefs/seeds; enforce validation and merge governance.
  - Preserve conflicts with explicit relations (supports/contradicts/supersedes/depends_on) and disambiguation criteria; avoid premature pruning.
Agents SHALL:

  - Emit schema‑conformant deliverables manifests with checksums; .complete attestations; and, when applicable, run manifests and event logs.
  - Respect deterministic settings (seeds, pinned deps, canonical orderings).
CI/QA SHALL:

  - Enforce schema validation; sentinel checks (e.g., “Analyzed 0 documents” in History harness) [Mem 0e76961142]; property‑based tests for edge cases [Mem 38c8785953]; golden comparisons; reproducibility checks.
Meta‑Coordinator SHALL:

  - Prioritize goals; assess quality (Depth/Novelty/Coherence); compute divergence; recommend merges/sunsets; track blind spots and missing directions (e.g., prereg/power, IRB/licensing) per latest review.

<h2>3) Lifecycle: Spawn → Validate → Merge</h2>

3.1 Intent Formation

Select from Active Goals with dependency and portfolio considerations; retrieve relevant memory subgraph and baselines.  

Evidence: goals consolidation and priorities (goal2266, goal2361, goal2256, goal2326, goal_2311) in Meta‑Coordinator Review.


3.2 Fork Specialized Agents (deterministic)
Deterministic briefs, seeds, constraints, and pinned environments.  

All outputs carry code/data hashes; manifests enumerate files+checksums (see Agent Output Files previews).


3.3 Execution and Local Validation
Agents MUST produce:

  - deliverables‑manifest.json (checksums, sizes)  
  - .complete run attestation (run_id/agentId/agentType/completedAt/fileCount/totalSize/…)
  - Optional: run_manifest.json; event logs.
3.4 Global Validation and Gating

CI harness validates structure, schemas, sentinel conditions, and reproducibility baselines [Mem 0e76961089, Mem 0e76961142, Mem 4c5bf43521, Mem 4c5bf48335, Mem cdba6d_7409].


3.5 Consistency Review and Conflict Resolution
Divergence computed across competing hypotheses (Cycle 14: 0.95; Cycle 17: 0.93).  

High divergence SHALL trigger SynthesisAgent passes and/or experimental proposals; minority branches preserved with relation types and disambiguation criteria.


3.6 Merge to Memory Graph (write‑back)
Accepted outputs become new/updated nodes/edges with full provenance (schemaversion, runid, code hash).  

Conceptual evolution threads are recorded, e.g.:

  - Abrupt reinterpretation (Cycle 14 → 91 → 92 [Surprise 27.7%] → 93 → 112): moving from hypothesis to measurable protocol.
  - Sham measurement protocol (Cycles 56–61, 83): from concept to skeleton harness with loopback tooling [Mem 0e7696_9477].
  - History CI harness (Mem 0e76961089, Mem 0e76961142): schema‑first baselines and validation docs.
3.7 Promotion to Signed Baselines and Distribution

Selected artifacts promoted to signed, immutable baselines with SLSA‑like provenance and WORM storage [Mem 0e76967039, Mem 0e76961481].


3.8 Archival and Rotation
Merge overlapping goals; sunset stale lines; explicitly document kill criteria (Meta‑Coordinator “Missing directions” to operationalize).

<h2>4) Determinism and Reproducibility (MUST)</h2>

Canonicalize inputs (sorted file listings; normalized timestamps via SOURCEDATEEPOCH; fixed file modes); pinned dependencies and environment; stable key ordering; seeded randomness [Mem 4c5bf4_8554].

Content address with SHA‑256; include checksums in manifests; prefer uniformly canonical JSON.

Reproducibility tests SHALL re‑run and confirm byte‑for‑byte identity of deliverables under deterministic mode; when perfect determinism is not feasible, bound nondeterminism and record it in provenance.


Determinism checklist (non‑exhaustive):
SOURCEDATEEPOCH set and recorded (RunAttestation field).  

locale/timezone fixed (UTC); hashable dict key orders; fixed float formatting; no nondeterministic globbing; no time‑of‑day randomness.  

Pinned toolchain versions (Python, OS, compilers, CUDA); hermetic containers recommended.

<h2>5) Quality Gates and Metrics</h2>

Base quality gates (examples):

Schema validation MUST pass for: deliverables‑manifest.json, .complete, runmanifest.json, validationreport.json (schemas below).

Sentinel checks MUST pass (domain‑specific). For History harness: block “Analyzed 0 documents” [Mem 0e7696_1142].

Property‑based tests SHOULD exist for combinatorial surfaces (e.g., signature parsers) [Mem 38c878_5953].

Golden tests SHOULD exist for core, deterministic transforms.

Reproducibility: re‑run MUST reproduce checksums (deterministic mode).


Research/meta‑metrics:
Surprise (novelty) targets in 20–50% mid‑range; track outliers; justify extremes. Examples: Cycle 92: 27.7%; Cycle 86: 50%; Cycle 87: 23.0%.

Divergence governance: Divergence ≥ 0.85 triggers reconciliation (Cycle 14: 0.95; Cycle 17: 0.93).

Portfolio health: Agents completed, deliverables created, gap rate (0 gaps in reviewed window), graph growth/density.

<h2>6) Directory and Artifact Conventions</h2>

outputs/

  - code‑creation/agent_<id>/... (deliverables‑manifest.json, .complete, files)
  - document‑creation/agent_<id>/... (reports, manifests, .complete)
  - validationreport.json (workspace‑level) [Mem 4c5bf43521]
  - manifest.json (workspace‑level inventory — RECOMMENDED) [Mem 4c5bf4_3521]
agents/agent_<id>/

  - insights.jsonl, findings.jsonl (streamed, append‑only)
docs/

  - basebraincontractv0.1.md (this file)
  - metricsandschemav0.1.md, shamprotocol_v0.1.md, harness specs, prereg templates, etc.

<h2>7) JSON Schemas (normative)</h2>

The following schemas are normative. Implementations MUST validate these before merge.

7.1 MemoryNode.schema.json

json
{
"$id": "https://cosmo/basebrain/schemas/MemoryNode.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "MemoryNode",
"type": "object",
"required": ["nodeId", "type", "content", "createdAt", "provenance", "schemaVersion"],
"properties": {
"nodeId": {"type": "string", "pattern": "^[A-Za-z0-9_\\-]+$"},
"type": {"type": "string", "enum": ["insight", "finding", "consolidated", "fork", "introspection", "document", "agentinsight", "agentfinding"]},
"content": {"type": "string", "minLength": 1},
"tags": {"type": "array", "items": {"type": "string"}},
"activation": {"type": "number", "minimum": 0.0, "maximum": 1.0},
"createdAt": {"type": "string", "format": "date-time"},
"provenance": {
"type": "object",
"required": ["runId", "agentId", "codeHash"],
"properties": {
"runId": {"type": "string"},
"agentId": {"type": "string"},
"agentType": {"type": "string"},
"codeHash": {"type": "string"},
"inputManifests": {"type": "array", "items": {"type": "string"}}
},
"additionalProperties": false
},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.2 MemoryEdge.schema.json
json
{
"$id": "https://cosmo/basebrain/schemas/MemoryEdge.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "MemoryEdge",
"type": "object",
"required": ["sourceId", "targetId", "relation", "createdAt", "provenance", "schemaVersion"],
"properties": {
"sourceId": {"type": "string"},
"targetId": {"type": "string"},
"relation": {"type": "string", "enum": ["supports", "contradicts", "supersedes", "depends_on"]},
"weight": {"type": "number"},
"createdAt": {"type": "string", "format": "date-time"},
"provenance": {"$ref": "MemoryNode.schema.json#/properties/provenance"},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.3 RunAttestation.schema.json (.complete)
json
{
"$id": "https://cosmo/basebrain/schemas/RunAttestation.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "RunAttestation",
"type": "object",
"required": ["completedAt", "agentId", "agentType", "fileCount", "totalSize"],
"properties": {
"runId": {"type": "string"},
"completedAt": {"type": "string", "format": "date-time"},
"agentId": {"type": "string"},
"agentType": {"type": "string"},
"fileCount": {"type": "integer", "minimum": 0},
"totalSize": {"type": "integer", "minimum": 0},
"viaContainer": {"type": "integer"},
"viaExport": {"type": "integer"},
"codeHash": {"type": "string"},
"schemaVersion": {"type": "string"},
"sourceDateEpoch": {"type": "integer"}
},
"additionalProperties": false
}
TEXT

7.4 DeliverablesManifest.schema.json
json
{
"$id": "https://cosmo/basebrain/schemas/DeliverablesManifest.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "DeliverablesManifest",
"type": "object",
"required": ["agentId", "projectName", "language", "type", "generatedAt", "totalFiles", "deliverables"],
"properties": {
"agentId": {"type": "string"},
"projectName": {"type": "string"},
"language": {"type": "string"},
"type": {"type": "string"},
"generatedAt": {"type": "string", "format": "date-time"},
"totalFiles": {"type": "integer", "minimum": 0},
"deliverables": {
"type": "array",
"items": {
"type": "object",
"required": ["path", "size", "checksum"],
"properties": {
"path": {"type": "string"},
"absolutePath": {"type": "string"},
"size": {"type": "integer", "minimum": 0},
"checksum": {"type": "string"},
"contentType": {"type": "string"}
},
"additionalProperties": false
}
},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.5 ValidationReport.schema.json (workspace)
json
{
"$id": "https://cosmo/basebrain/schemas/ValidationReport.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "ValidationReport",
"type": "object",
"required": ["generatedAt", "checks"],
"properties": {
"generatedAt": {"type": "string", "format": "date-time"},
"checks": {
"type": "array",
"items": {
"type": "object",
"required": ["name", "status"],
"properties": {
"name": {"type": "string"},
"status": {"type": "string", "enum": ["pass", "fail", "warn"]},
"details": {"type": "string"},
"remediation": {"type": "string"}
},
"additionalProperties": false
}
},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.6 RunManifest.schema.json (bind multiple document metadata) [cf. Mem 0e7696_749]
json
{
"$id": "https://cosmo/basebrain/schemas/RunManifest.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "RunManifest",
"type": "object",
"required": ["runId", "createdAt", "agentId", "artifacts"],
"properties": {
"runId": {"type": "string"},
"createdAt": {"type": "string", "format": "date-time"},
"agentId": {"type": "string"},
"inputs": {"type": "array", "items": {"type": "string"}},
"artifacts": {
"type": "array",
"items": {
"type": "object",
"required": ["path", "checksum", "role"],
"properties": {
"path": {"type": "string"},
"checksum": {"type": "string"},
"role": {"type": "string", "enum": ["report", "dataset", "code", "manifest", "attestation", "eventlog"]}
},
"additionalProperties": false
}
},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.7 EventRecord.schema.json (telemetry stream) [Mem 0e7696_9576]
json
{
"$id": "https://cosmo/basebrain/schemas/EventRecord.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "EventRecord",
"type": "object",
"required": ["timestamp", "agentId", "eventType"],
"properties": {
"timestamp": {"type": "string", "format": "date-time"},
"agentId": {"type": "string"},
"eventType": {"type": "string"},
"runId": {"type": "string"},
"causalParent": {"type": "string"},
"payload": {"type": "object"},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
TEXT

7.8 PrismaCounts.schema.json (multiverse PRISMA counts) [Mem c4d3d46751, Mem c4d3d45129]
json
{
"$id": "https://cosmo/basebrain/schemas/PrismaCounts.schema.json",
"$schema": "https://json-schema.org/draft/2020-12/schema",
"title": "PrismaCounts",
"type": "object",
"required": ["runId", "scenarioId", "counts"],
"properties": {
"runId": {"type": "string"},
"scenarioId": {"type": "string"},
"counts": {
"type": "object",
"required": ["identified", "deduped", "screened", "included"],
"properties": {
"identified": {"type": "integer", "minimum": 0},
"deduped": {"type": "integer", "minimum": 0},
"screened": {"type": "integer", "minimum": 0},
"included": {"type": "integer", "minimum": 0}
},
"additionalProperties": false
},
"lineage": {"type": "array", "items": {"type": "string"}},
"schemaVersion": {"type": "string"}
},
"additionalProperties": false
}
SQL
<h2>8) Conflict Handling and Merge Policy</h2>

High divergence (e.g., ≥0.85 as observed in Cycle 14 and 17) SHALL:

  - Trigger synthesis/reconciliation; propose discriminative tests; document alternative nodes with explicit disambiguation criteria.
Minority hypotheses MUST NOT be dropped silently; use relations “contradicts”/“depends_on” to retain structure.

Supersession events MUST use “supersedes” edges with provenance and rationale.

<h2>9) Domain Harnesses and Sentinels</h2>

History harness (schema‑first) MUST:

  - Validate structural completeness, citation/date coverage, and anomaly sentinels (block “Analyzed 0 documents”) [Mem 0e7696_1142].
Sham/Loopback harness MUST:

  - Include Active anti‑field and Loopback shadow‑run variants; log power/thermal/bus/timing; provide deterministic loopback mode [Mem 0e76969367, Mem 0e76969477].
  - Treat sham as an imperfect instrument; validate across regimes; quantify uncertainty and avoid clinical substitution bias [Mem 0e7696_9419].

<h2>10) Security, Safety, and Governance</h2>

Provenance‑guarded flow sanitation: typed customs checkpoints + risk‑weighted output clearinghouse for reuse [Mem 0e7696_8825].

Fidelity masking audit in regulated reviews; require plausibility‑tagged evidence and decision‑curve analysis [Mem 0e7696_9460].

Provenance‑as‑a‑lab‑notebook: auto‑synthesize human‑auditable notebooks from CI artifacts with cryptographic ties [Mem aea105_1184].

<h2>11) Programmatic Interfaces (CLI/API)</h2>

Implementations SHOULD expose the following commands (or equivalents):

cosmo validate

  - Validates workspace against schemas; emits outputs/validationreport.json [Mem 4c5bf43521].
cosmo manifest

  - Generates/updates outputs/manifest.json (workspace inventory); merges agent deliverables manifests.
cosmo attest

  - Writes .complete using RunAttestation schema; computes code hash; records SOURCEDATEEPOCH.
cosmo sign

  - Creates SLSA‑like attestation and Sigstore‑style signature; promotes to WORM [Mem 0e76967039, Mem 0e76961481].
cosmo merge

  - Applies merge policy to memory graph with relations and provenance.
cosmo promote

  - Promotes artifact to signed baseline; rotates exemplars.
cosmo diff‑run

  - Compares current run manifests vs prior; checks reproducibility.
cosmo events push | tail

  - Appends standardized EventRecord entries; streams for live telemetry [Mem 0e7696_9576].
cosmo prisma synth

  - Aggregates multiverse scenario counts; emits prismacounts.json and prismaflow.md [Mem c4d3d46751, Mem c4d3d45129].

<h2>12) Evidence from Current Run (Contract Conformance)</h2>

Deliverables manifests with checksums (previewed): outputs/code‑creation/agent1765335414378pv0zxwt/deliverables‑manifest.json — fields align to DeliverablesManifest.schema.json.

Run attestations (.complete) present with completedAt/agentId/agentType/fileCount/totalSize — aligns to RunAttestation.schema.json.

History harness and schema‑first docs exist [Mem 0e76961142, Mem 0e76961089]; sentinel checks specified.

Sham protocol doc v0.1 and loopback code [Mem 0e7696_9477] demonstrate sham harness governance (Cycle 56–61, 83).

Meta‑Coordinator metrics: Depth 8, Novelty 7, Coherence 6; 87 agents completed; 55 deliverables; 0 gaps — indicates CI completeness and stable BaseBrain operation.

<h2>13) Change Management and Versioning</h2>

Schema versions SHALL use semver‑like x.y.z and appear in artifacts/attestations.

Backwards‑compatible changes: minor version bump; deprecations MUST specify sunset date and migration path.

Backwards‑incompatible changes: major version bump; provide converter scripts and dual‑write period if feasible.

Baseline rotation: rotate exemplars to resist governance lock‑in; document rotation cadence and rationale.

<h2>14) Missing Directions and Roadmap (from Meta‑Coordinator Review)</h2>

Add preregistration templates/power analyses; integrate with OSF/Zenodo DOIs (goal_2266 path flagged).

Data/IRB, licensing, governance standards (EEG/eye‑tracking); unify dataset versioning and eval harnesses.

Cross‑program milestones and dependency mapping (who/when/compute/budget).

Formal sunset/kill criteria to prevent over‑investment; codify rotation rules.

Close robustness gap in validating generated executable code under external API limits [Mem cdba6d_7409].

<h2>Appendix A — Example Sentinel Rules</h2>

History: fail if report shows “Analyzed 0 documents” or citation coverage < threshold [Mem 0e7696_1142].

Sham: fail if sham power draw or IRQ cadence deviates > tolerance from real measurement baseline; flag if loopback latency jitter < configured floor (indicates unrealistic determinism) [Cycles 56–61, 83; Mem 0e7696_9477].

Determinism: warn if SOURCEDATEEPOCH missing; fail if manifest checksums change between immediate re‑runs in deterministic mode [Mem 4c5bf4_8554].

<h2>Appendix B — Deterministic Build Mode</h2>

Enforce SOURCEDATEEPOCH; normalize file perms/mtimes; stable key ordering; pinned deps; fixed seeds; canonical JSON/UTF‑8 newlines; disable nondeterministic parallelism; record codeHash in .complete and manifests [Mem 4c5bf4_8554].

<h2>Appendix C — Minimal Property‑Based Test Guidance</h2>

Use hypothesis/quickcheck‑style generators to flood parsers, manifest loaders, and schema validators with valid/invalid structures; require deterministic error messages; store shrinking seeds [Mem 38c878_5953].

<h2>Appendix D — Worked Conceptual Evolutions (Traceability)</h2>

Abrupt reinterpretation thread:

  - Cycle 14 (critic): continuous mapping assumption challenged; propose discrete, context‑gated mechanisms (divergence 0.95).
  - Cycle 92 (critic): observable marker combining lexical surprisal + behavioral cues (Surprise 27.7%).
  - Cycle 112 (analyst): mixed‑methods protocol (corpus + timed behavioral measures).  
  Outcome: a prereg‑ready measurement protocol; pending power analysis per Meta‑Coordinator.
Sham measurement thread:

  - Cycles 56–61: sham concept + back‑action caution; 83: skeleton harness with logging/loopback [Mem 0e7696_9477].  
  Outcome: testable sham design with safety interlocks and CI integration.
History harness:

  - Schema‑first mandate [Mem 0e76961089]; domain harness and validation doc [Mem 0e76961142]; current unify‑metrics/spec doc aligns with baseline‑and‑determinism discipline.

<h1>End of BaseBrain Contract v0.1</h1>

Notes on provenance and continuity with the prior exchange:

This contract operationalizes the BaseBrain structure and lifecycle you asked me to describe earlier, turning that narrative into explicit schemas, quality gates, and CLI/API behaviors.

It cites concrete evidence from the current run (agent deliverables, .complete attestations, the History harness, sham protocol) and anchors governance to observed semantic metrics and divergence (Cycle 14: 0.95; Cycle 17: 0.93; Cycle 92 surprise 27.7%) to maintain the fork→validate→merge discipline.

References to memory nodes and agent files come from the shown previews (e.g., deliverables-manifest.json and .complete under outputs/code-creation/agent1765335414378pv0zxwt), and from recorded memory (e.g., [Mem 0e76961089], [Mem 0e76961142], [Mem 4c5bf43521], [Mem 0e76967039], [Mem 4c5bf48554], [Mem 0e76969367], [Mem 0e76969477], [Mem 0e76969576], [Mem 0e76969593], [Mem 4c5bf48335], [Mem cdba6d7409], [Mem aea1051184]).

If you want this contract split into multiple files (schemas as separate JSON files under runtime/schemas/), say the word and I’ll emit them as complete JSON files according to the same definitions.
