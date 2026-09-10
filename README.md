<h1 align="center">Hi 👋, I'm Florin Matei</h1>
<h3 align="center">Full-Stack Engineer • Go on the back end, TypeScript on the front</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="Go" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes" />
</p>

---

## About Me

I build and operate backend systems in **Go** — HTTP and gRPC services, event-driven pipelines, and
the data layer underneath them — then carry the work all the way to a UI when the product needs one.

Most of my time goes into the parts nobody sees: request lifecycles, connection pools, retries and
timeouts, migrations, and the observability that tells you when any of it goes wrong. I like Go
because it keeps those parts explicit — small interfaces, obvious control flow, and a compiler that
turns most mistakes into build failures instead of pages at 3am.

- 🔭 Working on **Go microservices, gRPC + REST APIs, and cloud-native infrastructure**
- 🧰 Comfortable end to end: schema design → service → API contract → React/TypeScript client → CI/CD
- ⚙️ Fond of `context`, structured concurrency, table-driven tests, and code that reads like prose
- 📈 Chasing p99 latency, allocation counts, and clean pprof flame graphs

---

## What I Work On

| Area | What that looks like in practice |
| --- | --- |
| **Backend services** | Idiomatic Go services with `net/http` / chi / Echo, gRPC + protobuf, graceful shutdown, layered config |
| **APIs & contracts** | REST with OpenAPI, gRPC schemas, versioning strategy, pagination and error models clients can rely on |
| **Data** | PostgreSQL schema design, indexing and query plans, `pgx`/`sqlc`, migrations, Redis caching, transactional outbox |
| **Async & messaging** | Kafka / NATS / RabbitMQ consumers, at-least-once delivery, idempotency keys, retries and dead-letter handling |
| **Frontend** | React + TypeScript, typed API clients generated from the backend contract, pragmatic state management |
| **Platform** | Docker, Kubernetes, GitHub Actions, Terraform, blue/green and canary rollouts |
| **Observability** | OpenTelemetry traces, Prometheus metrics, structured logs with `slog`, dashboards and alerts that mean something |

---

## Go Toolbox

The shape most of my services end up in:

```go
type Server struct {
    cfg    Config
    db     *pgxpool.Pool
    cache  Cache // interface defined here, next to the consumer — not in the Redis package
    log    *slog.Logger
    tracer trace.Tracer
}

func (s *Server) Run(ctx context.Context) error {
    ctx, stop := signal.NotifyContext(ctx, os.Interrupt, syscall.SIGTERM)
    defer stop()

    g, ctx := errgroup.WithContext(ctx)
    g.Go(func() error { return s.serveHTTP(ctx) })
    g.Go(func() error { return s.consumeEvents(ctx) })
    return g.Wait() // one cancelled context takes the whole process down cleanly
}
```

- **Transport / routing** — `net/http`, chi, Echo, gRPC-Go, Connect
- **Data access** — `pgx`, `sqlc`, `database/sql`, golang-migrate, GORM when a team already lives in it
- **Concurrency** — `context`, `errgroup`, worker pools, semaphores, `sync` primitives over cleverness
- **Testing** — table-driven tests, `testify`, `httptest`, testcontainers, golden files, fuzzing for parsers
- **Ops** — `slog`, OpenTelemetry, Prometheus client, pprof, `go test -race`, `golangci-lint`

---

## Languages and Tools

<p align="left">
  <a href="https://go.dev" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/go/go-original-wordmark.svg" alt="go" width="45" height="45"/> </a>
  <a href="https://grpc.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/grpcio/grpcio-icon.svg" alt="grpc" width="40" height="40"/> </a>
  <a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="typescript" width="40" height="40"/> </a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a>
  <a href="https://reactjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a>
  <a href="https://nextjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nextjs/nextjs-original.svg" alt="nextjs" width="40" height="40"/> </a>
  <a href="https://nodejs.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a>
  <a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a>
  <a href="https://www.rust-lang.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/rust/rust-original.svg" alt="rust" width="40" height="40"/> </a>
  <a href="https://graphql.org" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/graphql/graphql-icon.svg" alt="graphql" width="40" height="40"/> </a>
  <a href="https://www.postgresql.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a>
  <a href="https://redis.io" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original-wordmark.svg" alt="redis" width="40" height="40"/> </a>
  <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" width="40" height="40"/> </a>
  <a href="https://kafka.apache.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/apache_kafka/apache_kafka-icon.svg" alt="kafka" width="40" height="40"/> </a>
  <a href="https://nats.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/nats_io/nats_io-icon.svg" alt="nats" width="40" height="40"/> </a>
  <a href="https://www.rabbitmq.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/rabbitmq/rabbitmq-icon.svg" alt="rabbitmq" width="40" height="40"/> </a>
  <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a>
  <a href="https://kubernetes.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40"/> </a>
  <a href="https://www.terraform.io/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/terraformio/terraformio-icon.svg" alt="terraform" width="40" height="40"/> </a>
  <a href="https://aws.amazon.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/> </a>
  <a href="https://cloud.google.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/google_cloud/google_cloud-icon.svg" alt="gcp" width="40" height="40"/> </a>
  <a href="https://prometheus.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/prometheus/prometheus-icon.svg" alt="prometheus" width="40" height="40"/> </a>
  <a href="https://grafana.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/grafana/grafana-icon.svg" alt="grafana" width="40" height="40"/> </a>
  <a href="https://opentelemetry.io" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opentelemetryio/opentelemetryio-icon.svg" alt="opentelemetry" width="40" height="40"/> </a>
  <a href="https://www.nginx.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/nginx/nginx-icon.svg" alt="nginx" width="40" height="40"/> </a>
  <a href="https://www.linux.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a>
  <a href="https://www.gnu.org/software/bash/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/> </a>
  <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a>
</p>

---

## How I Build

- **Boring beats clever.** A service a new teammate can read top to bottom beats a framework that
  saves twenty lines. In Go, verbosity is a feature.
- **Errors are values, so handle them.** Wrap with context, never swallow, let the caller decide.
  Every ignored `err` becomes an incident report eventually.
- **Design the contract first.** OpenAPI or protobuf before implementation — the schema is the part
  other teams actually depend on.
- **Make it observable before you make it fast.** Traces and metrics turn performance work from
  guesswork into arithmetic.
- **Test where it pays.** Table-driven unit tests for logic, testcontainers for the data layer, a thin
  smoke suite in CI. Coverage percentage is not the goal.
- **Ship in small pieces.** Feature flags, backwards-compatible migrations, reversible deploys.

---

## Currently Exploring

- Generics and range-over-func iterators, and where they genuinely simplify an API
- Profile-guided optimization and squeezing the last few percent out of hot paths
- Event sourcing and CQRS without the accidental complexity
- WebAssembly targets for sharing validation logic between Go services and the browser
- eBPF-based observability for the things tracing can't reach

---

<p align="center"><i>Simplicity is a feature. Ship small, observe everything, delete more than you add.</i></p>
