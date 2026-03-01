Here is the **complete .NET Learning Planner** with **Concepts + Scenario-Based Questions** for every topic, structured from **Basics → Intermediate → Advanced** across all modules.

---

# 🗓️ .NET Developer Master Planner — 2026
## Concepts + Scenario-Based Questions | Basics → Advanced

---

# 📦 MODULE 1: C# Language Fundamentals

---

## 🟢 BASICS

### 📘 Concept 1: Value Types vs Reference Types
| | |
|---|---|
| **What to Learn** | `int`, `struct`, `enum` vs `class`, `string`, arrays. Stack vs Heap memory allocation. `null` behavior differences. |
| **Key Topics** | Boxing/Unboxing, `default` keyword, `nullable<T>` (`int?`), `==` vs `.Equals()` |

> 🎯 **Scenario:** A junior dev stores a `Point` struct in an `object` variable and passes it to a method. After the method modifies it, the original value is unchanged. Explain what happened (boxing) and how to fix it using generics.

---

### 📘 Concept 2: Type System — Classes, Interfaces, Abstract Classes
| | |
|---|---|
| **What to Learn** | `class` vs `abstract class` vs `interface`. When to use each. Default interface methods (.NET 8). |
| **Key Topics** | `sealed`, `virtual`, `override`, `new` keyword, explicit interface implementation |

> 🎯 **Scenario:** You have `ILogger` and `IAuditLogger` both requiring a `Log()` method. A `DatabaseLogger` needs to implement both differently. How do you use explicit interface implementation to resolve the conflict?

---

### 📘 Concept 3: Collections & Generics
| | |
|---|---|
| **What to Learn** | `List<T>`, `Dictionary<K,V>`, `HashSet<T>`, `Queue<T>`, `Stack<T>`, `LinkedList<T>` |
| **Key Topics** | When to use which collection, time complexity (O(1) vs O(n)), `IEnumerable<T>` vs `ICollection<T>` vs `IList<T>` |

> 🎯 **Scenario:** Your product search feature needs to check if a product ID exists in a list of 100,000 IDs per request. It's slow. How do you change from `List<T>.Contains()` (O(n)) to `HashSet<T>.Contains()` (O(1))?

---

### 📘 Concept 4: String Handling
| | |
|---|---|
| **What to Learn** | String immutability, `StringBuilder`, `string.Format` vs interpolation vs `string.Concat` |
| **Key Topics** | `StringComparison`, `OrdinalIgnoreCase`, `string.IsNullOrWhiteSpace`, verbatim strings `@""`, raw string literals `"""` (.NET 8) |

> 🎯 **Scenario:** A loop builds a CSV string by concatenating 50,000 rows using `+=`. Memory profiling shows 2GB of allocations. Refactor using `StringBuilder` and measure the difference.

---

### 📘 Concept 5: Exception Handling
| | |
|---|---|
| **What to Learn** | `try/catch/finally`, custom exceptions, exception filters `when`, `AggregateException` |
| **Key Topics** | `throw` vs `throw ex` (stack trace preservation), global exception handling, `ExceptionDispatchInfo` |

> 🎯 **Scenario:** Your team catches all exceptions with `catch(Exception ex)` and logs them, but the original stack trace is lost. Explain `throw` vs `throw ex` and implement a proper global exception handler in ASP.NET Core middleware.

---

## 🟡 INTERMEDIATE

### 📘 Concept 6: Delegates, Events & Func/Action
| | |
|---|---|
| **What to Learn** | `delegate`, `Func<T>`, `Action<T>`, `Predicate<T>`, multicast delegates, `event` keyword |
| **Key Topics** | Lambda expressions, closure variables, event handler memory leaks, `EventHandler<T>` |

> 🎯 **Scenario:** Your e-commerce app has a pricing engine where discount rules change monthly. How do you build a pluggable rule engine using `List<Func<Order, decimal>>` so rules can be added/removed at runtime without changing the core engine?

---

### 📘 Concept 7: LINQ (Language Integrated Query)
| | |
|---|---|
| **What to Learn** | `Where`, `Select`, `GroupBy`, `Join`, `Aggregate`, `SelectMany`, `OrderBy`, `Distinct`, `Any`, `All`, `First`, `Single` |
| **Key Topics** | Deferred vs immediate execution, method syntax vs query syntax, `IQueryable<T>` vs `IEnumerable<T>`, LINQ to SQL translation |

> 🎯 **Scenario:** A LINQ query filters a list of 10,000 orders in memory after fetching them all from the DB. How do you move the `Where` clause to `IQueryable<T>` so it executes as a SQL `WHERE` clause instead?

---

### 📘 Concept 8: Generics & Constraints
| | |
|---|---|
| **What to Learn** | Generic classes, methods, constraints (`where T : class`, `new()`, `IComparable<T>`), covariance/contravariance |
| **Key Topics** | Generic type inference, open vs closed generic types, `typeof(T)` vs `T.GetType()` |

> 🎯 **Scenario:** You're building a `Repository<T>` class that must work only with entities that implement `IEntity` (with an `Id` property). How do you add a generic constraint `where T : IEntity` and use `T.Id` safely?

---

### 📘 Concept 9: Pattern Matching & Switch Expressions
| | |
|---|---|
| **What to Learn** | `is` type patterns, `switch` expressions, positional patterns, property patterns, relational patterns (.NET 6+) |
| **Key Topics** | Exhaustive matching, discard pattern `_`, `when` guards, list patterns (.NET 7) |

> 🎯 **Scenario:** You have a payment system with `CreditCard`, `DebitCard`, and `Crypto` payment types. Replace a long `if-else if` chain with a clean `switch` expression using property patterns that extracts the processing fee per type.

---

### 📘 Concept 10: Extension Methods & Fluent API
| | |
|---|---|
| **What to Learn** | Defining and using extension methods, LINQ as extension methods, building fluent builder APIs |
| **Key Topics** | `this` keyword in static methods, method chaining, extension methods on interfaces |

> 🎯 **Scenario:** You want to add `.ToPagedList(page, size)` to any `IQueryable<T>` without modifying existing code. How do you implement it as an extension method and use it across your repositories?

---

## 🔴 ADVANCED

### 📘 Concept 11: Memory Management & Disposable Pattern
| | |
|---|---|
| **What to Learn** | `IDisposable`, `using` statement, `GC.Collect()`, finalizers `~T()`, weak references |
| **Key Topics** | `IAsyncDisposable`, `SafeHandle`, managed vs unmanaged resources, dispose pattern best practices |

> 🎯 **Scenario:** A long-running .NET service has a memory leak. Using dotMemory or `dotnet-counters`, you identify that `HttpClient` instances are not being disposed. Walk through implementing `IDisposable` correctly and why `HttpClientFactory` is the right solution.

---

### 📘 Concept 12: Span\<T\>, Memory\<T\> & High-Performance APIs
| | |
|---|---|
| **What to Learn** | `Span<T>`, `Memory<T>`, `ReadOnlySpan<T>`, `stackalloc`, `ArrayPool<T>`, `MemoryPool<T>` |
| **Key Topics** | Avoiding heap allocations, slicing without copying, `System.Buffers`, unsafe code basics |

> 🎯 **Scenario:** Your CSV parser allocates 500MB per minute due to `string.Split()` creating thousands of substrings. Rewrite it using `ReadOnlySpan<char>` and `MemoryExtensions.Split()` to parse without allocations. Use BenchmarkDotNet to prove the improvement.

---

### 📘 Concept 13: Records, Immutability & Structural Equality
| | |
|---|---|
| **What to Learn** | `record`, `record struct`, `init` properties, `with` expressions, primary constructors (.NET 8) |
| **Key Topics** | Value equality semantics, immutability benefits in DDD, `IEquatable<T>` auto-generation |

> 🎯 **Scenario:** You're implementing a CQRS command `PlaceOrderCommand`. Why should it be a `record` instead of a `class`? Show how `with` expressions allow creating modified copies for retry scenarios without mutating the original.

---

### 📘 Concept 14: IAsyncEnumerable\<T\> & Async Streams
| | |
|---|---|
| **What to Learn** | `IAsyncEnumerable<T>`, `yield return` in async methods, `await foreach`, `ConfigureAwait`, cancellation support |
| **Key Topics** | Streaming vs buffering, backpressure, difference from `Task<IEnumerable<T>>` |

> 🎯 **Scenario:** Your API exports 1 million records from SQL Server. Using `Task<List<T>>` crashes the server with OOM. Refactor using `IAsyncEnumerable<T>` with EF Core's `AsAsyncEnumerable()` and stream results to the HTTP response using `IActionResult` chunked transfer.

---

### 📘 Concept 15: Reflection, Source Generators & Expression Trees
| | |
|---|---|
| **What to Learn** | `Type`, `MethodInfo`, `PropertyInfo`, `Activator.CreateInstance`, Roslyn Source Generators, `Expression<Func<T>>` |
| **Key Topics** | Performance cost of reflection, Source Generators as compile-time alternative, building dynamic LINQ filters |

> 🎯 **Scenario:** Your admin grid needs dynamic column filtering where users pick any property to filter by at runtime. Implement this using `Expression<Func<T, bool>>` built dynamically, then compare the performance to a naive reflection-based approach.

---

---

# 📦 MODULE 2: ASP.NET Core Web API

---

## 🟢 BASICS

### 📘 Concept 1: Middleware Pipeline
| | |
|---|---|
| **What to Learn** | `Use`, `Run`, `Map`, `MapWhen`, built-in middleware order, `IMiddleware` vs convention-based |
| **Key Topics** | Request/response pipeline, short-circuiting, `next()` delegate, middleware ordering importance |

> 🎯 **Scenario:** Your API returns `200 OK` for unauthenticated requests to protected routes. You discover `UseAuthorization()` was placed before `UseAuthentication()` in `Program.cs`. Explain why order matters and show the correct middleware pipeline order.

---

### 📘 Concept 2: Controller vs Minimal APIs
| | |
|---|---|
| **What to Learn** | `ControllerBase`, `[ApiController]`, `[Route]`, Minimal API `app.MapGet/Post/Put/Delete`, `RouteGroups` (.NET 7+) |
| **Key Topics** | When to use each, `IResult`, `TypedResults`, endpoint filters (Minimal API equivalent of filters) |

> 🎯 **Scenario:** Your team is building a lightweight microservice with 5 endpoints. A team member insists on using full MVC controllers. Make the case for Minimal APIs and demonstrate how to use `RouteGroupBuilder` to organize endpoints cleanly.

---

### 📘 Concept 3: Model Binding & Validation
| | |
|---|---|
| **What to Learn** | `[FromBody]`, `[FromQuery]`, `[FromRoute]`, `[FromHeader]`, `[FromForm]`, `ModelState`, `DataAnnotations` |
| **Key Topics** | Custom model binders, `IValidatableObject`, FluentValidation integration, `ProblemDetails` response format |

> 🎯 **Scenario:** Your order API receives a `POST /orders` request where `Quantity` is `-5`. The API processes it and creates a negative-quantity order. How do you add `[Range(1, 1000)]` validation, return `400` with a `ProblemDetails` body, and integrate FluentValidation for complex business rules?

---

### 📘 Concept 4: Dependency Injection (DI) in ASP.NET Core
| | |
|---|---|
| **What to Learn** | `AddSingleton`, `AddScoped`, `AddTransient`, `IServiceProvider`, `IServiceScope`, constructor injection |
| **Key Topics** | Service lifetime pitfalls, `IOptions<T>`, `IOptionsSnapshot<T>`, `IOptionsMonitor<T>` |

> 🎯 **Scenario:** A `Singleton` `CacheService` was injected with `DbContext` (which is `Scoped`). In production, random users see each other's data. Explain the captured dependency anti-pattern and solve it using `IServiceScopeFactory`.

---

### 📘 Concept 5: Configuration & Options Pattern
| | |
|---|---|
| **What to Learn** | `appsettings.json`, `IConfiguration`, `IOptions<T>`, `IOptionsSnapshot<T>`, Environment-specific configs |
| **Key Topics** | Secret management, environment variables, Azure Key Vault integration, `ConfigureOptions<T>` |

> 🎯 **Scenario:** Your app has hardcoded connection strings in `appsettings.json` committed to GitHub. Redesign the config strategy using environment variables locally, Azure Key Vault in production, and `IOptions<DatabaseSettings>` for type-safe access.

---

## 🟡 INTERMEDIATE

### 📘 Concept 6: Filters — Action, Exception, Resource, Result
| | |
|---|---|
| **What to Learn** | `IActionFilter`, `IExceptionFilter`, `IResultFilter`, `IResourceFilter`, `IAsyncActionFilter`, filter pipeline order |
| **Key Topics** | Global filters vs controller-level vs action-level, `ServiceFilter` vs `TypeFilter`, filter vs middleware |

> 🎯 **Scenario:** Every API action should log the request duration and user ID. Instead of copy-pasting code in every action, implement a global `IAsyncActionFilter` that captures start/end time and logs it using `ILogger`. Show how to register it globally.

---

### 📘 Concept 7: API Versioning
| | |
|---|---|
| **What to Learn** | URL versioning (`/api/v1/`), query string (`?api-version=1.0`), header versioning, `Asp.Versioning.Mvc` package |
| **Key Topics** | Deprecating versions, versioning Minimal APIs, Swagger/OpenAPI per version |

> 🎯 **Scenario:** Your `GET /api/orders` endpoint needs a breaking change (renaming a field). You can't break existing mobile clients. Implement URL-based versioning (`v1` keeps old contract, `v2` has new schema) and expose separate Swagger docs per version.

---

### 📘 Concept 8: Caching Strategies
| | |
|---|---|
| **What to Learn** | `IMemoryCache`, `IDistributedCache`, Response Caching, Output Caching (.NET 7+), Cache-aside pattern |
| **Key Topics** | Cache invalidation, cache stampede, Redis as distributed cache, `VaryBy` policies |

> 🎯 **Scenario:** Your product catalog API is called 10,000 times/minute but the data changes only every 5 minutes. Implement a layered cache: in-memory for first 1 minute, Redis for 5 minutes, with a `CacheAside` pattern that auto-populates on miss.

---

### 📘 Concept 9: Health Checks & Diagnostics
| | |
|---|---|
| **What to Learn** | `AddHealthChecks()`, custom health checks, `AspNetCore.HealthChecks.*` packages, readiness vs liveness probes |
| **Key Topics** | Health check UI, integration with Kubernetes probes, `/health/live`, `/health/ready` endpoints |

> 🎯 **Scenario:** Your Kubernetes deployment randomly marks pods as unhealthy. Implement separate `/health/live` (is the process alive?) and `/health/ready` (can it serve traffic? — DB connected, Redis reachable) endpoints and configure Kubernetes probes accordingly.

---

### 📘 Concept 10: File Handling & Streaming
| | |
|---|---|
| **What to Learn** | `IFormFile`, multipart form data, streaming large files, `FileStreamResult`, chunked responses |
| **Key Topics** | `[DisableRequestSizeLimit]`, Azure Blob Storage upload/download, `Stream` vs byte array |

> 🎯 **Scenario:** Users upload 500MB video files and the server crashes with OOM errors. Refactor the upload endpoint to stream directly from `Request.Body` to Azure Blob Storage without buffering the entire file in memory, using `BlockBlobClient.UploadAsync(Stream)`.

---

## 🔴 ADVANCED

### 📘 Concept 11: gRPC in .NET
| | |
|---|---|
| **What to Learn** | Protobuf, `Grpc.AspNetCore`, service/client code generation, streaming (unary, server, client, bidirectional) |
| **Key Topics** | gRPC vs REST, gRPC-Web for browsers, deadlines/cancellation, interceptors |

> 🎯 **Scenario:** Your internal microservice communication is slow due to large JSON payloads. Replace REST calls between `OrderService` and `InventoryService` with gRPC. Show the `.proto` definition, server implementation, typed client injection, and how to handle deadlines.

---

### 📘 Concept 12: SignalR & Real-Time Communication
| | |
|---|---|
| **What to Learn** | `Hub`, `IHubContext<T>`, groups, connection management, `HubConnectionBuilder` client, scale-out with Redis backplane |
| **Key Topics** | WebSockets vs SSE vs Long Polling fallback, authentication in SignalR, `StronglyTypedHub` |

> 🎯 **Scenario:** Build a real-time order tracking dashboard. When an order status changes in the backend, push updates only to the browser of the customer who placed that order. Implement using SignalR groups (one group per `customerId`) and scale it with a Redis backplane for multi-pod deployment.

---

### 📘 Concept 13: Rate Limiting & Throttling (.NET 7+)
| | |
|---|---|
| **What to Learn** | `AddRateLimiter`, `FixedWindowLimiter`, `SlidingWindowLimiter`, `TokenBucketLimiter`, `ConcurrencyLimiter` |
| **Key Topics** | Per-user vs global limits, `[EnableRateLimiting]`, custom rejection responses, chaining policies |

> 🎯 **Scenario:** Your public API is being abused by one client making 1,000 requests/minute, degrading service for others. Implement a `SlidingWindow` rate limiter of 100 req/min per API key, return `429 Too Many Requests` with `Retry-After` header, and whitelist internal service calls.

---

### 📘 Concept 14: Multi-Tenancy Architecture
| | |
|---|---|
| **What to Learn** | Tenant resolution (subdomain, header, JWT claim), per-tenant DbContext, `IMultiTenantStore`, Finbuckle.MultiTenant |
| **Key Topics** | Shared DB (row-level), DB per tenant, schema per tenant trade-offs, tenant-aware DI |

> 🎯 **Scenario:** Your SaaS app needs to isolate data per tenant. Design a system where tenant is resolved from the `X-Tenant-Id` header, the correct connection string is selected dynamically, and EF Core `DbContext` is configured per-tenant — with a fallback if the tenant doesn't exist.

---

### 📘 Concept 15: Observability — Logging, Tracing, Metrics
| | |
|---|---|
| **What to Learn** | Structured logging (Serilog/Seq), distributed tracing (OpenTelemetry), metrics (`System.Diagnostics.Metrics`), `ActivitySource` |
| **Key Topics** | Correlation IDs, trace propagation across services, Jaeger/Zipkin integration, Prometheus + Grafana |

> 🎯 **Scenario:** A customer reports intermittent failures in checkout. Using OpenTelemetry, trace the request from the API Gateway → OrderService → PaymentService → InventoryService. Show how to add `Activity` spans, propagate `TraceId` via headers, and visualize in Jaeger.

---

---

# 📦 MODULE 3: Entity Framework Core & SQL Server

---

## 🟢 BASICS

### 📘 Concept 1: DbContext & Entity Configuration
| | |
|---|---|
| **What to Learn** | `DbContext`, `DbSet<T>`, `OnModelCreating`, `IEntityTypeConfiguration<T>`, conventions vs explicit config |
| **Key Topics** | Fluent API vs Data Annotations, `HasKey`, `HasIndex`, `HasColumnType`, `IsRequired`, `HasMaxLength` |

> 🎯 **Scenario:** Your `Product` table is created with `nvarchar(max)` for all string columns, causing slow queries. Use `IEntityTypeConfiguration<Product>` with Fluent API to set `HasMaxLength(200)` on `Name` and `HasColumnType("decimal(18,2)")` on `Price`.

---

### 📘 Concept 2: Relationships — One-to-Many, Many-to-Many, One-to-One
| | |
|---|---|
| **What to Learn** | Navigation properties, foreign keys, `HasOne/HasMany/WithOne/WithMany`, cascade delete |
| **Key Topics** | Shadow properties, owned entities, table splitting, `DeleteBehavior` options |

> 🎯 **Scenario:** Deleting a `Category` accidentally deletes all its `Products` due to cascade delete. How do you configure `DeleteBehavior.Restrict` using Fluent API to prevent this and instead throw a database error?

---

### 📘 Concept 3: Migrations
| | |
|---|---|
| **What to Learn** | `Add-Migration`, `Update-Database`, `Script-Migration`, `MigrationBuilder`, rollback strategies |
| **Key Topics** | Custom migration operations, `migrationBuilder.Sql()`, seeding with `HasData`, CI/CD migration automation |

> 🎯 **Scenario:** A migration adds a non-nullable `TenantId` column to an existing `Orders` table with millions of rows. The migration fails in production. How do you write a safe multi-step migration: add nullable → backfill data → add NOT NULL constraint?

---

### 📘 Concept 4: Querying — Basic CRUD
| | |
|---|---|
| **What to Learn** | `Find`, `FirstOrDefault`, `Where`, `Select`, `Include`, `Add`, `Update`, `Remove`, `SaveChanges` |
| **Key Topics** | Tracking vs no-tracking queries, `AsNoTracking()`, change tracker, `Entry()` state management |

> 🎯 **Scenario:** Your dashboard loads 10,000 products in a read-only grid. Each product update triggers the change tracker unnecessarily, consuming extra memory. Add `AsNoTracking()` to read queries and explain when NOT to use it (when you need to update the entity).

---

### 📘 Concept 5: Connection Management & DbContext Lifetime
| | |
|---|---|
| **What to Learn** | `AddDbContext` (Scoped lifetime), `AddDbContextFactory`, pooling (`AddDbContextPool`), connection strings |
| **Key Topics** | Avoid using `DbContext` in Singleton, `IDbContextFactory<T>` for background services |

> 🎯 **Scenario:** A `BackgroundService` (Singleton) needs to query the database every minute. Injecting `DbContext` directly throws a lifetime exception. How do you use `IDbContextFactory<AppDbContext>` to create a fresh context per operation?

---

## 🟡 INTERMEDIATE

### 📘 Concept 6: Performance Optimization
| | |
|---|---|
| **What to Learn** | Eager loading (`Include`), lazy loading, explicit loading, `Select` projections, split queries |
| **Key Topics** | N+1 query problem, compiled queries, `EF.Functions`, query logging, SQL Server execution plans |

> 🎯 **Scenario:** A product listing query with `Include(p => p.Reviews).Include(p => p.Category)` generates a massive cartesian product SQL query and times out. How do you use `AsSplitQuery()` to split it into separate SQL queries and measure the improvement?

---

### 📘 Concept 7: Concurrency Handling
| | |
|---|---|
| **What to Learn** | Optimistic concurrency with `[Timestamp]` / `RowVersion`, `DbUpdateConcurrencyException`, pessimistic locking |
| **Key Topics** | `UPDLOCK` hints via raw SQL, last-write-wins vs conflict detection, `ConcurrencyToken` |

> 🎯 **Scenario:** Two warehouse staff update the same product stock simultaneously. One update silently overwrites the other. Implement optimistic concurrency using `[Timestamp]` on the entity, catch `DbUpdateConcurrencyException`, and show the user a "record modified by another user" error with merge options.

---

### 📘 Concept 8: Raw SQL, Views & Stored Procedures
| | |
|---|---|
| **What to Learn** | `FromSqlRaw`, `FromSqlInterpolated`, `ExecuteSqlRaw`, `ExecuteSqlInterpolated`, mapping to keyless entities |
| **Key Topics** | SQL injection prevention, mapping views to entities, calling stored procedures with output params |

> 🎯 **Scenario:** A complex financial report requires a query with 10 joins that EF Core translates poorly. Implement a SQL Server View, map it to a keyless EF Core entity using `entity.HasNoKey()`, and query it via `FromSqlRaw()`.

---

### 📘 Concept 9: Global Query Filters
| | |
|---|---|
| **What to Learn** | `HasQueryFilter()`, soft delete pattern, multi-tenancy filters, `IgnoreQueryFilters()` |
| **Key Topics** | Filter stacking, performance impact, testing with query filters disabled |

> 🎯 **Scenario:** Every `Product` and `Order` query must automatically exclude soft-deleted records. Instead of adding `Where(x => !x.IsDeleted)` everywhere, implement a global query filter and demonstrate how an admin API endpoint can bypass it using `IgnoreQueryFilters()`.

---

### 📘 Concept 10: Transactions & Unit of Work
| | |
|---|---|
| **What to Learn** | `DbContext.Database.BeginTransactionAsync()`, `IDbContextTransaction`, `TransactionScope`, savepoints |
| **Key Topics** | Unit of Work pattern with EF Core, ambient transactions, distributed transactions |

> 🎯 **Scenario:** Placing an order requires: (1) decrement stock, (2) create order, (3) create payment record — all or nothing. Implement a `PlaceOrderUseCase` that wraps all 3 operations in a single EF Core transaction with a savepoint, rolling back only the payment if it fails.

---

## 🔴 ADVANCED

### 📘 Concept 11: Dapper Integration & Hybrid Approach
| | |
|---|---|
| **What to Learn** | Dapper basics, `QueryAsync<T>`, `ExecuteAsync`, multi-mapping, `DynamicParameters` |
| **Key Topics** | When Dapper beats EF Core, sharing DB connection between EF Core and Dapper, Repository abstraction |

> 🎯 **Scenario:** Your reporting module runs 50 complex aggregation queries that EF Core translates inefficiently. Introduce Dapper for read operations while keeping EF Core for writes. Show how to share the same `IDbConnection` from `DbContext` to Dapper inside the same transaction.

---

### 📘 Concept 12: Bulk Operations
| | |
|---|---|
| **What to Learn** | `EFCore.BulkExtensions`, `SqlBulkCopy`, `ExecuteUpdate`, `ExecuteDelete` (EF Core 7+) |
| **Key Topics** | Batch inserts, batch updates without loading entities, `BulkInsertOrUpdateAsync`, TVP (Table-Valued Parameters) |

> 🎯 **Scenario:** A nightly import job inserts 500,000 product rows using `DbContext.AddRange()` + `SaveChanges()` and takes 45 minutes. Refactor using `BulkInsertAsync` from EFCore.BulkExtensions and reduce it to under 2 minutes. Measure with `Stopwatch`.

---

### 📘 Concept 13: EF Core Interceptors
| | |
|---|---|
| **What to Learn** | `DbCommandInterceptor`, `ISaveChangesInterceptor`, `IDbConnectionInterceptor`, `AddInterceptors()` |
| **Key Topics** | Audit logging via interceptors, soft-delete via `SavingChangesAsync`, query tagging |

> 🎯 **Scenario:** Your compliance team requires an audit trail for every `INSERT`, `UPDATE`, and `DELETE` on the `Orders` table — capturing the old/new values, timestamp, and user ID — without adding audit code to every repository. Implement an `ISaveChangesInterceptor` that auto-writes to an `AuditLog` table.

---

### 📘 Concept 14: Table-Per-Hierarchy (TPH), Table-Per-Type (TPT), Table-Per-Concrete (TPC)
| | |
|---|---|
| **What to Learn** | Inheritance mapping strategies in EF Core, discriminator column (TPH), separate tables (TPT), TPC (.NET 7+) |
| **Key Topics** | Performance trade-offs, polymorphic queries, when each strategy fits |

> 🎯 **Scenario:** You have `PaymentMethod` with subtypes `CreditCard`, `BankTransfer`, and `Crypto`. Using TPH stores nulls for inapplicable columns. Migrate to TPC where each payment type gets its own table. Show the migration and measure query performance differences.

---

### 📘 Concept 15: Event Sourcing with EF Core
| | |
|---|---|
| **What to Learn** | Event store schema design, append-only writes, aggregate reconstruction, snapshots |
| **Key Topics** | `IEvent` interface, `EventStoreRepository`, projections/read models, eventual consistency |

> 🎯 **Scenario:** Your `OrderAggregate` needs a full audit history of every state transition (Created → Paid → Shipped → Delivered). Design an event store using SQL Server with EF Core where events are append-only, implement `OrderAggregate.Rehydrate(IEnumerable<IEvent>)`, and add snapshotting every 50 events.

---

---

# 📦 MODULE 4: Dependency Injection & Clean Architecture

---

## 🟢 BASICS

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **DI Fundamentals** | Service registration, lifetimes (`Singleton/Scoped/Transient`), constructor injection | A `ReportService` creates `new EmailService()` internally. Refactor to use DI and explain testability benefits. |
| **Interface Abstraction** | Program to interfaces, Liskov Substitution Principle | Swap `SmtpEmailService` to `SendGridEmailService` at deployment time using `IEmailService` + DI configuration only. |
| **Options Pattern** | `IOptions<T>`, `IOptionsSnapshot<T>`, `IOptionsMonitor<T>` | A feature flag needs to be changed without restarting the service. Use `IOptionsMonitor<T>` to hot-reload config. |
| **Service Locator Anti-Pattern** | Why `IServiceProvider.GetService<T>()` is bad | A colleague injects `IServiceProvider` into a service and calls `GetService<T>()` everywhere. Explain why this is an anti-pattern and refactor it. |
| **Project Layer Structure** | Domain, Application, Infrastructure, API layers | A new "Place Order" feature needs to span all 4 layers. Walk through where each class lives and why. |

---

## 🟡 INTERMEDIATE

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **MediatR — Commands & Queries** | `IRequest<T>`, `IRequestHandler<T>`, `INotification`, send vs publish | Refactor a fat controller action that does validation + business logic + DB save into a `PlaceOrderCommand` + `PlaceOrderCommandHandler`. |
| **MediatR Pipeline Behaviors** | `IPipelineBehavior<TRequest, TResponse>`, ordering behaviors | Add `ValidationBehavior`, `LoggingBehavior`, and `CachingBehavior` as a pipeline. Show how they execute in order for every command. |
| **CQRS Pattern** | Separate command/query models, read vs write DbContext | Your order query returns 50 fields but the mobile app only needs 5. Implement a dedicated `OrderSummaryQuery` using a thin read model. |
| **Domain Events** | `INotification`, raising events from domain, `INotificationHandler<T>` | When an order is placed, trigger `SendConfirmationEmailHandler` and `UpdateInventoryHandler` using MediatR domain event notifications. |
| **Keyed Services (.NET 8)** | `AddKeyedSingleton/Scoped/Transient`, `[FromKeyedServices]` | Register `SmsNotification`, `EmailNotification`, `PushNotification` under the same `INotification` interface, resolve by key based on user preference. |

---

## 🔴 ADVANCED

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **Outbox Pattern** | Transactional outbox, polling publisher, EF Core + outbox table | RabbitMQ is down when an order is placed. Events are lost. Implement an outbox table written in the same transaction as the order, with a background poller that publishes pending events. |
| **Vertical Slice Architecture** | Feature folders, `IRequest/IRequestHandler` per feature, no shared service layers | Compare adding a "Cancel Order" feature in Layered vs Vertical Slice architecture. Show the folder structure and class count difference. |
| **Modular Monolith** | Module boundaries, inter-module communication via events, separate `DbContext` per module | Build an `OrderModule` and `InventoryModule` that each have their own `DbContext`, communicate only via domain events, but run in the same process. |
| **Decorator Pattern via DI** | `Scrutor`'s `.Decorate<T>()`, wrapping services | Add retry + circuit breaker behavior to `IPaymentService` without modifying the original class, using the Decorator pattern registered via Scrutor. |
| **Process Manager / Saga** | Stateful saga, compensating transactions, state machine | An order saga coordinates: payment → inventory reservation → shipping. If shipping fails, compensate by releasing inventory and refunding payment. Implement using `Stateless` state machine. |

---

---

# 📦 MODULE 5: Authentication & Authorization

---

## 🟢 BASICS

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **JWT Authentication** | JWT structure (header.payload.signature), `AddJwtBearer`, `[Authorize]`, claims | Build a `POST /auth/login` endpoint that returns a JWT. Protect `GET /orders` with `[Authorize]` and test with/without token. |
| **ASP.NET Core Identity** | `UserManager<T>`, `RoleManager<T>`, `SignInManager<T>`, Identity tables | Scaffold Identity for an existing app. Add email confirmation before allowing login. |
| **Role-Based Authorization** | `[Authorize(Roles="Admin")]`, role claims, `AddRoles<IdentityRole>()` | An `AdminController` must only be accessible to users with the `Admin` role. Implement and test unauthorized access returns `403`. |
| **Cookie Authentication** | `AddCookie`, `HttpContext.SignInAsync`, sliding expiration | Build an MVC app with cookie-based login. Implement "Remember Me" with a 30-day persistent cookie. |
| **HTTPS & Security Headers** | `UseHttpsRedirection`, `UseHsts`, `AddAntiforgery`, CORS | A browser rejects API calls due to CORS. Configure `AddCors` to allow only your frontend origin and test with preflight requests. |

---

## 🟡 INTERMEDIATE

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **OAuth2 / OpenID Connect** | Authorization Code flow, PKCE, `AddOpenIdConnect`, Azure AD integration | Integrate Azure AD SSO into your ASP.NET Core app. Configure `AddMicrosoftIdentityWebApi` and test token validation. |
| **Policy-Based Authorization** | `AddAuthorization`, `AddPolicy`, `IAuthorizationRequirement`, `IAuthorizationHandler` | Implement a `MinimumAgeRequirement` (user must be 18+) as a custom policy. Apply it to a gambling feature endpoint. |
| **Resource-Based Authorization** | `IAuthorizationService.AuthorizeAsync`, resource parameter | A user can only edit their own profile. Implement `ProfileOwnerAuthorizationHandler` that checks if the `userId` claim matches the resource owner. |
| **Refresh Tokens** | Short-lived access token + long-lived refresh token, token rotation, revocation | Implement a `/auth/refresh` endpoint. When refresh token is used, issue a new access + refresh token pair and invalidate the old refresh token (rotation). |
| **Multiple Auth Schemes** | `AddJwtBearer` + `AddCookie`, `[Authorize(AuthenticationSchemes="...")]` | Your app serves both an SPA (JWT) and server-rendered MVC (Cookie). Configure both schemes so each client type authenticates correctly. |

---

## 🔴 ADVANCED

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **Custom Token Provider (IdentityServer / Duende)** | `ITokenService`, custom claims transformation, `IClaimsTransformation` | Your JWT tokens need to include dynamically loaded permissions from the DB on every request. Implement `IClaimsTransformation` to enrich the principal after validation. |
| **Zero Trust / mTLS** | Mutual TLS, certificate authentication, `AddCertificate`, Azure Managed Identity | Service-to-service calls between microservices must use mTLS. Configure `AddCertificate` authentication and validate client certificates in middleware. |
| **Dynamic Policy Provider** | `IAuthorizationPolicyProvider`, policies loaded from DB | Your permission system stores "CanEditOrder", "CanRefundOrder" in a DB. Implement a `DynamicPolicyProvider` that builds policies on-demand without restarting the app. |
| **Tenant Isolation in SaaS** | Tenant claim validation, prevent cross-tenant access, tenant-scoped tokens | A bug allows User A of Tenant 1 to query orders of Tenant 2 by manipulating the `tenantId` query parameter. Implement a `TenantAuthorizationFilter` that validates the tenant claim in the JWT matches the requested resource's tenant. |
| **GDPR & Data Protection** | `IDataProtectionProvider`, `DataProtector`, key management, purpose strings | Encrypt PII (email, phone) stored in SQL Server using ASP.NET Core Data Protection API. Show how to rotate keys without losing access to old encrypted data. |

---

---

# 📦 MODULE 6: Performance, Async & Concurrency

---

## 🟢 BASICS

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **async/await Basics** | `Task`, `Task<T>`, `async void` pitfalls, `await` vs `.Result` | Convert a synchronous `GetProductById()` that calls an HTTP API into a properly `async` method. Explain why `async void` is dangerous. |
| **Task.WhenAll & WhenAny** | Parallel async operations, aggregating results | An order summary page needs data from 3 APIs: product, user, and shipping. Run all 3 calls in parallel using `Task.WhenAll` and combine results. |
| **CancellationToken** | `CancellationTokenSource`, propagation, cooperative cancellation | A user navigates away from a slow report page. Pass `CancellationToken` from the HTTP request down through service → repository → DB query, so the DB query is cancelled when the user disconnects. |
| **BackgroundService** | `IHostedService`, `BackgroundService`, `ExecuteAsync` | Build a background service that processes a queue of email notifications every 30 seconds without blocking the main thread. |
| **ConfigureAwait** | `ConfigureAwait(false)` in library code, context capture | A library method using `await` without `ConfigureAwait(false)` deadlocks in a sync-over-async caller. Fix it and explain when `ConfigureAwait(false)` is needed. |

---

## 🟡 INTERMEDIATE

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **Channel\<T\>** | `Channel.CreateBounded/Unbounded`, producer/consumer, backpressure | Build an order processing pipeline: HTTP requests write to a `Channel<Order>`, background workers read and process. Show how `BoundedChannel` applies backpressure when the channel is full. |
| **SemaphoreSlim** | Limiting concurrency, async throttling | Your service calls an external API that allows max 10 concurrent connections. Use `SemaphoreSlim(10)` to throttle concurrent calls and prevent `429` errors. |
| **Parallel.ForEachAsync (.NET 6+)** | Bounded parallelism for async operations | Process 10,000 product images (resize + upload to Azure) with max 20 concurrent operations using `Parallel.ForEachAsync` with `MaxDegreeOfParallelism = 20`. |
| **ValueTask** | When to use `ValueTask` over `Task`, avoid allocations in hot paths | A `GetFromCacheOrDb<T>()` method is called millions of times/hour. Show how `ValueTask<T>` avoids `Task` allocations when the result is already cached. |
| **Thread Safety — Interlocked & Concurrent Collections** | `Interlocked.Increment`, `ConcurrentDictionary`, `ConcurrentQueue` | A request counter in a Singleton service is incremented by multiple threads. The count is wrong. Fix using `Interlocked.Increment` and explain why `lock` would also work but is slower. |

---

## 🔴 ADVANCED

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **System.IO.Pipelines** | `PipeReader/PipeWriter`, zero-copy I/O, `SequenceReader<T>` | Parse a high-throughput binary TCP protocol (e.g., FIX financial protocol) with minimal allocations using `System.IO.Pipelines`. Compare memory usage vs `StreamReader`. |
| **Memory & ArrayPool** | `ArrayPool<T>.Shared`, `MemoryPool<T>`, `IMemoryOwner<T>` | Your image thumbnail generator allocates a new `byte[]` per image. Use `ArrayPool<T>` to rent/return buffers and eliminate GC pressure at 1000 images/second. |
| **GC Tuning** | Server GC vs Workstation GC, `GCSettings.LatencyMode`, `GC.TryStartNoGCRegion`, LOH tuning | Your trading app has GC pauses of 50ms during high load, causing missed SLA. Tune `DOTNET_GCConserve` and `GCSettings.LatencyMode = SustainedLowLatency`, and eliminate LOH allocations by using pooled buffers. |
| **Lock-Free Programming** | `Interlocked.CompareExchange`, `Volatile.Read/Write`, `SpinLock`, `SpinWait` | Implement a thread-safe LRU cache using `ConcurrentDictionary` and `Interlocked` operations without using `lock`. Benchmark against a lock-based implementation. |
| **Native AOT & Trimming (.NET 8)** | `PublishAot`, trimming annotations, reflection-free serialization, `JsonSerializerContext` | Publish a microservice with Native AOT to reduce startup time from 800ms to 50ms. Identify and fix trimming warnings, replace reflection-based serialization with `JsonSerializerContext`. |

---

---

# 📦 MODULE 7: Testing in .NET

---

## 🟢 BASICS

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **xUnit Basics** | `[Fact]`, `[Theory]`, `[InlineData]`, `[MemberData]`, `Assert.*`, test project setup | Write tests for a `DiscountCalculator.Calculate(order)` method covering zero discount, 10%, and 100% edge cases using `[Theory]` + `[InlineData]`. |
| **Moq Basics** | `Mock<T>`, `.Setup()`, `.Returns()`, `.Verify()`, `It.IsAny<T>()` | Unit test `OrderService.PlaceOrder()` by mocking `IInventoryService` and `IEmailService`. Verify `IEmailService.Send()` was called exactly once with the correct email address. |
| **FluentAssertions** | `.Should().Be()`, `.Throw<T>()`, `.BeEquivalentTo()`, collection assertions | Replace raw `Assert.Equal()` calls with FluentAssertions. Show how `result.Should().BeEquivalentTo(expected, opts => opts.Excluding(x => x.CreatedAt))` handles ignoring dynamic fields. |
| **Test Organization** | Arrange-Act-Assert pattern, test naming conventions, test categories `[Trait]` | Organize tests for `OrderService` into unit, integration, and acceptance categories. Show a clear naming convention: `MethodName_Scenario_ExpectedResult`. |
| **Testing Exceptions** | `Assert.Throws<T>()`, FluentAssertions `.Should().Throw<T>().WithMessage()` | Test that `OrderService.PlaceOrder()` throws `InsufficientStockException` when stock is 0, and verify the exception message contains the product name. |

---

## 🟡 INTERMEDIATE

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **WebApplicationFactory** | `WebApplicationFactory<Program>`, `HttpClient`, overriding services in tests | Write an integration test for `POST /api/orders` that uses a real in-memory SQLite database, overrides `IEmailService` with a mock, and asserts the response is `201 Created` with correct body. |
| **TestContainers** | `Testcontainers.MsSql`, `Testcontainers.RabbitMq`, Docker-based integration tests | Replace SQLite in integration tests with a real SQL Server container. Show `MsSqlBuilder` setup, running migrations, seeding data, and tearing down after tests. |
| **Time Abstraction** | `IClock` / `TimeProvider` (.NET 8), `FakeTimeProvider` | A discount expires at midnight. Unit test the expiry logic by injecting `FakeTimeProvider` set to 11:59 PM (active) and 12:01 AM (expired). |
| **Contract Testing with Pact** | Consumer-driven contracts, `PactNet`, provider verification | Your .NET API is consumed by a React app. Write a Pact consumer test in React that defines the expected `GET /orders/{id}` response, then verify the .NET API satisfies it using `PactVerifier`. |
| **Code Coverage** | `Coverlet`, `dotnet test --collect:"XPlat Code Coverage"`, ReportGenerator, branch coverage | Configure coverage in CI. Set a minimum threshold of 80% line coverage for the `Application` layer. Fail the build if coverage drops below threshold. |

---

## 🔴 ADVANCED

| 📘 Concept | What to Learn | Scenario |
|---|---|---|
| **Architecture Tests** | `NetArchTest`, `ArchUnitNET`, layer dependency rules | Write an architecture test that asserts: "Domain layer must not reference Infrastructure layer." Run it in CI to prevent accidental layer violations. |
| **Mutation Testing** | `Stryker.NET`, mutation score, surviving mutants | Run Stryker on `DiscountCalculator`. It shows 40% of mutants survive. Identify which conditions are undertested and add tests to kill surviving mutants. |
| **BenchmarkDotNet** | `[Benchmark]`, `MemoryDiagnoser`, comparing implementations | Benchmark `string.Split()` vs `ReadOnlySpan<char>` based CSV parsing. Show mean time, allocations, and GC collections per operation. Integrate baseline comparison in CI. |
| **Chaos Engineering** | `Simmy` (Polly chaos), fault injection, latency injection | Inject a 500ms latency into `IPaymentService` calls during integration tests using Simmy. Verify your Polly timeout policy triggers correctly and the API returns `503` gracefully. |
| **End-to-End Testing with Playwright** | `Microsoft.Playwright`, browser automation, `IPlaywright`, page objects | Write an E2E test for the full order checkout flow: login → add to cart → checkout → confirm order. Run it against a Docker-composed test environment in CI. |

---

---

# 🗺️ Master Concept Map Summary

```
MODULE 1: C# Fundamentals
├── 🟢 Value Types, Collections, Strings, Exceptions
├── 🟡 Delegates, LINQ, Generics, Pattern Matching, Extension Methods
└── 🔴 IDisposable, Span<T>, Records, IAsyncEnumerable, Reflection

MODULE 2: ASP.NET Core Web API
├── 🟢 Middleware, Controllers, Model Binding, DI, Configuration
├── 🟡 Filters, Versioning, Caching, Health Checks, File Streaming
└── 🔴 gRPC, SignalR, Rate Limiting, Multi-tenancy, OpenTelemetry

MODULE 3: EF Core & SQL Server
├── 🟢 DbContext, Relationships, Migrations, CRUD, Lifetimes
├── 🟡 Performance, Concurrency, Raw SQL, Query Filters, Transactions
└── 🔴 Dapper, Bulk Ops, Interceptors, TPH/TPT/TPC, Event Sourcing

MODULE 4: DI & Clean Architecture
├── 🟢 DI Basics, Interfaces, Options, Anti-patterns, Layering
├── 🟡 MediatR, CQRS, Pipeline Behaviors, Domain Events, Keyed DI
└── 🔴 Outbox, Vertical Slice, Modular Monolith, Decorator, Saga

MODULE 5: Auth & Security
├── 🟢 JWT, Identity, RBAC, Cookies, HTTPS
├── 🟡 OAuth2/OIDC, Policy Auth, Resource Auth, Refresh Tokens
└── 🔴 Custom Token, mTLS, Dynamic Policies, Tenant Isolation, GDPR

MODULE 6: Performance & Async
├── 🟢 async/await, WhenAll, CancellationToken, BackgroundService
├── 🟡 Channel<T>, SemaphoreSlim, Parallel.ForEachAsync, ValueTask
└── 🔴 Pipelines, ArrayPool, GC Tuning, Lock-Free, Native AOT

MODULE 7: Testing
├── 🟢 xUnit, Moq, FluentAssertions, AAA Pattern
├── 🟡 WebApplicationFactory, TestContainers, Time Abstraction, Pact
└── 🔴 Architecture Tests, Mutation Testing, BenchmarkDotNet, Chaos, Playwright
```

---

> 💡 **Pro Tip:** Each 🟢 Basic concept should take ~2 hours, 🟡 Intermediate ~4 hours, 🔴 Advanced ~1 day. Total estimated time: **~14 weeks** at 2 hours/day.

Would you like me to:
1. 📝 **Create a GitHub Issue** with this full planner to track your progress?
2. 🧩 **Generate similar planners** for Angular, RabbitMQ/MassTransit, Kubernetes, Azure, or Microservices?
3. 💻 **Provide code examples** for any specific concept above?
