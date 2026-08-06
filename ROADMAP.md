# Spring Boot Course Roadmap (0 → 3 YOE Interview-Ready)

> Detailed chapter-wise subtopic breakdown. See `SESSION_CONTEXT.md` for live progress tracking.

## Chapter 1: Spring Fundamentals
- What is Spring Framework? Why Spring?
- IoC (Inversion of Control)
- Dependency Injection
- Bean Lifecycle
- Spring Container
- Bean Scopes — Singleton, Prototype, Request, Session
- Core annotations — @Component, @Service, @Repository, @Controller, @RestController, @Configuration, @Bean, @Autowired
- Constructor Injection, Setter Injection, Field Injection
- @Primary, @Qualifier
- Lazy Initialization
- Circular Dependency

## Chapter 2: Spring Boot Basics
- Why Spring Boot?
- Spring Boot Architecture
- Starter Dependencies
- Auto Configuration
- Spring Initializr
- Embedded Tomcat
- application.properties / application.yml
- Profiles
- CommandLineRunner
- Logging
- External Configuration
- @ConfigurationProperties
- @Value

## Chapter 3: REST API Development
- REST Principles
- HTTP Methods — GET, POST, PUT, PATCH, DELETE, OPTIONS, HEAD
- Request Mapping (@RequestMapping, @GetMapping, etc.)
- @PathVariable
- @RequestParam
- @RequestBody
- ResponseEntity
- Response Status
- Request/Response Headers
- Content Negotiation
- JSON Serialization (Jackson)
- DTO (Data Transfer Object)
- Validation — @Valid, @NotNull, @Size, @Email, Custom Validation

## Chapter 4: Spring Data JPA
- ORM concepts
- Hibernate
- Entity, Table Mapping, Column Mapping
- Primary Key, @GeneratedValue
- CrudRepository, JpaRepository, PagingAndSortingRepository
- Derived Query Methods
- JPQL
- Native Query
- Pagination
- Sorting
- Transactions
- Lazy Loading vs Eager Loading
- Cascade Types
- Entity Relationships — OneToOne, OneToMany, ManyToOne, ManyToMany
- Fetch Types
- Optimistic Locking
- N+1 Problem
- Auditing

## Chapter 5: Exception Handling
- try-catch basics recap
- Custom Exceptions
- Global Exception Handler
- @ControllerAdvice
- @ExceptionHandler
- Error Response Standardization

## Chapter 6: Layered Architecture
- Controller Layer
- Service Layer
- Repository Layer
- DTO Layer
- Entity Layer
- Mapper Classes
- Utility Classes
- Constants
- Validation Layer

## Chapter 7: Spring Security
- Authentication vs Authorization
- Security Filter Chain
- BCryptPasswordEncoder
- JWT (JSON Web Token)
- Login Flow
- Refresh Token
- Roles
- Authorities
- Method Security
- CORS
- CSRF
- Stateless Authentication

## Chapter 8: Spring Boot Advanced
- Bean Lifecycle Callbacks
- Profiles (deep dive)
- Scheduling (@Scheduled)
- Async (@Async)
- File Upload / File Download
- Multipart Requests
- Email Sending
- Caching (@Cacheable, etc.)
- Swagger / OpenAPI
- Actuator

## Chapter 9: AOP (Aspect-Oriented Programming)
- What is AOP?
- Aspect
- Advice
- Join Point
- Pointcut
- Around Advice
- Before Advice
- After Advice
- Logging using AOP
- Performance Monitoring using AOP

## Chapter 10: Testing
- JUnit 5
- Mockito
- @MockBean
- Unit Testing
- Integration Testing
- TestContainers (basic understanding)
- AssertJ
- MockMvc

## Chapter 11: Microservices Basics
- Why Microservices
- Monolith vs Microservices
- Service Communication
- RestTemplate
- WebClient
- OpenFeign
- Config Server
- API Gateway
- Circuit Breaker
- Resilience4j
- Distributed Logging (basic)

## Chapter 12: Production Concepts
- Logging, Logback
- Profiles & Environment Variables
- Secrets Management
- Health Checks
- Metrics
- Graceful Shutdown
- Docker Basics
- Deployment Basics

## Chapter 13: SQL + JPA Deep Dive
- Joins
- Group By, Having
- Aggregate Functions
- Subqueries
- Window Functions (basic)
- Indexes
- Normalization
- Transactions
- ACID
- Isolation Levels

## Chapter 14: Design Patterns in Spring
- Singleton Pattern
- Factory Pattern
- Builder Pattern
- Strategy Pattern
- Proxy Pattern
- Template Method Pattern
- Dependency Injection Pattern
- MVC Pattern

## Chapter 15: Interview Prep + Projects
**Consolidated Interview Q&A:**
- How does Spring Boot start? What happens after `main()`?
- How does auto-configuration work?
- How does @Autowired work internally?
- Bean lifecycle (deep dive)
- DispatcherServlet flow
- Request lifecycle
- Transaction flow
- Hibernate session, first-level cache, second-level cache
- Lazy vs Eager loading (interview framing)
- Why DTO? Why Service layer? Why Repository layer?
- @Component vs @Service vs @Repository
- @Controller vs @RestController
- @Bean vs @Component
- CrudRepository vs JpaRepository

**Practice Projects:**
1. Employee Management System (CRUD)
2. Hospital Management System
3. E-commerce Backend
4. JWT Authentication System
5. Library Management System
6. URL Shortener (intermediate)
7. Banking API (transactions)
8. Expense Tracker

## Chapter 16: Legacy / Low-Priority Topics (Covered Last)
_These are asked occasionally in interviews or exist in older codebases, but are low-priority for current industry practice. Covered only after Chapter 15, and kept brief._
- Banner customization (Spring Boot startup banner)
- @NamedQuery (JPA) — mostly replaced by JpaRepository derived methods / @Query
- DevTools (developer productivity tool, not core concept)
- Eureka Service Discovery — still asked in interviews, but many companies now use Kubernetes-native discovery or Consul instead
- SQL Window Functions — good-to-know depth, rarely required at 0-3 YOE level
- Field Injection — shown only to recognize it in legacy code; constructor injection is the industry-preferred approach (already taught as the default in Chapter 1)