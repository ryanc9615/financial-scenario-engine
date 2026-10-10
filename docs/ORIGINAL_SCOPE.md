I want you to help me scope and define **Project 2 of my technical apprenticeship: Financial Scenario Engine**.

Project 1 — Business Model Explorer — focused primarily on frontend engineering and interactive visualisation.

Project 2 should shift the technical centre of gravity to:

- Backend engineering
- HTTP and APIs
- Python application development
- Relational databases
- SQL
- PostgreSQL
- Persistence
- Backend architecture
- Validation
- Testing

The application domain should remain business and finance so that the technical learning reinforces my broader commercial and financial understanding.

---

# Project concept

I want to build a backend service that represents a business model and allows another application to:

- Create a company
- Define operating assumptions
- Create a financial scenario
- Calculate financial outcomes
- Save the scenario
- Retrieve it later
- Update it
- Create alternative scenarios
- Compare scenarios

The initial company should remain a fictional B2B SaaS business, ideally using concepts I already understand from Project 1.

The goal is not to build another polished frontend.

The goal is to understand what happens **behind the interface**.

I want to be able to trace:

User/client\
→ HTTP request\
→ API route\
→ validation\
→ business/domain logic\
→ financial calculation engine\
→ database operation\
→ persisted data\
→ response serialization\
→ JSON response

By the end of the project, I should genuinely understand this pipeline rather than merely having AI generate it for me.

---

# Broader objective

I am working toward becoming someone who can:

- Understand businesses financially and commercially
- Build useful software end to end
- Model business systems
- Use technology as leverage
- Eventually build more sophisticated AI-enabled business applications

This project should move me from:

> “I can build an interactive frontend”

toward:

> “I understand how a real application receives requests, executes business logic, stores data and returns results.”

---

# Primary technical learning objectives

Help me use the project to develop practical understanding of:

## Python application development

- Python modules and packages
- Functions and classes
- Type hints
- Data structures
- Exceptions
- Virtual environments
- Dependency management
- Separation of concerns
- Organising a real Python codebase

## HTTP

- Client/server model
- Requests and responses
- JSON
- Headers
- URL/path/query parameters
- HTTP methods
- GET
- POST
- PATCH / PUT
- DELETE
- Status codes
- Idempotency where relevant
- Statelessness
- Basic caching concepts if naturally relevant

## API design

- REST-style resource design
- Endpoints
- Request schemas
- Response schemas
- Validation
- Error responses
- API contracts
- Versioning only if justified
- API documentation
- OpenAPI / Swagger

## Backend architecture

- Routing layer
- Service/application layer
- Domain/business logic
- Persistence/repository layer
- Separation of calculations from HTTP concerns
- Dependency injection at a useful level
- Configuration
- Error handling
- Logging at a basic level

## Financial modelling in code

- Business assumptions
- Derived values
- Scenario calculations
- Three-statement logic where appropriate
- Business KPIs
- Scenario comparison
- Deterministic calculations
- Clear separation between assumptions and outputs

## SQL

- SELECT
- INSERT
- UPDATE
- DELETE
- WHERE
- ORDER BY
- GROUP BY
- Aggregation
- JOINs
- Subqueries where useful
- Basic query planning intuition

## Relational databases

- Tables
- Rows
- Columns
- Data types
- Primary keys
- Foreign keys
- One-to-many relationships
- Many-to-many relationships only if genuinely needed
- Constraints
- Uniqueness
- Nullability
- Referential integrity
- Indexes
- Normalisation versus denormalisation at a basic level

## PostgreSQL

- Creating schemas/tables
- Connecting from Python
- Query execution
- Transactions
- Constraints
- Indexes
- Database inspection/debugging

## ORM and persistence

Likely:

- SQLAlchemy
- ORM concepts
- Models
- Sessions
- Queries
- Transactions

But I want you to explain the difference between:

- SQL itself
- PostgreSQL
- ORM abstractions
- SQLAlchemy

I do not want the ORM to hide SQL from me.

## Migrations

Likely Alembic.

Teach me:

- Why migrations exist
- How schema changes are represented
- Upgrade / downgrade concepts
- Why production applications cannot simply recreate databases whenever the model changes

## Testing

- Unit tests
- Calculation tests
- API tests
- Integration tests
- Database tests
- Fixtures
- Test isolation
- Happy paths
- Failure cases
- Validation tests

Likely using pytest.

## Debugging

I want to learn to diagnose failures across:

API route\
→ validation\
→ business logic\
→ ORM\
→ SQL\
→ database

rather than blindly changing code until things work.

---

# Likely technology stack

My initial expectation is something close to:

- Python
- FastAPI
- Pydantic
- PostgreSQL
- SQLAlchemy
- Alembic
- pytest
- Git
- GitHub

Possibly Docker later in the project if it adds genuine learning value.

Please challenge this stack if there is a better reasoned alternative.

For every major technology, explain:

1. What problem it solves
2. What abstraction it introduces
3. What underlying concept I still need to understand
4. What would happen if we did not use it

---

# Deliberate constraints

Protect the scope aggressively.

For Project 2:

- No production-grade authentication
- No user accounts unless absolutely necessary
- No OAuth
- No payments
- No LLMs
- No RAG
- No agents
- No machine learning
- No complex frontend
- No fancy visualisation work
- No third-party accounting integrations
- No distributed systems
- No queues unless a real need emerges
- No microservices
- No Kubernetes
- No complex cloud architecture
- No excessive DevOps
- No premature scalability engineering

If I suggest features that belong more naturally to later projects, label them:

**PARK FOR LATER**

The goal is not to create a startup.

The goal is to become much more capable at backend engineering.

---

# Relationship to Project 1

Project 1 already taught me frontend concepts through an interactive business model.

For Project 2, I want to reuse that domain knowledge.

The business itself should therefore not become dramatically more complicated unless the complexity teaches an important backend concept.

If useful, the Project 1 frontend may eventually call the Project 2 API, but that integration should not dominate the project.

The backend should be understandable and testable independently.

---

# What I want you to produce

Please scope the project systematically.

## 1. Product definition

Define:

- What the Financial Scenario Engine is
- Who/what consumes it
- The core problem
- The primary use case
- What the service should be capable of doing by the end
- Why this is a useful backend-engineering project

Keep this narrow and concrete.

---

## 2. Domain model

Design the smallest useful business domain.

Potential concepts might include:

- Company
- Scenario
- Assumptions
- Revenue model
- Cost model
- Financial outputs
- KPI outputs
- Scenario versions

But do not assume all of these need to become database entities.

Explain the difference between:

- Domain concepts
- API objects
- Database tables

I want to learn why these are not always identical.

---

## 3. Financial model

Define the financial/business model to be implemented.

Prefer one fictional B2B SaaS business.

Specify:

### Inputs

For example:

- Starting customers
- Price / ARPU
- Churn
- Sales headcount
- Sales productivity
- Conversion
- Marketing spend
- Headcount
- Salary assumptions
- Gross margin
- Payment terms
- Starting cash

### Derived values

For example:

- New customers
- Churned customers
- Ending customers
- MRR
- ARR
- Revenue
- Gross profit
- EBITDA
- Cash movement
- Ending cash
- Runway

### Statements

Assess whether V1 should include:

- P&L only
- P&L + cash flow
- Full P&L + balance sheet + cash flow

Choose the level that maximises backend/architecture learning without letting accounting complexity dominate the project.

Explain your reasoning.

---

## 4. API specification

Design the API.

Potential actions may include:

- Create company
- Get company
- Create scenario
- Get scenario
- Update scenario assumptions
- Delete scenario
- Calculate scenario
- Compare scenarios
- List scenarios

For every endpoint specify:

- HTTP method
- URL
- Purpose
- Request body
- Response body
- Expected status codes
- Validation rules
- Likely failure cases

Do not create unnecessary endpoints.

Also explain why each HTTP method is appropriate.

---

## 5. Database design

Design the relational database.

Show:

- Tables
- Columns
- Data types
- Primary keys
- Foreign keys
- Constraints
- Relationships
- Indexes

Provide an ER diagram in simple text form.

Explain why each table exists.

Explain what we deliberately do **not** persist.

I want to understand:

> What belongs in the database versus what should be recalculated?

---

## 6. SQL learning

Identify the SQL queries I should deliberately write or inspect during this project.

I do not want SQLAlchemy to mean I never learn SQL.

Create a small set of queries that will teach me:

- basic SELECT
- filtering
- JOINs
- aggregation
- insertion
- update
- delete
- indexing intuition

Tie each query to an actual application feature.

---

## 7. Backend architecture

Propose the application structure.

For example, assess whether something like this is appropriate:

```text
app/
    main.py
    api/
    schemas/
    domain/
    services/
    models/
    repositories/
    db/
    tests/
```

Do not create layers merely to imitate enterprise software.

Use the simplest architecture that clearly separates:

- HTTP
- validation
- business logic
- persistence

Explain what belongs in each layer.

Provide a simple architecture diagram.

---

## 8. Request lifecycle

Take one example such as:

> Create a downside scenario.

Walk through exactly what happens from:

HTTP request\
→ FastAPI route\
→ Pydantic validation\
→ service/domain logic\
→ financial model\
→ SQLAlchemy\
→ SQL\
→ PostgreSQL\
→ transaction commit\
→ response serialization\
→ HTTP response

I want this lifecycle to become a core mental model.

---

## 9. Python learning objectives

Identify the Python concepts the project naturally requires.

For each concept, explain:

- Where it appears in the project
- Why I need it
- What I should be able to explain afterward

Do not create a separate Python course.

Teach concepts when they become necessary.

---

## 10. Database learning objectives

Do the same for:

- SQL
- PostgreSQL
- transactions
- indexes
- constraints
- relationships
- migrations

I want project-driven learning, not a detached database curriculum.

---

## 11. Validation and error handling

Design how the application should handle cases such as:

- Negative prices
- Churn above 100%
- Missing assumptions
- Non-existent company
- Non-existent scenario
- Duplicate names if relevant
- Database failures
- Invalid IDs
- Calculation failure

Explain which errors belong at:

- validation layer
- domain layer
- persistence layer
- API layer

This distinction is important for my learning.

---

## 12. Testing strategy

Define the testing pyramid for this project.

Separate:

### Unit tests

Especially financial calculations.

### API tests

Request/response behaviour.

### Integration tests

Backend + database.

### Database-specific tests

Constraints, persistence and transactions.

For each category, give representative examples.

Do not test every trivial implementation detail.

---

## 13. Migrations

Design at least one intentional schema evolution during the project.

For example:

V1 database\
→ later add scenario description / version / created timestamp.

I want to experience:

- creating a migration
- applying it
- inspecting it
- rolling it back if appropriate

Do not let Alembic remain a magical command I run without understanding it.

---

## 14. Observability and debugging

Keep this lightweight but real.

Define:

- useful application logs
- useful error information
- how to inspect requests
- how to inspect PostgreSQL
- how to see generated SQL
- how to trace a failed API request

Give me a debugging workflow.

---

## 15. Security basics

Security is not the primary objective of Project 2, but I should begin learning secure habits.

Include only foundational issues such as:

- input validation
- parameterised queries / ORM safety
- secrets in environment variables
- database credentials
- least privilege at a basic level
- not exposing internal errors unnecessarily

Explicitly park production authentication/authorization for the later full-stack/security project.

---

## 16. Git and development workflow

Recommend a simple professional workflow covering:

- branches if useful
- commits
- pull requests if useful for solo development
- issue/task tracking
- `.gitignore`
- environment files
- dependency files
- README

Avoid process theatre.

---

## 17. Milestones

Break the build into approximately **5–7 cumulative milestones**.

Every milestone must result in observable functionality.

For each milestone specify:

### What I build

### Backend concepts I learn

### Database concepts I learn

### Business concepts I reinforce

### Tests I should write

### Definition of done

A possible progression might resemble:

1. Pure Python financial engine
2. First API endpoint
3. PostgreSQL persistence
4. Scenario CRUD
5. Scenario comparison
6. Migrations + robustness
7. Integration/deployment

But redesign this if there is a better sequence.

---

## 18. Definition of finished

Create a strict final checklist.

At minimum I expect:

- Backend runs reliably
- API documented
- PostgreSQL persistence works
- CRUD works correctly
- Financial calculations are correct
- Scenarios can be compared
- Important inputs are validated
- Database relationships/constraints are sensible
- Migrations work
- Unit tests exist
- API tests exist
- Integration tests exist
- Code is organised
- README explains setup and architecture
- Schema/ER diagram documented
- API can be demonstrated externally
- I can explain the complete request lifecycle without AI

Improve this list where appropriate.

---

## 19. Technical mastery check

At the end, give me challenging questions I should be able to answer without AI.

Include questions such as:

- What happens when POST /scenarios is called?
- What is HTTP doing for us?
- Why POST rather than GET?
- What does Pydantic do?
- What does FastAPI do?
- What does SQLAlchemy do?
- What does PostgreSQL do?
- What SQL was actually executed?
- What is a transaction?
- Why do we need foreign keys?
- What is an index and what trade-off does it introduce?
- What is a migration?
- What happens if two operations partially fail?
- What belongs in the database versus being derived?
- Why shouldn't routes contain all the business logic?
- Where would I debug a 422 versus a 500?
- How would Project 1 call this backend?
- What would have to change to support multiple real users later?

Make this rigorous enough to reveal whether I genuinely understand the backend.

---

# AI coding tools

I expect to use AI coding tools during this project.

I want AI to accelerate development but not eliminate understanding.

When helping me implement something:

1. Explain the concept before or alongside the code.
2. Keep generated code small enough that I can reason about it.
3. Ask me to predict behaviour where useful.
4. Help me inspect what frameworks generate underneath.
5. Encourage me to debug before replacing large pieces of code.
6. Periodically test whether I can explain the architecture myself.

I should not finish with 10,000 lines of backend code I cannot navigate.

---

# Important scope rule

We are designing only:

# Project 2 — Financial Scenario Engine

If something belongs primarily to:

- authentication
- production security
- cloud architecture
- advanced CI/CD
- data engineering
- external integrations
- machine learning
- LLMs
- RAG
- agents
- distributed systems

label it:

**PARK FOR LATER**

rather than expanding Project 2.

The objective is to complete a focused backend project, deploy or expose it sufficiently to demonstrate it, and emerge with a strong mental model of:

**HTTP + Python backend + business logic + SQL + relational databases + persistence + testing.**

Start by giving me:

1. Your recommended one-paragraph product definition
2. The proposed V1 scope
3. The key architectural decisions

Then build the full engineering specification from there.