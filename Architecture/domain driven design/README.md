- [Domain Driven Design](#domain-driven-design)
  - [Design Tools](#design-tools)
    - [Strategic Design](#strategic-design)
      - [Common Terms](#common-terms)
        - [Model](#model)
        - [Ubiquitous Language](#ubiquitous-language)
        - [Bounded Context](#bounded-context)
    - [Tactical Design](#tactical-design)
      - [Tactical Design Tools](#tactical-design-tools)
        - [Entity](#entity)
        - [Value Object](#value-object)
        - [Service](#service)
        - [Aggregates](#aggregates)
        - [Domain Events](#domain-events)
        - [Factories and Repositories](#factories-and-repositories)
  - [Terminologies](#terminologies)
    - [Domain](#domain)

# Domain Driven Design

- Approach for architecting software design by looking at software in top-down approach
- Focus should be on business rather than technology

Domain driven design talks about two kinds of desgin tools:

## Design Tools

### Strategic Design

- Helps us to solve all problems that are related to software modeling
- It is a design approach similar to Object Oriented design where we are forced to think in terms of objects

#### Common Terms

##### Model

- Acts as a core logic and describes selected aspects of domain
- Used to solve problems related to that business

##### Ubiquitous Language

- Common language used by all team members to connect all activities of team around domain model

##### Bounded Context

- Refers to boundary conditions of context
- It is description of a boundary and acts as a threshold within which, a particular domain model is defined and applicable
- We should keep bounded context relatively small

### Tactical Design

- Talks about implementation details ie. modeling domain
- This process occurs during product development phase

#### Tactical Design Tools

##### Entity

- A class that has some properties
- An entity instance has `global identity` which never changes
- Implements some business logic and could be uniquery identified using an ID
- It is stored in DB as a row
- Eg: User, Order, Post

##### Value Object

- `Immutable`, light-weight object that has `no identity`
- It reduces the complexity by performing complex calculations, isolating heavy computational logic from entities
- Eg: Address, UserProfile, OrderDetails, OrderItems, PostComments

##### Service

- A `stateless` class that fits somewhere else other than and entity or value object
- A functionality that exists somewhere between entities and values objects but related to neither entity nor value object

##### Aggregates

- A collection of entities and values which come under a single transactional boundary
- It controls change and have a root entity called `Aggregate Root`
- Root entity governs lifetime of other entities in aggregates.

##### Domain Events

- Are generated to ensure `eventual consistency`

##### Factories and Repositories

- Factories
  - help in managing begining of lifecycle of aggregates
  - help in creating aggregates
- Repositories
  - help in managing middle and end of lifecycle of aggregates
  - help in persisting aggregates
  - We should always create a repository per aggregate root but not for all entities


## Terminologies

### Domain

- Refers to business
- 


