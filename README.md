# sympatico

Architecture and Domain Modeling workshop


Microservices
* Solve organizational problems
*     * Team is too large to work effectively on shared codebase
*         * Teams blocked on other teams, can’t make progress
*             * Communication overhead becomes gigantic
*                 * Product velocity stalled
*                 * Cause technical problems
*                     * Need well defined business domains for stable APIs
*                         * No more shared DB - distributed transactions?
*                                 * Better to avoid distributed transactions and instead rely on an enventually consistent solution
*                                     * Testing becomes really hard
*                                         * Require dev/ops culture: devs deploy & operate their work
*                                                 * Requires devs to realize they are responsible for operating their service
*                                                     * Job (service) scheduling - manually works, for a while….
*                                                         * Adressability I.e. service discovery
*                                                             * Monitoring and instrumentation - tail -f? Nagios?
*                                                                 * Distributed tracing?
*                                                                     * Build pipelines?
*                                                                         * Security???
*                                                                         * Structure is absolutely necessary to make micro services a success
*                                                                             * Design patterns provide a “cage” to the complexity
*                                                                                 * 40 concerns to answer when creating a prod ready service
*
*                                                                                 GoKit in Theory
*                                                                                 * A std lib for microservices
*                                                                                 * Like Finagle but for Go
*                                                                                 * Adapters, bindings, etc. to common infra components
*                                                                                 * Play nice in your existing, heterogeneous infrastructure
*                                                                                     * Microservices should be brown fielded, not green fielded
*                                                                                     * Structure to tame the beast of incidental complexity 
*
*                                                                                     Current Goals
*                                                                                     * Mostly the same
*                                                                                     * Less about infrastructure, operational details, etc.
*                                                                                     * More about application architecture
*                                                                                         * How do you achieve maintainability
*                                                                                             * Optimize for easy to learn/mantain
*                                                                                                 * Should build services to remove dependencies on any 1 person
*
*                                                                                                 Non-goals
*                                                                                                 * Messaging patterns other than RPC
*                                                                                                 * Requiring specific bits of infrastructure or tooling to work
*                                                                                                 * Acting as an all-in service framework
*                                                                                                 * Re-implementing existing, good solutions to problems
*
*                                                                                                 Comparisons
*                                                                                                 * Micro(Go) - very opinionated, all=in, framework-ish
*                                                                                                 * Finagle (Scala) - original inspiration, lower-level than Go kit
*                                                                                                 * Spring Boot (Java) - similar abstractions, far more magical
*                                                                                                 * Tokio (Rust) - explicitly a clone of Finagle, lower-level than Go kit
*
*                                                                                                 Go kit is not important, Good architectural decisions for services is
*
*                                                                                                 Domain Driven Design
*                                                                                                 * Wiki definition
*                                                                                                 * Team must typically. Implement a great deal of isolation and encapsulation (structure) within the domain model. Consequently, a system based on a domain-driven design can come at a relatively high cost.
*                                                                                                 * Boundary context
*                                                                                                     * Each service has its own entities
*                                                                                                             * A customer for a salesperson (service) could be wildly different from a customer for support (service
*
*                                                                                                             Example Service Design
*                                                                                                             * ExampleService that does adding and concatenating
*                                                                                                             * Core layer (no side effects) and wrap it in layers (Transport, logging, … so forth)
*                                                                                                             * https://appliedgo.net/di/ - Clean architecture
*                                                                                                                 * All external interfaces (source code dependencies) can only point inward (towards business domain)
*
*                                                                                                                 When to extract a service?
*                                                                                                                 * Service has well-defined bounded context
*                                                                                                                     * Minimal/no coordination with other services
*                                                                                                                     * At least on of these is true:
*                                                                                                                         * Radically different runtime reqs (i.e. QPS)
*                                                                                                                             * Test/deploy/etc. on much different schedule
*
*                                                                                                                             Client/Service coupling?
*                                                                                                                             * Prefer to not couple them
*                                                                                                                             * Instead prefer a binding contract between the two services
*                                                                                                                                 * Consumer Driven Contracts
*
*                                                                                                                                 GoKit in practice
*                                                                                                                                 * Go kit enforces a lot of structure and boilerplate
*                                                                                                                                 * The benefit really comes in large and fluid orgs
*                                                                                                                                 * Good architecture already gives us 80% of the value
*                                                                                                                                 * Ask your doctor if Go kit is right for you…
*                                                                                                                                 )
