<!-- title:Microservice Architecture Patterns -->

<!-- Card Start -->
### Front
What is the Microservices architectural style? (Give core defining traits)

### Back
**Answer**: An approach that structures an application as a suite of small, independently deployable services aligned to business capabilities.

**Key Traits**:
- Independently deployable & scalable
- Loosely coupled via well-defined APIs
- Organized around business capabilities
- Owned by small, autonomous teams
- Polyglot tech & data (where justified)
- Automated CI/CD & observability essential
<!-- Card End -->

<!-- Card Start -->
### Front
Compare **Cache-Aside** vs **Read-Through** caching patterns: how they differ and when to use each.

### Back
**Answer**: Both patterns improve read performance but differ in _who loads the cache_ and _how cache population is handled_.

**Cache-Aside (Lazy Loading)**
- Application checks the cache; on a miss, the app reads from the DB, then writes to the cache.
- Pros: Simple to implement, gives application control over cache lifecycle and eviction.
- Cons: App must implement loader logic; increased risk of cache stampede; more application complexity.

**Read-Through**
- Cache (or cache client/library) transparently loads data from the DB on a miss and returns it to the app.
- Pros: Simplifies application code; centralizes caching logic and can implement optimized batching/coalescing.
- Cons: Makes cache layer more complex and may obscure DB load; can hide latency/costs from app developers.

**When to choose**
- Use Cache-Aside when you need fine-grained app control (complex domain logic or conditional caching).
- Use Read-Through when you prefer the cache to manage loading and want simpler app logic.

**Mitigations for both**: TTLs, negative caching, request coalescing/singleflight, and rate limiting to avoid stampedes and protect the DB.


**Quick summary**

**Cache-Aside** (lazy loading): the application (caller) is responsible for checking the cache, loading from the DB on a miss, and populating the cache.

**Read-Through**: the cache layer or client transparently loads from the DB on a miss; the application simply asks the cache for the data and the cache handles population.
**Behavioral differences (practical)**

**Responsibility**
- Cache-Aside: app implements the load-and-populate logic.
- Read-Through: cache (or cache client/library/proxy) implements load-and-populate logic.

**Visibility**
- Cache-Aside: app sees DB load and can react (backoff, degrade logic).
- Read-Through: DB loads are hidden behind cache, simplifying app code but potentially obscuring DB load/cost.

**Complexity**
- Cache-Aside: slightly more app complexity but maximum control for conditional caching, complex reads, or telemetry.
- Read-Through: simpler app code, more complexity in cache infrastructure.

**Optimizations**
- Read-Through caches can implement batching, coalescing, or prefetching centrally.
- Cache-Aside requires the app to implement coalescing (singleflight, locks) to avoid stampedes.

**Writes & invalidation**
- Cache-Aside: app must explicitly update/invalidate cache on writes (or use TTLs).
- Read-Through: still needs invalidation on writes; some cache systems support write-through or write-back semantics for writes.


<!-- Card End -->

<!-- Card Start -->
### Front
Which principle of microservices encourages services to be owned by small, autonomous teams?

- A. Conway's Segmentation
- B. Two-Pizza Team Ownership
- C. Horizontal Sharding Principle
- D. Vertical Scaling Maximization

### Back
**Correct Answer**: B

**Explanation**: Amazon's "two-pizza team" concept influences microservice team sizing—small, autonomous, independent decision-making aligned to service ownership.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the API Gateway pattern.

### Back
**Answer**: A single entry point that fronts multiple backend services, handling cross-cutting concerns.

**Common Responsibilities**:
- Request routing & aggregation
- Authentication / authorization
- Rate limiting / throttling
- Protocol translation (HTTP <-> gRPC, WebSocket)
- Caching, compression, response shaping
- Canary & version routing

**Related**: Backend for Frontend (BFF) focuses on per-client tailoring; API Gateway is broader & general-purpose.
<!-- Card End -->

<!-- Card Start -->
### Front
API Gateway vs Backend for Frontend (BFF): what's the difference?

### Back
**Answer**:
- **API Gateway**: Single, generalized entry point for many clients; centralizes cross-cutting concerns.
- **BFF**: Specialized gateway per client type (web, mobile) optimizing payloads & workflows.

**When to use BFF**: Divergent client needs, performance tuning, tailored composition.
**Risk**: Proliferation of too many BFFs → maintenance overhead.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern aggregates responses from multiple services and can implement rate limiting?

- A. Service Registry
- B. API Gateway
- C. Circuit Breaker
- D. Bulkhead

### Back
**Correct Answer**: B

**Explanation**: API Gateway centralizes request routing, aggregation, rate limiting, and auth.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Circuit Breaker pattern.

### Back
**Answer**: A resiliency pattern that prevents an application from repeatedly invoking a failing remote call by "opening" after failures until recovery.

**States**: Closed (normal), Open (short-circuit), Half-Open (probe limited calls).

**Benefits**: Faster failure, protects resources, avoids cascading outages.

**Often paired with**: Timeouts, retries with backoff, bulkheads, fallback logic.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern isolates resource pools (e.g., thread pools) to contain failures within one service interaction?

- A. Bulkhead
- B. Circuit Breaker
- C. Service Mesh
- D. Saga

### Back
**Correct Answer**: A
 
**Explanation**: The **Bulkhead** pattern isolates capacity so failures or slowdowns in one dependency cannot consume all resources and bring down the entire application.

Key ideas:
- Partition resources (thread pools, connection pools, queues, or containers) by downstream dependency, customer, or capability.
- Bound concurrency and queue lengths for each partition so saturation causes localized rejections instead of total outage.

Concrete examples:
- Use a dedicated executor/thread-pool for calls to the payment service; if payment is slow, only those tasks queue or fail while other functionality (e.g., browsing) remains available.
- Create separate connection pools or circuit-limited clients per downstream DB or API.
- Run critical components in separate pods/namespaces with resource quotas so one noisy service cannot exhaust node resources.

Implementation tactics:
- Bounded queues + rejection handlers (return fallback or 503)
- Separate connection/thread pools per dependency
- Kubernetes resource quotas & limits, Pod priority classes
- Adaptive bulkheads: dynamically resize quotas based on load/health metrics

Trade-offs and pitfalls:
- Can cause under-utilization if partitions are sized too conservatively.
- Sizing is hard: monitor and iterate (use metrics for queue length, rejection rates, latency).
- Combined with poor retry logic, rejections can be amplified; use retry budgets and backoff.

Related patterns:
- **Circuit Breaker**: prevents repeated calls to a failing dependency; bulkhead limits resource impact when calls are attempted.
- **Backpressure / Load Shedding**: intentionally drop or defer requests when overloaded; bulkhead provides a structural way to shed load in a scoped manner.

What to monitor:
- Thread/pool utilization, queue lengths, rejection/error rates per partition, latency, and SLO violations.

When to use:
- When a few failing or slow dependencies should not degrade the whole service; in high-concurrency services where resource isolation improves availability.
<!-- Card End -->

<!-- Card Start -->
### Front
Bulkhead vs Circuit Breaker: primary distinction?

### Back
**Answer**:
- **Bulkhead**: Isolation of resource pools to limit blast radius.
- **Circuit Breaker**: Monitoring call failures; stops calling failing dependency to allow recovery.

They are complementary: bulkhead limits impact; breaker prevents repeated failing calls.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Strangler Fig pattern.

### Back
**Answer**: An incremental migration approach where new microservices gradually replace pieces of a legacy monolith by routing specific functionality to new services until the old is decommissioned.

**Key Steps**: Identify boundary → redirect subset of traffic → implement service → expand scope → retire legacy code.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern is best suited to gradually replace a legacy monolith feature-by-feature?

- A. Event Sourcing
- B. Strangler Fig
- C. Saga
- D. Sidecar

### Back
**Correct Answer**: B

**Explanation**: Strangler Fig lets you incrementally route functionality to new components, enabling staged migration.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Event Sourcing pattern.

### Back
**Answer**: Store state as an append-only sequence of domain events rather than current state snapshots.

**Rebuild State**: Replay events to reconstruct aggregates.

**Benefits**: Auditability, temporal queries, easier retroactive projections.

**Challenges**: Evolving event schemas, eventual consistency, larger storage, replay cost.

**Often paired with**: CQRS for read model projections.
<!-- Card End -->

<!-- Card Start -->
### Front
What problem does the Transactional Outbox pattern solve?

### Back
**Answer**: Ensures reliable publication of messages/events when updating a database and emitting an integration event, avoiding dual-write inconsistency.

**Mechanism**: Write domain change + outbox record in same DB transaction → background publisher reads outbox table → publishes to broker → marks sent.
**Prevents**: Lost events on crashes between DB write and message publish.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern prevents dual-write inconsistencies between a database update and event broker publish?

- A. CQRS
- B. Transactional Outbox
- C. Saga
- D. Event Sourcing

### Back
**Correct Answer**: B

**Explanation**: Transactional Outbox couples DB write + outbox entry atomically; async relay publishes reliably.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Saga pattern.

### Back
**Answer**: A sequence of local transactions across services coordinated via events or a central orchestrator, with compensating actions to maintain consistency without distributed 2PC.
 
**Key**: Eventually consistent business process; rollback via compensating actions rather than a global two-phase commit (2PC) lock-based protocol.

**Why avoid 2PC in microservices**: 2PC enforces strong distributed atomicity but requires distributed locking and coordination across services/databases. This introduces availability and performance risks (blocking during coordinator failures), tight coupling between services, and operational complexity—making sagas (eventual consistency + compensations) the preferred pattern in many microservice architectures.
<!-- Card End -->

<!-- Card Start -->
### Front
What is Two-Phase Commit (2PC) and why is it often avoided in microservices?

### Back
**Answer**: Two-Phase Commit is a distributed transaction protocol that ensures atomic commit across multiple participants using a coordinator.

**Phases**:
- **Phase 1 — Prepare**: Coordinator asks each participant to prepare (can you commit?) and participants reply with yes (prepared) or no (abort).
- **Phase 2 — Commit/Rollback**: If all participants vote yes, the coordinator sends a commit; otherwise it sends a rollback.

**Properties & Drawbacks**:
- Guarantees atomicity (either all commit or none) but at the cost of distributed locking and blocking during coordinator or participant failures.
- Participants hold locks/resources during the protocol increasing contention.
- Coordinator failure requires complex recovery protocols and can reduce availability.
- Works best in single-database or tightly-coupled environments; poorly suited for polyglot microservices.

**Alternatives in microservices**:
- **Saga**: Compose local transactions with compensations for eventual consistency.
- **Transactional Outbox / CDC**: Ensure reliable messaging and eventual reconciliation without global locks.

**When 2PC may be acceptable**: In constrained, tightly-controlled environments where availability trade-offs are understood, or when using distributed databases that provide transactional guarantees across shards.
<!-- Card End -->

<!-- Card Start -->
### Front
Saga Orchestration vs Choreography: difference?

### Back
**Answer**:
- **Orchestration**: Central controller commands each step; simpler visibility, potential central bottleneck.
- **Choreography**: Services react to events; more decoupled, harder to trace, risk of emergent complexity.

**Guideline**: Start with choreography for simple flows; move to orchestration when complexity/visibility issues grow.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern coordinates a multi-step business transaction without a distributed lock?

- A. 2PC
- B. Saga
- C. Bulkhead
- D. Strangler Fig

### Back
**Correct Answer**: B

**Explanation**: Saga uses compensating local transactions to maintain eventual consistency.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the CQRS pattern.

### Back
**Answer**: Segregates write (command) models from read (query) models to optimize independently for domain consistency vs query performance.

**Benefits**: Scalable reads, tailored projections, simpler write model.
**Trade-offs**: Increased complexity, eventual consistency between models.
**Often paired with**: Event Sourcing to build projections.
<!-- Card End -->

<!-- Card Start -->
### Front
CQRS vs Event Sourcing: relationship?

### Back
**Answer**: Orthogonal patterns; Event Sourcing stores events, CQRS separates read/write models. Often, events feed CQRS projections, but you can use either independently.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Database per Service pattern.

### Back
**Answer**: Each service owns a private data store (schema or DB instance) to enforce loose coupling and independent scaling.

**Benefits**: Autonomy, isolated schema evolution.
**Challenges**: Enforcing referential integrity across services, distributed transactions, duplicated reference data.
**Mitigation**: Saga, domain events, API composition.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern supports service autonomy by eliminating shared database coupling?

- A. Sidecar
- B. Database per Service
- C. Service Discovery
- D. API Gateway

### Back
**Correct Answer**: B

**Explanation**: Database per Service isolates persistence per bounded context to reduce coupling.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Service Discovery / Service Registry pattern.

### Back
**Answer**: Dynamic mechanism where services register their network locations; clients or intermediaries query registry to resolve endpoints.

**Types**:
- Client-side discovery (client selects instance)
- Server-side discovery (load balancer routes request)
**Examples**: Consul, Eureka, etcd, Kubernetes API/Endpoints.
<!-- Card End -->

<!-- Card Start -->
### Front
Client-side vs Server-side service discovery difference?

### Back
**Answer**:
- **Client-side**: Client fetches registry list and load balances itself; fewer hops but more client logic.
- **Server-side**: Client calls a stable endpoint; load balancer / proxy selects instance.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Sidecar pattern.

### Back
**Answer**: Deploy an auxiliary container/process beside the main service in the same host/pod to abstract infrastructure capabilities (e.g., logging, metrics, proxying, TLS, config reload).

**Benefits**: Language-agnostic, reuse infra features.
**Examples**: Envoy sidecar in service mesh, log forwarders, Vault agents.
<!-- Card End -->

<!-- Card Start -->
### Front
Service Mesh vs Sidecar: relationship?

### Back
**Answer**: A service mesh leverages a fleet of sidecar proxies to provide uniform networking (mTLS, retries, routing, observability) through a control plane. Sidecar is the deployment pattern enabling it.


<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern introduces uniform cross-cutting networking features via sidecar proxies?

- A. Bulkhead
- B. Service Mesh
- C. BFF
- D. Strangler Fig

### Back
**Correct Answer**: B

**Explanation**: Service mesh standardizes networking behavior using sidecar data plane + control plane.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe Blue-Green deployment.

### Back
**Answer**: Maintain two production environments: Blue (active) and Green (idle). Deploy new version to idle, run tests, then switch traffic atomically.

**Benefits**: Fast rollback (switch back), minimal downtime.
**Costs**: Double infra during deployment window.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe Canary release.

### Back
**Answer**: Gradually route a small percentage of traffic to the new version, monitor metrics/errors, progressively increase if healthy.

**Benefits**: Early anomaly detection with limited blast radius.
**Needs**: Fine-grained traffic routing + observability.
<!-- Card End -->

<!-- Card Start -->
### Front
Blue-Green vs Canary: key difference?

### Back
**Answer**:
- **Blue-Green**: Two full environments; traffic switch is near-instant cutover.
- **Canary**: Incremental traffic shifting; progressive confidence building.

Often combined: Blue-Green for environment prep, Canary for phased exposure.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe Rolling Update.

### Back
**Answer**: Update a fleet incrementally by replacing instances one (or a batch) at a time while keeping service available.

**Pros**: Lower infra cost than Blue-Green.
**Cons**: Harder instant rollback; mixed version state.
<!-- Card End -->

<!-- Card Start -->
### Front
Which deployment approach maintains two parallel environments and flips traffic?

- A. Rolling Update
- B. Blue-Green
- C. Canary
- D. A/B Experiment

### Back
**Correct Answer**: B

**Explanation**: Blue-Green uses dual environments for rapid cutover & rollback.
<!-- Card End -->

<!-- Card Start -->
### Front
Horizontal vs Vertical scaling: difference?

### Back
**Answer**:
- **Horizontal (scale-out)**: Add more instances; improves redundancy & elasticity.
- **Vertical (scale-up)**: Add resources (CPU/RAM) to existing instance; simpler but limited & single point of failure persists.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe Load Balancing in microservices.

### Back
**Answer**: Distributes incoming traffic across multiple service instances to improve availability, performance, and fault tolerance.

**Strategies**: Round-robin, least-connections, weighted, request hashing.
**Layers**: L4 (transport) vs L7 (application-aware).
<!-- Card End -->

<!-- Card Start -->
### Front
Which technique improves resilience by spreading traffic across multiple instances?

- A. Event Sourcing
- B. Load Balancing
- C. Strangler Fig
- D. Transactional Outbox

### Back
**Correct Answer**: B

**Explanation**: Load balancing distributes requests to reduce overload of any single instance.
<!-- Card End -->

<!-- Card Start -->
### Front
Observability pillars often emphasized in microservices?

### Back
**Answer**: Logs, Metrics, Traces (and sometimes Events). Together support root cause analysis & performance insight.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern separates read and write models to optimize for performance and complexity boundaries?

- A. CQRS
- B. Saga
- C. Sidecar
- D. BFF

### Back
**Correct Answer**: A

**Explanation**: CQRS partitions command and query responsibilities.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Backend for Frontend (BFF) pattern.

### Back
**Answer**: A dedicated API layer per client experience (web, mobile, IoT) to tailor endpoints, aggregate data, reduce chattiness, and adapt formats.

**Benefits**: Optimized payloads, UI-driven iteration.
**Risk**: Fragmentation if not curated.
<!-- Card End -->

<!-- Card Start -->
### Front
When to avoid premature microservice decomposition?

### Back
**Answer**: Early-stage products with unclear domain boundaries; when operational maturity (monitoring, deployment automation) is insufficient; when inter-service latency outweighs modular benefits; if monolith change cadence is not the bottleneck.
<!-- Card End -->

<!-- Card Start -->
### Front
List two common pitfalls of microservices adoption.

### Back
**Answer**:
- Distributed monolith (tight coupling via synchronous calls)
- Excessive chatty communication increasing latency
- Lack of centralized observability
- Inconsistent contract/version governance
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the API Composition pattern (a.k.a. Aggregator Service) and how it differs from using CQRS projections.

### Back
**Answer**: API Composition aggregates data from multiple service APIs at request time to build a composite response. CQRS projections precompute denormalized read models asynchronously.

**Differences**:
- Composition: On-demand aggregation; runtime latency cost.
- Projection: Pre-built read model; faster queries; eventual consistency.
**Use Composition**: Low query volume, dynamic fields, rapid iteration.
**Use Projection**: High read throughput, complex joins, predictable shapes.
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach precomputes denormalized views to optimize query latency?

- A. API Composition
- B. Circuit Breaker
- C. CQRS Projection
- D. Strangler Fig

### Back
**Correct Answer**: C

**Explanation**: CQRS read side uses projections/materialized views for low-latency queries.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the Anti-Corruption Layer (ACL) pattern in microservices.

### Back
**Answer**: A translation layer that shields a service/domain model from legacy or external model semantics by mapping inbound/outbound representations, preventing model pollution.

**Benefits**: Preserves ubiquitous language, isolates change.
**Techniques**: Adapters, facades, mapping DTOs, protocol translation.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern protects your domain model from leaking legacy concepts?

- A. Anti-Corruption Layer
- B. Bulkhead
- C. Saga
- D. Sidecar

### Back
**Correct Answer**: A

**Explanation**: ACL translates & isolates models to avoid semantic bleed-through.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe Idempotency Keys and why they matter in distributed systems.

### Back
**Answer**: Client-supplied unique keys (e.g., UUID) included with mutation requests allowing the server to detect duplicates and return the original result rather than reapplying side effects.

**Benefits**: Safe retries, resilience to network timeouts, prevents double charges/orders.
**Implementation**: Store key + result hash / status with expiry.
<!-- Card End -->

<!-- Card Start -->
### Front
Idempotent Consumer pattern: goal?

### Back
**Answer**: Ensures a message handler can process duplicate deliveries without producing duplicate side effects (e.g., using dedup store, sequence numbers, natural keys, conditional writes).
<!-- Card End -->

<!-- Card Start -->
### Front
Which technique helps ensure retrying a POST request doesn\'t create duplicate orders?

- A. Event Sourcing
- B. Idempotency Key
- C. Load Balancer Hashing
- D. Blue-Green Deployment

### Back
**Correct Answer**: B

**Explanation**: Idempotency keys correlate duplicate submissions to a single effect.
<!-- Card End -->

<!-- Card Start -->
### Front
Retry pattern: core best practices?

### Back
**Answer**:
- Use bounded retries (limit attempts)
- Apply exponential backoff + jitter
- Combine with circuit breaker & timeout
- Make operations idempotent
- Differentiate transient vs fatal errors
<!-- Card End -->

<!-- Card Start -->
### Front
Exponential Backoff with Jitter: purpose of jitter?

### Back
**Answer**: Randomizes retry intervals to avoid thundering herd synchronization where many clients retry simultaneously causing spikes.
<!-- Card End -->

<!-- Card Start -->
### Front
Which answer lists a recommended resilience trio?

- A. Canary, Blue-Green, Monolith
- B. Retry, Timeout, Circuit Breaker
- C. Load Balancer, CDN, ORM
- D. CQRS, Event Sourcing, CSS

### Back
**Correct Answer**: B

**Explanation**: These three control latency, failure detection, and repeated failure propagation.
<!-- Card End -->

<!-- Card Start -->
### Front
Rate Limiting algorithms: name three common strategies.

### Back
**Answer**: Token Bucket, Leaky Bucket, Fixed Window (or Sliding Window). Each balances burst handling vs fairness.
<!-- Card End -->

<!-- Card Start -->
### Front
Which algorithm allows short bursts while enforcing an average rate via token replenishment?

- A. Fixed Window Counter
- B. Token Bucket
- C. Round Robin
- D. Leaky Funnel

### Back
**Correct Answer**: B

**Explanation**: Token Bucket accumulates tokens allowing bursts up to bucket capacity.
<!-- Card End -->

<!-- Card Start -->
### Front
Compare Token Bucket vs Leaky Bucket rate-limiting algorithms: how they behave and when to use each.

### Back
**Answer**: Both control rate but differ in burst handling and enforcement model.

**Token Bucket**
- Allows bursts up to the token bucket capacity; tokens accumulate at a steady rate.
- Behavior: a request consumes tokens; if tokens available, request passes immediately (supporting bursts); if not, request is throttled or delayed.
- Use when you want to allow short bursts while enforcing a long-term average rate (e.g., user-facing services allowing bursts).

**Leaky Bucket**
- Shapes traffic into a steady outflow (fixed drain rate); excess arrivals are queued or dropped.
- Behavior: incoming requests enter a queue; they are processed at a constant rate; bursts are smoothed; if the queue is full, new requests are dropped.
- Use when you need to smooth bursts into a constant processing rate (e.g., protecting downstream systems with fixed capacity).

**Practical differences & trade-offs**
- Burst handling: Token Bucket permits bursts (up to capacity); Leaky Bucket smooths bursts.
- Implementation: Token Bucket is easier for per-client burst allowances; Leaky Bucket is conceptually a queue with fixed drain.
- Fairness & predictability: Leaky Bucket enforces steadier output; Token Bucket provides better responsiveness for bursty workloads.

**When to choose**
- Choose Token Bucket when clients need occasional burstiness but the long-term average must be bounded.
- Choose Leaky Bucket when you must strictly smooth traffic to protect fixed-capacity downstream services.
<!-- Card End -->

<!-- Card Start -->
### Front
Distributed Tracing: purpose & core identifiers.

### Back
**Answer**: Observability technique to follow a request across services.

**Identifiers**: Trace ID (end-to-end), Span ID (individual operation), Parent Span ID.

**Benefits**: Latency breakdown, dependency mapping, faster root cause analysis.
<!-- Card End -->

<!-- Card Start -->
### Front
Describe the difference between Shadow Traffic and Canary Release.

### Back
**Answer**:

- **Shadow Traffic**: Duplicate live production requests and send copies to new version (responses ignored) for evaluation.
- **Canary**: Route a small percentage of *real* user traffic whose responses count.
**Goal**: Shadow validates behavior safely; canary validates under partial real load.
<!-- Card End -->

<!-- Card Start -->
### Front
Dark Launch vs Feature Flag difference?

### Back
**Answer**:
- **Dark Launch**: Deploy feature in production executing internally but hidden from users; collects performance metrics.
- **Feature Flag**: Config-based toggle controlling exposure per user/segment; can disable quickly.
Often combined: dark launch first, then gradually enable via flags.
<!-- Card End -->

<!-- Card Start -->
### Front
Health Probes: distinguish Liveness vs Readiness.

### Back
**Answer**:
- **Liveness**: Is process alive? If failing → restart.
- **Readiness**: Is instance prepared to serve traffic? If failing → remove from endpoints.
Startup probes (optional) defer liveness until init completes.
<!-- Card End -->

<!-- Card Start -->
### Front
Graceful Shutdown steps (containerized microservice)?

### Back
**Answer**:
1. Receive termination signal (SIGTERM)
2. Stop accepting new requests (drain / deregister)
3. Finish in-flight work with timeout
4. Flush buffers (logs, metrics)
5. Close connections & exit cleanly
<!-- Card End -->

<!-- Card Start -->
### Front
Backpressure vs Load Shedding?

### Back
**Answer**:
- **Backpressure**: Signal upstream to slow input (e.g., queue size, reactive streams demand).
- **Load Shedding**: Proactively drop work when over capacity to protect core latency (e.g., reject, 503).
Use both to maintain SLOs.
<!-- Card End -->

<!-- Card Start -->
### Front
Which concept intentionally drops lower-priority requests to preserve core service health under overload?

- A. Backpressure
- B. Load Shedding
- C. Blue-Green
- D. Saga

### Back
**Correct Answer**: B

**Explanation**: Load shedding discards excess work to maintain performance.
<!-- Card End -->

<!-- Card Start -->
### Front
Secrets Management: best practices summary.

### Back
**Answer**:
- External secret store (e.g., Vault, AWS Secrets Manager)
- Short-lived credentials (rotate)
- Encrypt at rest + in transit (mTLS/TLS)
- Avoid embedding secrets in images
- Principle of least privilege (scoped policies)
<!-- Card End -->

<!-- Card Start -->
### Front
Change Data Capture (CDC) vs Transactional Outbox difference?

### Back
**Answer**:
- **CDC**: Observes DB log to emit change events (low app code change, can be noisy).
- **Outbox**: App writes explicit event records in same transaction (more control, explicit schema).
Use CDC for legacy DB integration; Outbox for explicit domain event intent.
<!-- Card End -->

<!-- Card Start -->
### Front
Materialized View pattern in microservices: purpose?

### Back
**Answer**: Precomputed, query-optimized snapshot of data (often from events or CDC) enabling fast reads and reduced join complexity at query time.
<!-- Card End -->

<!-- Card Start -->
### Front
Which pattern relies on append-only commit log to rebuild read models?

- A. Saga
- B. Event Sourcing
- C. Bulkhead
- D. BFF

### Back
**Correct Answer**: B

**Explanation**: Event Sourcing stores domain events forming a log for replay.
<!-- Card End -->

<!-- Card Start -->
### Front
API Versioning strategies (list two) and trade-offs.

### Back
**Answer**:
- URI versioning (/v1/) – simple caching; noisy URL.
- Header versioning – cleaner URLs; needs client tooling.
- Media type / accept header – fine-grained; complexity.
- Semantic versioned resources – more nuance; governance overhead.
<!-- Card End -->

<!-- Card Start -->
### Front
Consumer-Driven Contract Testing purpose?

### Back
**Answer**: Ensures provider APIs meet consumer expectations by defining versioned contracts; detects breaking changes early and reduces integration environment dependency.
<!-- Card End -->

<!-- Card Start -->
### Front
Which practice helps prevent breaking API changes by formalizing expectations from each client?

- A. Dark Launching
- B. Consumer-Driven Contracts
- C. Canary Release
- D. Rolling Update

### Back
**Correct Answer**: B

**Explanation**: CDC tests capture each consumer's expectations as contracts.
<!-- Card End -->

<!-- Card Start -->
### Front
Zero Trust / mTLS in microservices: rationale?

### Back
**Answer**: Authenticate & encrypt every service-to-service call (no implicit trust on internal network) reducing lateral movement risk and ensuring confidentiality & integrity.
<!-- Card End -->

<!-- Card Start -->
### Front
What is the Cache-Aside (Lazy Loading) pattern: flow summary.

### Back
**Answer**:
1. App checks cache
2. If miss → load from DB
3. Populate cache
4. Return data
Eviction/invalidation critical to prevent stale reads.
<!-- Card End -->

<!-- Card Start -->
### Front
Which cache pattern loads data on demand and stores it after a miss?

- A. Write-Through
- B. Read-Through
- C. Write-Behind
- D. Cache-Aside

### Back
**Correct Answer**: D

**Explanation**: Cache-aside (lazy loading) fetches from source only on miss then populates cache.
<!-- Card End -->

<!-- Card Start -->
### Front
Common microservice anti-pattern: "Distributed Monolith" — describe it.

### Back
**Answer**: A system split into multiple deployable units that still require synchronized deployments due to tight coupling (shared DB schemas, chatty synchronous calls, cross-service transactions), losing benefits while adding complexity.
<!-- Card End -->

<!-- Card Start -->
### Front
Which issue arises when services must be deployed together due to shared database schemas?

- A. Event Storming
- B. Distributed Monolith
- C. Canary Drift
- D. Circuit Saturation

### Back
**Correct Answer**: B

**Explanation**: Tight coupling negates independent deployability.
<!-- Card End -->

<!-- Card Start -->
### Front
Bulkhead pattern implementation examples.

### Back
**Answer**:
- Separate connection pools per downstream
- Dedicated thread pools / executor per dependency
- Partitioned queues or shards
- Resource quotas at container level
<!-- Card End -->

<!-- Card Start -->
### Front
Timeout selection guidelines for remote calls?

### Back
**Answer**:
**Guidelines (practical recipe)**:

- Measure the target service's p95/p99 latency under normal load.
- Timeout = observed p99 latency * 1.5 (or p95 * 2) as a starting point, then tune.
- Ensure the timeout is shorter than the caller's overall SLA/deadline so callers can fail fast and recover.

**Connect vs Read/Write timeouts**:
- Use short connect timeouts (e.g., 200–500ms) to avoid slow handshakes.
- Use longer read/response timeouts based on p99 latency for the operation.

**Interaction with retries and circuit breakers**:
- Keep retries bounded and use exponential backoff + jitter.
- A too-long timeout multiplied by retries can exhaust capacity; use retry budgets.
- Combine timeouts with circuit breakers to stop repeated attempts to slow/unhealthy services.

**Examples**:
- If p99 = 300ms, start with timeout ≈ 300ms * 1.5 = 450ms.
- If caller SLA = 1s, ensure sum of retries/backoffs + timeout < 1s.

**Avoid**: infinite/very long default timeouts — they tie up threads/resources and increase cascading failures.
OpenTelemetry role in microservices observability?

### Back
**Answer**: Provides vendor-neutral APIs & SDKs to generate standardized traces, metrics, and logs exported to backends (Jaeger, Prometheus, etc.), reducing vendor lock-in.
<!-- Card End -->

<!-- Card Start -->
### Front
mTLS adds which primary security properties to service-to-service calls?

- A. Integrity & Authentication & Confidentiality
- B. Only Authorization
- C. Only Caching
- D. Only Compression

### Back
**Correct Answer**: A

**Explanation**: Mutual TLS authenticates both ends & encrypts channel ensuring integrity & confidentiality.
<!-- Card End -->

<!-- Card Start -->
### Front
Feature Flag Kill Switch: purpose?

### Back
**Answer**: Immediate disablement of a problematic feature without redeploying, minimizing user impact and rollback time.
<!-- Card End -->

<!-- Card Start -->
### Front
Which is NOT a typical rate limiting algorithm?

- A. Sliding Window Log
- B. Token Bucket
- C. Leaky Bucket
- D. Depth-First Search

### Back
**Correct Answer**: D

**Explanation**: DFS is a graph traversal algorithm, not used for rate limiting.
<!-- Card End -->



<!-- Card Start -->
### Front
Expand/Contract pattern for API or schema evolution: describe the approach.

### Back
**Answer**: Make changes in two phases to maintain backward compatibility. First, Expand: add new fields/endpoints while keeping old ones. Migrate clients. Then, Contract: remove deprecated parts after adoption.
.

**Detailed Explanation**:

- **Phase 1 — Expand (Add-Compat)**: Introduce new fields, endpoints, or event attributes in a fully backward-compatible way. Keep existing fields/behaviours unchanged so old clients continue to function. Examples:
	- Add a nullable column or optional JSON field to a response.
	- Add a new endpoint (e.g., /v2/resource) while leaving /v1/resource intact.
	- Emit additional event attributes while preserving prior event schema.

- **Migration tactics during Expand**:
	- Dual-read / dual-write: write to both old and new shapes while consumers migrate.
	- Use feature flags to enable server behaviour selectively for clients.
	- Provide adapters or ACLs to map new fields for legacy consumers.

- **Phase 2 — Contract (Remove-Compat)**: After a measured adoption window and when monitoring shows clients migrated, remove deprecated fields or endpoints.
	- Deprecation timeline: announce, monitor adoption metrics, and schedule removal.
	- Provide clear error messages and a migration guide.

- **Rollback & Safety**:
	- Keep the old behaviour behind a flag or in a compatibility layer until removal date.
	- If removal causes issues, re-enable compat quickly (feature flag or routing rollback).

- **Pitfalls & Considerations**:
	- Don't rename fields in-place without mapping — use new names and deprecate old ones.
	- Avoid breaking changes that require simultaneous deploys across many services (distributed monolith risk).
	- Plan data backfills or sidecar translations when adding non-nullable columns.

**Applies to**: APIs, events, DB schemas, message contracts.

**Tools & Practices**: Versioned contracts, feature flags, consumer-driven contracts, dual-write patterns, migration scripts, monitoring adoption metrics (client version usage), and clear deprecation notices.
<!-- Card End -->

<!-- Card Start -->
### Front
Which step comes first in the Expand/Contract approach?

- A. Contract (remove old fields)
- B. Fork (split repo)
- C. Freeze (block changes)
- D. Expand (add new fields)

### Back
**Correct Answer**: D

**Explanation**: Always add compatibly before removing to avoid breaking consumers.


<!-- Card End -->

<!-- Card Start -->
### Front
Database migration compatibility in microservices: safe change examples.

### Back
**Answer**:
- Add nullable column (backfill separately)
- Add new table referenced by code later
- Split column into two by writing both (dual-write)
- Avoid renames/drops until all services updated
- Use views to bridge old/new during transition
<!-- Card End -->

<!-- Card Start -->
### Front
Write-through vs Write-behind caching: contrast.

### Back
**Answer**:
- **Write-through**: Write goes to cache and DB synchronously; strong consistency, higher write latency.
- **Write-behind**: Write to cache; persist to DB asynchronously; lower latency, risk of loss/out-of-order.
Use behind with durable queues & idempotence.
<!-- Card End -->

<!-- Card Start -->
### Front
Which caching pattern persists to the database asynchronously for lower write latency?

- A. Cache-aside
- B. Read-through
- C. Write-behind
- D. Write-through

### Back
**Correct Answer**: C

**Explanation**: Write-behind defers DB persistence via async pipeline.
<!-- Card End -->

<!-- Card Start -->
### Front
Read-through cache pattern: define it.

### Back
**Answer**: Application queries the cache provider, which on a miss loads from the backing store automatically (cache sits in front of DB with loader integration).
<!-- Card End -->



<!-- Card Start -->
### Front
Hedged Requests pattern: purpose?

### Back
**Answer**: Reduce tail latency by sending a duplicate request to another replica after a small delay; take the first successful response, cancel the other.

**Trade-off**: Extra load; use sparingly and with budgets.
<!-- Card End -->

<!-- Card Start -->
### Front
Quorum Reads/Writes (N, R, W): what ensures strong consistency?

### Back
**Answer**: Choose read (R) and write (W) such that R + W > N, ensuring overlap between read and write sets.

**Example**: N=3, W=2, R=2.
<!-- Card End -->

<!-- Card Start -->
### Front
Outlier Ejection (in service mesh/load balancer): describe it.

### Back
**Answer**: Automatically detects and temporarily ejects unhealthy or slow endpoints from the load balancing pool based on error rates/latency to improve overall tail latency.
<!-- Card End -->

<!-- Card Start -->
### Front
Deadline vs Timeout propagation: difference?

### Back
**Answer**:
- **Timeout**: Duration allowed for an operation.
- **Deadline**: Absolute time by which the operation must complete; easier to propagate end-to-end across hops.
Propagate deadlines to prevent overwork and respect user SLAs.
<!-- Card End -->

<!-- Card Start -->
### Front
Retry Budget: what is it and why use it?

### Back
**Answer**: A cap (percentage of live traffic) on the number of retries allowed in a timeframe to prevent retries amplifying incidents; protects capacity during outages.
<!-- Card End -->

<!-- Card Start -->
### Front
Dead Letter Queue (DLQ): purpose in event streaming?

### Back
**Answer**: A holding queue for messages that repeatedly fail processing, enabling isolation, inspection, and remediation without blocking the main stream.
<!-- Card End -->

<!-- Card Start -->
### Front
Poison Message handling: recommended approach?

### Back
**Answer**: Detect repeated failures → move to DLQ with context → alert → analyze & fix producer/consumer → optionally reprocess with idempotency safeguards.
<!-- Card End -->

<!-- Card Start -->
### Front
Consistent Hashing usage in microservices?

### Back
**Answer**: Distribute keys/requests across shards/nodes so minimal remapping occurs when nodes join/leave; used in caches, sharded services, and partitioned message topics.
<!-- Card End -->

<!-- Card Start -->
### Front
Chaos Engineering: goal and a safe starting experiment.

### Back
**Answer**: Proactively test system resilience by injecting controlled failures in prod-like environments.

**Start with**: Kill one instance (pod) during business hours with on-call watching; verify auto-recovery, alerting, and SLOs.
<!-- Card End -->

<!-- Card Start -->
### Front
SLI vs SLO vs SLA: quick definitions.

### Back
**Answer**:
- **SLI**: Measured metric (e.g., availability %, latency p99)
- **SLO**: Target for SLI (e.g., 99.9% monthly availability)
- **SLA**: Contractual commitment with penalties based on SLOs
<!-- Card End -->

<!-- Card Start -->
### Front
Automated Canary Analysis (ACA): describe the concept.

### Back
**Answer**: Statistical comparison of metrics (error rate, latency, saturation) between canary and baseline to decide promotion/rollback automatically using score thresholds.
<!-- Card End -->
