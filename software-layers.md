# Software Layers

## Handler

* HTTP Domain
* All error and success codes
* API payload validation
* Calls a service or a model function

## Service

* Orchestration between services and the domain model
  * Database session
  * External APIs
  * Cloud Services (such as RabbitMQ or S3)

## Model

* Domain logic
* Accesses repositories
* Allowances
  * We allow HTTP 404 errors to be thrown from within the model as a convenience for now

## Repository

* Accesses the database, performs CRUD operations
* One repository for each database table in RDMS
