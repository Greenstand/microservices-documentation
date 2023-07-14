# Testing Methodology

## Unit Tests

## Integration Tests

* Only access the API, do not perform database check
  * First write seeded tests for GET endpoints
  * Then write tests for create and update that use GET endpoint to validate functionality
* APIs should return created objects, and get queryable via these object Ids
* Seeding should be done using knex, and use the same seeding scenarios provided to the frontend developers
* Best Practices
  * Do specific seeding for each integration test, don't use a generic seed that isn't for the specific test
  * Objects posted to an API should be explicitly expressed within the integration test file (?)
  * Use async syntax
    * `it('should do something', async function() { ...`
  * Log request errors in test to facilitate debugging
    * `if(res.error ) { console.log(res.error); }`
  * Stub functions on a per-test basis
* Running integration tests
  * Use the test-integration-working command to specific a specific test file rather than running all
  * Use .only to specify a single test
  * Don't leave .only in place after getting the test to pass



* TODO
  * Need a solution to print response errors when expect fails on an error code&#x20;
    * [https://github.com/visionmedia/supertest/issues/12](https://github.com/visionmedia/supertest/issues/12)
  * What tests are required?
    * Endpoint behaviors
    * How much validation?
      * Payload structure vs 404 responses
      * JOI tests could be unit tests



