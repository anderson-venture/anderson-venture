<h1 align="center">Hi 👋, I'm Pedro Lin</h1>
<h3 align="center">Full-Stack Engineer • PHP & Laravel on the back end, TypeScript & Node everywhere else</h3>

<p align="center">
  <img src="https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white" alt="PHP" />
  <img src="https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white" alt="Laravel" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
</p>

---

## About Me

I build web products end to end with **PHP, Laravel, TypeScript, and Node.js** — from the database
schema and queue workers up through the API and into the UI people actually click on.

Laravel is where I'm most at home: Eloquent models that stay thin, service classes that hold the
business logic, jobs and events for anything slow, and a test suite that makes refactoring boring.
On the TypeScript side I write Node services, real-time features, and typed front ends that share
contracts with the backend instead of guessing at them.

- 🔭 Working on **Laravel applications, REST/GraphQL APIs, and Node.js services**
- 🧰 Comfortable end to end: schema design → Laravel/Node API → TypeScript client → CI/CD
- ⚙️ Fond of strict types, `declare(strict_types=1)`, `"strict": true`, and code that reads like prose
- 📈 Chasing N+1 queries, slow jobs, and response times that make dashboards boring

---

## What I Work On

| Area | What that looks like in practice |
| --- | --- |
| **Laravel applications** | Modern Laravel 11/12, service + action classes, form requests, policies, Sanctum/Passport auth, multi-tenancy |
| **PHP** | PHP 8.3+ with enums, readonly properties, attributes, Composer packages, PSR standards, PHPStan at max level |
| **Node.js services** | Express / Fastify / NestJS APIs, WebSockets, background workers, CLI tooling |
| **APIs & contracts** | REST with OpenAPI, GraphQL (Lighthouse / Apollo), API resources, versioning, consistent error models |
| **Data** | MySQL / PostgreSQL schema design, indexing, Eloquent & Prisma, migrations, Redis caching |
| **Async & queues** | Laravel Horizon, queued jobs & events, BullMQ, retries, idempotency, failed-job handling |
| **Frontend** | TypeScript with Vue / React, Inertia.js, Livewire, Next.js, Tailwind CSS |
| **Platform** | Docker, Laravel Forge / Vapor, AWS, GitHub Actions, zero-downtime deploys |

---

## Laravel Toolbox

The shape most of my Laravel features end up in:

```php
final class PlaceOrderController
{
    public function __invoke(PlaceOrderRequest $request, PlaceOrder $placeOrder): OrderResource
    {
        $order = $placeOrder->handle(
            customer: $request->user(),
            items: $request->validated('items'),
        );

        return new OrderResource($order); // controllers stay thin — the action owns the logic
    }
}

final class PlaceOrder
{
    public function handle(User $customer, array $items): Order
    {
        return DB::transaction(function () use ($customer, $items) {
            $order = $customer->orders()->create(['status' => OrderStatus::Pending]);
            $order->items()->createMany($items);

            OrderPlaced::dispatch($order); // side effects go to the queue, not the request
            return $order;
        });
    }
}
```

- **Framework** — Laravel, Livewire, Inertia.js, Filament, Laravel Octane
- **Data access** — Eloquent, query builder, Scout, Redis, database transactions over hope
- **Queues & events** — Horizon, jobs, events/listeners, broadcasting with Reverb / Pusher
- **Testing** — Pest, PHPUnit, factories, `RefreshDatabase`, HTTP & feature tests, Dusk
- **Quality** — PHPStan / Larastan, Pint, Rector, Laravel Telescope

## Node & TypeScript Toolbox

```ts
const app = Fastify({ logger: true });

app.post<{ Body: CreateUser }>("/users", { schema: { body: CreateUserSchema } }, async (req, reply) => {
  const user = await users.create(req.body); // body is validated and typed before it gets here
  return reply.code(201).send(user);
});
```

- **Runtime / frameworks** — Node.js, Express, Fastify, NestJS
- **Types & validation** — TypeScript strict mode, Zod, tRPC, OpenAPI-generated clients
- **Data** — Prisma, Drizzle, TypeORM, BullMQ
- **Testing** — Vitest, Jest, Supertest, Playwright
- **Tooling** — ESLint, Prettier, pnpm, tsx, Vite

---

## Languages and Tools

<p align="left">
  <a href="https://www.php.net" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/php/php-original.svg" alt="php" width="40" height="40"/> </a>
  <a href="https://laravel.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/laravel/laravel-original.svg" alt="laravel" width="40" height="40"/> </a>
  <a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" alt="typescript" width="40" height="40"/> </a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a>
  <a href="https://nodejs.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a>
  <a href="https://expressjs.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/express/express-original-wordmark.svg" alt="express" width="40" height="40"/> </a>
  <a href="https://nestjs.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nestjs/nestjs-original.svg" alt="nestjs" width="40" height="40"/> </a>
  <a href="https://vuejs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vuejs/vuejs-original-wordmark.svg" alt="vuejs" width="40" height="40"/> </a>
  <a href="https://reactjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a>
  <a href="https://nextjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nextjs/nextjs-original.svg" alt="nextjs" width="40" height="40"/> </a>
  <a href="https://tailwindcss.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/tailwindcss/tailwindcss-original.svg" alt="tailwind" width="40" height="40"/> </a>
  <a href="https://graphql.org" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/graphql/graphql-icon.svg" alt="graphql" width="40" height="40"/> </a>
  <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a>
  <a href="https://www.postgresql.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a>
  <a href="https://redis.io" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original-wordmark.svg" alt="redis" width="40" height="40"/> </a>
  <a href="https://www.mongodb.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" width="40" height="40"/> </a>
  <a href="https://www.prisma.io/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/prisma/prisma-original.svg" alt="prisma" width="40" height="40"/> </a>
  <a href="https://www.docker.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a>
  <a href="https://aws.amazon.com" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/> </a>
  <a href="https://www.nginx.com" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/nginx/nginx-icon.svg" alt="nginx" width="40" height="40"/> </a>
  <a href="https://www.linux.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a>
  <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a>
</p>

---

## How I Build

- **Follow the framework.** Laravel conventions exist so the next developer knows where things live.
  Fight them only when there's a real reason.
- **Thin controllers, clear actions.** Validation in form requests, authorization in policies,
  business logic in single-purpose classes that are easy to test and reuse.
- **Types all the way down.** Strict PHP types and PHPStan on one side, strict TypeScript and Zod on
  the other — so the compiler catches what code review misses.
- **Design the contract first.** API resources, OpenAPI, or GraphQL schemas before implementation —
  the contract is what the front end and other teams depend on.
- **Push slow work to the queue.** Emails, webhooks, reports, and third-party calls belong in jobs
  with retries, not in the request cycle.
- **Test where it pays.** Pest feature tests for the happy and unhappy paths, Vitest for logic,
  Playwright for the flows that make money.

---

## Currently Exploring

- Laravel Octane and FrankenPHP for long-running, high-throughput PHP
- Laravel Reverb for first-party real-time features
- End-to-end type safety between Laravel back ends and TypeScript front ends
- Bun and Node's built-in test runner and TypeScript support
- AI-powered features in Laravel and Node apps

---

<p align="center"><i>Clean code, strong types, and shipping things people actually use.</i></p>
