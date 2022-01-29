- [Domain Driven Design Project Structure](#domain-driven-design-project-structure)
  - [BoundedContext.API](#boundedcontextapi)
  - [BoundedContext.Domain](#boundedcontextdomain)
    - [Entities](#entities)
    - [Aggregates](#aggregates)
  - [BoundedContext.Infrastructure](#boundedcontextinfrastructure)


# Domain Driven Design Project Structure

## BoundedContext.API

- Application layer / web api project
- Does not contain business rule knowledge, but only coordinates tasks and delegates work to collaboration of domain objects in next layer down
- It can have state that reflects the progress of task for user or program
- It can not have state reflecting business situation
- It implements microservice interaction, remote network access, and the external web api used from UI or client apps
- It includes command and queries, event driven communication between microservices
- Depends on the Domain Model layer so it can:
  - Use entity objects
  - Use repository interfaces/contracts
- Depends on the Infrastructure layer (thru DI) so it can:
  - Use repository implementation classes, ideally through DI
- Consists of:
  - ASP.Net Web API
  - Network access to microservice
  - API contracts/implementation
  - Commands and command handlers
  - Queries (when using an CQRS approach)
    - Micro ORMs like Dapper

## BoundedContext.Domain

- Domain model layer / class library
- Responsible for representing concepts of the business, information about business situation, and business rules
- Follows the `persistence ignorance` and `infrastructure ignorance` principles
- Should not depend on any other layer
- Ideally, it must NOT take dependency on any other layer
- It implements:
  - Domain Entities, Aggregate-Roots, and Value-Objects
  - Repository contracts/interfaces (to be used in DI)
- Consists of:
  - Domain entity model
  - POCO entity classes (clean C# code)
  - Domain entities with data + behavior
  - DDD patterns
    - Domain entity, aggregate
    - Aggregate root, value object
    - Repository contracts/interfaces

### Entities

### Aggregates

## BoundedContext.Infrastructure

- Infrastructure layer / ORM like Entity Framework Core
- Responsible for persisting domain entity data in database or persistence store
- Depends on the Domain-Model layer so it can:
  - Use entity objects
    - Like EF updating a database through mapped entities
- Direct dependency on infrastructure frameworks `EF Core` or any other `database`, `cache` or infrastructure API
- Consists of:
  - Data persistence infrastructure
    - Repository implementations
  - Use of ORMs or data access API
    - Entity framework core or any ORM
    - ADO.Net
    - Any NoSql database API
  - Other infrastructure implementation used from the application layer
    - Logging, cryptography, search engine, etc.




