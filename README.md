## Node.js Senior Interview Prep Guide

A curated set of senior-level Node.js interview questions and hands-on prompts. Organized by topic, with an additional section tailored to the provided job requirements.

### How to use
- Skim the topic sections to identify weak spots.
- For each question, try to answer aloud and note gaps.
- Do the hands-on prompts under time constraints (30–60 minutes each).

## Categorized Node.js interview questions

### Core JavaScript in Node
- **scoping**: Differences between `var`, `let`, and `const`. When does the temporal dead zone matter in backend code?
- **closures**: Real examples where closures help (memoization, encapsulation) and where they hurt (memory leaks).
- **equality**: `==` vs `===` and pitfalls with objects, `NaN`, and `Object.is`.
- **prototypes**: How prototype chains work and implications for extending built-ins in Node.
- **immutability**: What is a pure function and how does purity improve reliability in services?
- **copying**: Safe deep cloning strategies; structuredClone vs JSON tricks; caveats with Buffers and Dates.

### Node runtime and architecture
- **event loop**: Describe phases (timers, pending, idle, poll, check, close). Where do network IO and timers fit?
- **tasks**: Microtasks vs macrotasks: `Promise.then`, `queueMicrotask`, `process.nextTick`, `setImmediate`, `setTimeout`.
- **libuv**: What is libuv? Which operations use the thread pool (fs, crypto, DNS)?
- **cpu-bound**: Symptoms of event loop blocking; mitigation with Worker Threads, sharding, offloading.
- **isolation**: When to choose Worker Threads vs Cluster; memory, IPC, and failure isolation trade-offs.
- **timers**: Differences between `setImmediate` and `setTimeout(0)` under load.

### Modules and packaging (CJS vs ESM)
- **formats**: Differences between CommonJS and ES Modules in Node; interop strategies.
- **resolution**: Effects of `type: "module"`, `.mjs`, `.cjs`; resolving “ERR_REQUIRE_ESM”.
- **assets**: Importing JSON, native addons (N-API), and WASM.
- **exports**: Conditional exports and subpath imports in `package.json`.
- **tooling**: Source maps and loaders; custom ESM loader hooks use cases.

### Asynchronous patterns
- **paradigms**: Callbacks vs Promises vs `async/await`: error handling, readability, control flow.
- **conversion**: Converting callback APIs to promises; when not to wrap.
- **concurrency**: Running parallel tasks with limited concurrency; pools and queues.
- **cancellation**: Using `AbortController` and propagating signals across layers.
- **safety**: Avoiding unhandled rejections and swallowed errors; global handlers.

### Streams and buffers
- **types**: Readable, Writable, Duplex, Transform streams; object mode.
- **backpressure**: How `pipe`/`pipeline` manage backpressure; when to set `highWaterMark`.
- **files**: Streaming large file uploads/downloads; partial content and range requests.
- **buffers**: `Buffer` vs `ArrayBuffer`/TypedArray; zero-copy patterns.
- **performance**: Common mistakes that break streaming performance.

### HTTP, networking, and Web
- **http server**: Keep-alive, connection pooling, and socket reuse.
- **http2**: When to use HTTP/2; multiplexing and header compression trade-offs.
- **caching**: Cache control, ETags, conditional requests, and CDN considerations.
- **cors**: What CORS is and safe configurations; preflight implications.
- **real-time**: WebSockets vs SSE vs long-polling; choosing based on requirements.

### Frameworks (Express/Fastify/Nest)
- **express vs fastify**: Performance, plugin ecosystem, and DX.
- **middleware**: Ordering, error middleware, and async error handling.
- **validation**: Input validation with `zod`, `joi`, or class-validator; sanitization strategies.
- **nest**: Modules, providers, injectables, and interceptors; testing.
- **structure**: Designing a modular, testable API architecture.

### Data access and caching
- **orms**: Compare Prisma, TypeORM, Sequelize; when to use query builders.
- **pooling**: Designing connection pools for Postgres/MySQL; timeouts and retries.
- **transactions**: Isolation levels and retry patterns (e.g., serialization failures).
- **pagination**: Cursor vs offset pagination; trade-offs and consistency.
- **caching**: In-memory vs Redis; eviction policies; cache invalidation strategies.

### Security
- **risks**: Prototype pollution, RCE, deserialization attacks, ReDoS.
- **secrets**: Managing secrets and environment configuration; parameter store vs vault.
- **injection**: Guarding against SQL/NoSQL injection; prepared statements, query builders.
- **web vulns**: CSRF, XSS, clickjacking; API vs server-rendered contexts.
- **rate limiting**: Strategies and dealing with burst traffic; IP/user-based limits.
- **supply chain**: Lockfiles, `npm audit`, provenance, pinning, and SCA.

### Performance and scalability
- **metrics**: Measuring event loop lag; avoiding GC pauses.
- **profiling**: Heap snapshots, allocation timelines, CPU profiles, flamegraphs.
- **hot paths**: Optimizing JSON parsing/serialization and schema validation.
- **scale-out**: Cluster, PM2, containers; sticky sessions and horizontal scaling.
- **throughput**: Handling high-throughput streaming with backpressure and pooling.

### Observability and debugging
- **debugging**: `--inspect`, Chrome DevTools, VS Code.
- **logging**: Structured logs, correlation IDs, and log levels.
- **health**: Health checks; readiness/liveness probes.
- **telemetry**: OpenTelemetry basics; context propagation in async code.
- **errors**: Centralized error handling; domains vs `async_hooks` caveats.

### Testing
- **layers**: Unit, integration, and e2e testing; trade-offs and tooling.
- **runners**: Node built-in test runner vs Jest/Vitest.
- **async**: Testing promises, timers, streams, and HTTP.
- **isolation**: Determinism, seeding, and faking time/network.
- **contracts**: Consumer-driven contracts and schema evolution.

### Build, deploy, and runtime management
- **config**: 12-factor app principles and environment-specific configs.
- **docker**: Image size optimization, layer caching, and security (distroless).
- **cicd**: Test matrix, caching, artifacts, and canary rollouts.
- **versions**: Node version management and compatibility strategies.
- **feature flags**: Gradual rollouts and kill switches in backends.

### API design and reliability
- **rest**: Status codes, pagination, and error contracts.
- **alt protocols**: gRPC/GraphQL in Node; when and why; performance.
- **reliability**: Idempotency keys and safe retries; circuit breakers and timeouts.
- **compat**: Schema evolution and backward compatibility.

### Advanced Node internals
- **async hooks**: Context propagation and caveats.
- **n-api**: Native addons model; use cases and risks.
- **memory**: `--max-old-space-size` and memory tuning approaches.
- **threading**: Single-threaded JS with thread pool implications.

## Questions aligned to the job requirements

### Distributed systems and architecture (scalable, secure, high-performance)
- **trade-offs**: Pick two: latency, throughput, consistency. How do you reason about trade-offs for a customer-facing API?
- **consistency**: When to choose eventual consistency; patterns to make it acceptable (sagas, read repair).
- **failure**: Design for partial failures; timeouts, retries with backoff/jitter, circuit breakers.
- **isolation**: Bulkheads and partitioning; preventing cascading failures.
- **data flow**: Event-driven vs request/response; when to batch and when to stream.
- **observability**: SLIs/SLOs for services; connecting them to error budgets.
- **security**: Threat modeling for an internet-exposed Node service; authn/z, secrets, data protection.
- **evolution**: How to evolve schemas and APIs without downtime; deprecation policies.

### Microservices and service design
- **boundaries**: Defining service boundaries; avoiding chatty communication.
- **contracts**: API versioning; backward/forward compatibility.
- **orchestration**: Sagas vs orchestration engines vs choreography.
- **discovery**: Service discovery, DNS, and connection management.
- **idempotency**: Designing idempotent operations in distributed flows.
- **migration**: Strangler pattern to move from monolith to microservices incrementally.
- **testing**: End-to-end vs contract tests; test flakiness mitigation.

### Data structures, algorithms, and design patterns
- **structures**: Choosing between arrays, maps, tries, heaps in Node contexts.
- **algorithms**: Practical complexity trade-offs for pagination, deduplication, searching.
- **patterns**: Strategy, observer, factory, builder, decorator in Node.
- **concurrency**: Producer-consumer, work queues, bounded buffers in JS.
- **caching**: LFU/LRU vs TTL; write-through vs write-back.

### RESTful API design and development
- **nouns vs verbs**: Resource modeling; sub-resources; relationships.
- **errors**: Error contracts; problem+json; validation error shapes.
- **pagination**: Offset vs cursor; opaque cursors and stability.
- **filtering**: Designing powerful but safe filtering/sorting.
- **docs**: OpenAPI/Swagger-first vs code-first; client generation.
- **security**: OAuth2/OIDC, JWT pitfalls, rate limiting, and abuse prevention.

### Messaging and streams (Kafka, RabbitMQ)
- **semantics**: At-least-once vs exactly-once; deduplication and idempotency.
- **ordering**: Partitioning keys and ordering guarantees; consumer groups.
- **retries**: Dead-letter queues, retry backoff, and poison message handling.
- **compaction**: Log compaction vs retention; modeling entities as logs.
- **schemas**: Schema registry; evolution and compatibility.
- **ops**: Throughput tuning; batching; consumer lag monitoring.

### Databases (SQL, NoSQL, and more)
- **modeling**: Normalization vs denormalization; OLTP vs OLAP.
- **transactions**: Isolation levels; phantom reads; application-level retries.
- **indexes**: Query planning and index design; covering indexes.
- **sharding**: Choosing shard keys; cross-shard queries; rebalancing.
- **consistency**: Read replicas, lag, and read-your-writes strategies.
- **noSQL**: Document vs key-value vs columnar vs graph—when and why.
- **migrations**: Zero-downtime migrations; backfills and dual writes.

### Cloud platforms (AWS required; GCP/Azure plus)
- **networking**: VPCs, subnets, security groups; private links for databases.
- **compute**: ECS/Fargate vs EKS vs Lambda for Node services; cold starts and sizing.
- **data**: RDS/Aurora, DynamoDB; choosing based on access patterns.
- **infra**: IaC with Terraform/CDK; drift detection; environments.
- **resilience**: Multi-AZ and multi-region patterns; failover testing.
- **storage**: S3 performance, multipart uploads, presigned URLs, and S3 select.
- **observability**: CloudWatch, X-Ray/OpenTelemetry; cost monitoring.
- **security**: IAM least privilege; KMS; secret managers; boundary protection.

### Containerization and orchestration (Docker, Kubernetes)
- **images**: Multi-stage builds, slim bases, distroless; SBOM and scanning.
- **runtime**: Resource limits/requests; CPU throttling and Node event loop.
- **networking**: Ingress, service meshes (e.g., Istio/Linkerd), mTLS.
- **state**: ConfigMaps, Secrets; persistent volumes and storage classes.
- **deployments**: Rolling, blue/green, canary; readiness and liveness probes.
- **autoscaling**: HPA based on CPU/RAM/custom metrics; KEDA for queues.

### CI/CD and DevOps practices
- **pipelines**: Designing fast, reliable pipelines; caching strategies.
- **tests**: Sharding tests; flaky test detection and quarantine.
- **artifacts**: Versioning, provenance, SBOMs; artifact registries.
- **security**: Supply-chain security; signing images; dependency pinning.
- **releases**: Feature flags, migrations, and rollout safety.
- **observability**: Automated canary analysis; rollback triggers.

### Generative AI (GenAI) in production
- **use cases**: Selecting tasks (RAG, summarization, extraction, codegen) with measurable ROI.
- **models**: Trade-offs: hosted APIs vs open-source models on GPUs; latency and cost.
- **pipelines**: RAG architectures; vector stores; chunking and embeddings; prompt caching.
- **quality**: Prompt engineering vs system design; evals/benchmarks; guardrails.
- **safety**: PII handling, jailbreak prevention, toxicity filters, output validation.
- **observability**: Tracing, token accounting, drift detection; human-in-the-loop.
- **scalability**: Concurrency limits, streaming responses, batching, fallbacks.
- **tooling**: Popular Node frameworks and SDKs for GenAI and RAG.

### Communication and leadership
- **stakeholders**: Explaining trade-offs to product/UX in plain language.
- **alignment**: Writing RFCs/ADRs; decision records and reversibility.
- **mentorship**: Coaching teammates; code review guidelines; raising the bar.
- **incidents**: Postmortems; blameless culture; action items and follow-through.

## Hands-on coding exercises (practice prompts)
- Implement a concurrency-limited task runner with cancellation (use `AbortController`).
- Build an HTTP server that streams large files with range requests and proper caching headers.
- Write a Transform stream to gzip incoming data and handle backpressure using `pipeline`.
- Implement a rate limiter using Redis (sliding window) and expose middleware for Express/Fastify.
- Create a worker-queue using BullMQ or RabbitMQ with retry/backoff and idempotency.
- Add OpenTelemetry tracing to an Express app with context propagation across async boundaries.
- Implement graceful shutdown: drain connections, finish in-flight jobs, close pools, handle SIGTERM.
- Diagnose a synthetic memory leak: reproduce, take heap snapshots, identify retained objects, and fix.
- Build a streaming CSV parser using Node streams that outputs NDJSON records.

## System design prompts (Node-focused)
- Design an API gateway that handles authentication, rate limiting, routing, and observability.
- Architect a multi-tenant SaaS with per-tenant isolation for data, caching, and throttling.
- Real-time collaboration backend (docs/whiteboard): OT/CRDT, presence, and conflict resolution.
- High-volume event ingestion service: batching, backpressure, at-least-once semantics.
- Media processing pipeline: chunked uploads, virus scanning, transcoding workers, CDN, pre-signed URLs.
- A chat service with presence and delivery guarantees; scaling websockets; stickiness.
- An order service with exactly-once semantics over Kafka; idempotency and dedupe.

---

If you want model answers, flashcards, or a timed quiz version, open an issue or extend this README.

## Model answers (concise)

### Core JavaScript in Node
- **var/let/const, TDZ**: `var` is function-scoped and hoisted (initialized to undefined); `let/const` are block-scoped and hoisted into TDZ until initialization. Prefer `const`, use `let` for reassignment; TDZ catches uninitialized access early.
- **Closures**: Functions capture outer variables; useful for encapsulation and factories; can cause leaks if long-lived closures capture large objects.
- **== vs ===, NaN**: `===` checks type + value; `==` coerces. `NaN !== NaN`; use `Number.isNaN`. `Object.is` distinguishes `+0/-0` and treats `NaN` equal to itself.
- **Prototypes**: Objects delegate to `[[Prototype]]` chain; avoid mutating built-ins; extend via composition or subclasses where appropriate.
- **Pure functions**: No side effects, same output for same input; simpler tests and caching; reduces shared-state bugs in services.
- **Deep cloning**: `structuredClone` (Node 17+), or `v8.serialize`/`deserialize`; JSON tricks lose types; be careful with Buffers, Dates, Maps/Sets.

### Node runtime and architecture
- **Event loop phases**: timers → pending callbacks → idle/prepare → poll (I/O) → check (`setImmediate`) → close callbacks. Microtasks run after each phase.
- **Micro vs macro**: `Promise.then/queueMicrotask` (micro); `setTimeout/setImmediate` (macro); `process.nextTick` runs before other microtasks, can starve loop if abused.
- **libuv/thread pool**: Offloads fs, crypto, zlib, DNS (non-getaddrinfo) to a pool; size via `UV_THREADPOOL_SIZE`.
- **CPU-bound**: Blocks loop; detect via event loop lag; fix with Worker Threads, native addons, or service decomposition.
- **Workers vs Cluster**: Workers share memory and are for CPU-bound parallelism; Cluster forks processes for multi-core scaling and isolation.
- **setImmediate vs setTimeout(0)**: `setImmediate` queues in check phase (often after I/O); `setTimeout(0)` schedules in timers phase with clamped delay.

### Modules and packaging
- **CJS vs ESM**: CJS uses `require/module.exports` (sync); ESM uses `import/export` (static, async). Interop: dynamic `import()` or create dual packages via conditional exports.
- **type/module flags**: `type: "module"` treats `.js` as ESM; use `.cjs` for CJS; `.mjs` forces ESM. Fix ERR_REQUIRE_ESM by switching to `import()` or ESM entry.
- **Assets**: JSON via `import ... assert { type: 'json' }` (ESM) or `require`; N-API for native addons; WASM via `WebAssembly` or loaders.
- **Conditional exports**: `exports` field with `import`/`require` conditions; avoid deep requires; document subpaths.

### Async patterns
- **Callbacks vs Promises/async**: Promises/async improve composition and error flow; callbacks risk callback hell and error conventions.
- **Promisify**: Use `util.promisify` or wrap carefully; do not promisify hot paths that create many closures if perf critical.
- **Limited concurrency**: Use pools/semaphores; e.g., run N at a time to avoid thundering herd and hitting rate limits.
- **Cancellation**: `AbortController` with fetch, streams, and custom APIs; propagate `signal` and handle `abort` events.
- **Unhandled rejections**: Always `await` or attach `.catch`; add process-level handlers to log, then fail fast or isolate.

### Streams and buffers
- **Stream types**: Readable (source), Writable (sink), Duplex (both), Transform (read→write transform). Object mode for non-Buffer chunks.
- **Backpressure**: `write()` returns false; wait for `drain`. Prefer `pipeline` to compose safely.
- **Range requests**: Support `Range` header, respond 206, handle `If-None-Match`/`If-Modified-Since` for caching.
- **Buffer vs ArrayBuffer**: `Buffer` is Node-specific over Uint8Array; prefer zero-copy slices; beware of mutation.

### HTTP and Web
- **Keep-alive/pooling**: Reuse sockets with agents; tune `maxSockets`, `keepAlive`; reduces TCP/TLS handshakes.
- **HTTP/2**: Multiplex streams on one connection; good for many small resources; mind head-of-line at TCP layer.
- **CORS**: Preflight for non-simple requests; restrict origins/headers/methods; send credentials only when needed.
- **Real-time**: WebSockets (bi-directional low-latency), SSE (simple server→client), long-polling (fallback).

### Frameworks
- **Express vs Fastify**: Fastify is faster, schema-first, good plugin system; Express is ubiquitous and minimal.
- **Middleware ordering**: Register in correct order; error middleware signature `(err, req, res, next)` must be last.
- **Validation**: Enforce at edges with `zod/joi`/class-validator; reject unknown fields; apply output validation for contracts.
- **Nest concepts**: Modules group providers; DI via injectables; interceptors for cross-cutting concerns.

### Data and caching
- **ORM trade-offs**: Prisma (DX, schema), TypeORM (decorators), Sequelize (mature, dynamic). Query builders (knex) for control.
- **Pooling**: Tune max connections per service; set timeouts; avoid synchronous migrations at boot.
- **Transactions**: Understand isolation (read committed vs serializable); implement retries for serialization anomalies.
- **Pagination**: Cursor (stable under writes) vs offset (simple but can skip/duplicate under churn).
- **Caching**: Choose LRU/LFU; define TTLs; design invalidation strategies (write-through/write-back).

### Security
- **Prototype pollution/ReDoS**: Use safe merges, validate inputs, avoid catastrophic regex; limit payload sizes and timeouts.
- **Secrets**: Never in code; use env/SM/SSM/KMS; rotate regularly.
- **Injection**: Parameterize queries; escape identifiers; validate JSON paths for NoSQL.
- **CSRF/XSS**: Use same-site cookies/CSRF tokens; sanitize/encode outputs; set CSP, X-Frame-Options.
- **Rate limiting**: Sliding window/token bucket; per-IP/user; store in Redis; handle bursts.
- **Supply chain**: Pin versions, lockfiles, audit, provenance/signing, minimal privileges in CI.

### Performance and scalability
- **Event loop lag**: Measure with `perf_hooks.monitorEventLoopDelay`; alert when high; offload CPU.
- **Profiling**: Use `--inspect`/DevTools, clinic.js/0x, heap snapshots to find leaks.
- **JSON hot path**: Precompile schemas, stream parse, avoid double parse/stringify.
- **Horizontal scale**: Cluster/PM2/K8s; sticky sessions for websockets or use shared state (Redis, pub/sub).

### Observability and debugging
- **Logging**: Structured (JSON), correlation IDs, consistent levels; avoid PII.
- **Health**: `/live` vs `/ready`; include dependency checks for readiness only.
- **Tracing**: OpenTelemetry SDK; propagate context through async boundaries; sample wisely.
- **Errors**: Central handler maps to consistent problem responses; fail fast on invariants.

### Testing
- **Runner**: Built-in test runner is lightweight; Jest/Vitest for ecosystem/mocks.
- **Async tests**: Use fake timers for time-based logic; `supertest`/`undici` for HTTP.
- **Isolation**: Reset globals, randomize ports, seed DBs deterministically.
- **Contracts**: Pact/CDC to keep microservices decoupled; schema checks in CI.

### Build/deploy/runtime
- **12-factor**: Config via env; stateless processes; logs as streams.
- **Docker**: Multi-stage builds, `npm ci --only=prod`, distroless base; scan images.
- **CI/CD**: Cache deps, parallelize tests, canary, automated rollback.
- **Feature flags**: Gradual rollouts, kill switches, audit usage.

### API design and reliability
- **REST**: Clear resource modeling, consistent status codes, pagination and filtering standards.
- **Idempotency**: Idempotency keys stored server-side; retries safe under network flakiness.
- **Circuit breakers/timeouts**: Set per dependency; budgeted timeouts.

### Advanced internals
- **async_hooks**: Track async context (for tracing) but can be costly; beware library incompatibilities.
- **N-API**: Build native modules with ABI stability; use for CPU-bound tasks.
- **Memory tuning**: `--max-old-space-size` to raise heap; profile before tuning.

### Distributed systems (trade-offs)
- **CAP/latency**: Explicitly trade consistency vs availability vs latency; communicate SLAs and fallbacks.
- **Eventual consistency**: Use sagas/outbox; design UIs for asynchronous completion.
- **Partial failure**: Jittered retries, DLQs, bulkheads; idempotent handlers.

### Microservices
- **Boundaries**: Align with business capabilities; avoid shared DB schemas.
- **Sagas**: Orchestration (central coordinator) vs choreography (event-driven); choose based on coupling/visibility needs.
- **Discovery**: DNS/service mesh; exponential backoff; connection pooling per service.

### Messaging (Kafka/RabbitMQ)
- **Delivery**: At-least-once with idempotency; exactly-once via transactions (Kafka) plus dedupe.
- **Ordering**: Partition by key; avoid cross-partition ordering assumptions.
- **Retries/DLQ**: Exponential backoff; poison pill quarantine; visibility timeouts (queues).

### Databases
- **Indexes**: Use covering indexes; watch selectivity; avoid over-indexing writes.
- **Sharding**: Choose keys that avoid hotspots; plan re-sharding; consider consistent hashing.
- **Migrations**: Backward-compatible steps: expand → backfill → switch → contract.

### Cloud (AWS)
- **Compute**: Lambda vs ECS/EKS; cold starts and latency SLOs; provisioned concurrency if needed.
- **Data**: DynamoDB for predictable access patterns; RDS/Aurora for relational; design for quotas.
- **Security**: IAM least privilege; KMS; VPC endpoints; private subnets.

### Kubernetes
- **Probes**: Liveness kills stuck pods; readiness gates traffic; start-up probes for slow boots.
- **Autoscaling**: HPA on custom metrics; KEDA for queue depth.
- **Networking**: mTLS with mesh; restrict egress; resource requests/limits tuned.

### CI/CD
- **Pipelines**: Fail fast, parallel stages, artifacts versioned; SBOM and signing.
- **Rollouts**: Canary with metric checks; automated rollback on SLO breach.

### GenAI
- **RAG**: Split (chunk), embed, store vectors; retrieve top-k, ground prompts; cache embeddings.
- **Evals**: Golden sets and automatic scoring (BLEU/ROUGE/semantic similarity); human review for safety.
- **Safety**: PII redaction, prompt hardening, output constraints; model/route fallbacks.

## Coding interview tasks (with examples and acceptance criteria)

### 1) Concurrency-limited task runner
- **Goal**: Implement `runWithConcurrency(tasks: (() => Promise<T>)[], limit: number): Promise<T[]>` preserving order.
- **Example**: 10 tasks, `limit=3` → no more than 3 concurrent; output is in original order.
- **Acceptance**:
  - Never exceeds `limit` concurrent executions.
  - Preserves output order.
  - Propagates first error (configurable) and cancels remaining via `AbortController`.

### 2) Sliding-window rate limiter (Redis)
- **Goal**: Middleware limiting requests per user/IP to N per window with sliding precision.
- **Example**: 100 req/1m; bursts allowed up to N, distributed fairly.
- **Acceptance**:
  - O(1) or O(log n) per request using ZSET or Lua script.
  - Works under multi-instance cluster.
  - Includes retry-after headers and instrumentation.

### 3) Retry with exponential backoff + jitter
- **Goal**: `retry(fn, {retries, min, max, factor, jitter})` for transient errors.
- **Example**: Retry on 5xx/ENOTFOUND; stop on 4xx/non-transient.
- **Acceptance**:
  - Full jitter; caps at max; respects AbortSignal.
  - Emits metrics (attempts, latency, final outcome).

### 4) Streaming CSV → NDJSON transform
- **Goal**: Transform stream that converts CSV rows to JSON objects line-by-line with backpressure.
- **Example**: 5GB CSV processed with <100MB memory, with headers mapping.
- **Acceptance**:
  - Handles quoted fields/newlines; emits parse errors with row numbers.
  - Works in `pipeline` with file and HTTP streams.

### 5) Graceful shutdown for HTTP + queue workers
- **Goal**: On SIGTERM, stop accepting new requests, finish in-flight, drain queues, close pools.
- **Acceptance**:
  - Terminates within timeout; exposes `/healthz` readiness flip.
  - No requests dropped under normal termination; idempotent.

### 6) Idempotent POST endpoint with dedupe
- **Goal**: Implement idempotency keys using Redis with TTL.
- **Example**: Duplicate POST with same key returns original result without re-executing side effects.
- **Acceptance**:
  - Prevents duplicate external calls; handles concurrent duplicates safely.

### 7) Kafka consumer with at-least-once + dedupe
- **Goal**: Process messages idempotently and commit offsets after successful processing.
- **Acceptance**:
  - Idempotency store (e.g., Redis/DB unique constraint) prevents reprocessing.
  - Metrics for lag and processing latency; safe shutdown.

### 8) RAG microservice skeleton (GenAI)
- **Goal**: Ingest docs, chunk+embed, store vectors; query retrieves top-k chunks and composes grounded answer.
- **Acceptance**:
  - Deterministic chunking; embedding caching; trace spans over steps.
  - Redacts PII; rate limits per API key; logs token usage.
