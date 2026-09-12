Staff Platform Engineer building and operating ingestion pipelines that move telemetry from edge devices to queryable storage.

## Michale Kautzer

I design and operate distributed ingestion systems that handle high-throughput device telemetry, owning the full path from edge collection to durable storage. My work focuses on partitioning strategies, backpressure mechanics, and schema evolution across large-scale deployments. I prioritize operational stability over feature velocity, accepting tighter coupling in exchange for predictable failure modes. I've built internal tooling that reduces deployment friction and improves on-call signal quality.

### 🛠 Tech & Infrastructure

**Core:** `TypeScript`, `Node.js`, `Kafka`, `PostgreSQL`

**Data:** `Parquet`, `Redis`, `Debezium`

**Infra:** `Kubernetes`, `Terraform`, `Prometheus`, `Grafana`

**Tooling:** `GitHub Actions`, `Argo CD`, `OpenTelemetry`

### ⚙️ Engineering Areas

- Designing partition keys that balance write throughput against query locality for time-series telemetry.
- Implementing consumer groups with dead-letter queues and replayable offsets to handle partial failures.
- Automating schema migrations across multiple environments with zero-downtime backfill strategies.
- Building internal CLIs and CI pipelines that standardize deployment and rollback procedures.

### 🔭 Current Focus

- Reducing tail latency spikes caused by hot partitions in Kafka during traffic bursts.
- Evaluating a move from pull-based to push-based ingestion to cut end-to-end latency by 40%.
- Improving schema evolution tooling to support backward-compatible changes without manual coordination.
- Tuning Kubernetes HPA thresholds to avoid thrashing during diurnal load patterns.

### 📌 Engineering Notes

- Tests that require a running cluster are integration tests; keep them out of the default test suite and run them in CI only when the cluster is available.
- Prefer additive migrations over destructive ones; every schema change should be reversible within one release cycle.
- Retries belong at the edge, not in the middle; idempotent consumers and bounded retry counts prevent cascading failures.
- Every service must export traces and metrics; a deployment without dashboards is an incident waiting to happen.

### 🧭 How I Work

- I write down the failure modes before the happy path; if I can't explain how it breaks, I don't build it yet.
- I favor boring technology that the team already knows over novel tools that add cognitive load.
- I review code for operational impact first, then correctness, then style.

*Reliability is not a feature; it's the absence of surprises.*