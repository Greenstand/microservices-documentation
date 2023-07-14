# Team Projects

#### Schema support for db-migrate

* We decided to assign search\_path to each microservice user (service and migration users) in terraform to resolve this need.&#x20;

#### Developer Productivity

* Codeowners file and agreements
* Document observability tools and access
  * ELK: [\`](https://dev-k8s.treetracker.org/extauth/kibana/)kubernetes.container.image :"greenstand/treetracker-api:1.4.0"
    * deployed image version can be found by visiting the root path of any deployed api
    * (such as [https://dev-k8s.treetracker.org/messaging/](https://dev-k8s.treetracker.org/messaging/))
    * kubernetes.container.name: "treetracker-api"
    * u: admin p:xRrE6vZDUcRph%1P%0H
  * grafana  (Performance monitoring)
* Document about how deployment to dev environment works.
* Figure out if dicpher can work with node16 or if there is a replacement (npm run decrypt)&#x20;
  * Password for dipher is pinned

#### Improve Documentation

* [https://www.conventionalcommits.org/en/v1.0.0/](https://www.conventionalcommits.org/en/v1.0.0/)
* Sealed secrets: treetracker-infrastructure/sealed-secrets/scripts/create-database-secret.sh

#### Improve Microservices Template

* resolve all lint warnings
  * Update lint settings to our likely - are there rules we want to enable?
* remove co-mocha?
  * YES, remove from the template
* require lint errors to be removed to commit. &#x20;
  * Reject on warnings in CI, but not in husky
  * Reject on errors in husky
  * Quaid adding his settings to microservice template
* Resolve all vulnerabilities
  * Check for vulnerabilities when a new PR comes in.
*   Resolve dependencies errors for test files

    ```
      import/no-extraneous-dependencies: [error, { devDependencies: true }]
    ```

    \
    \* [https://eslint.org/docs/user-guide/configuring/rules](https://eslint.org/docs/user-guide/configuring/rules)

    * `"import/no-extraneous-dependencies": [ "error", { "devDependencies": ["`**`/*.test.js", "`**`/*.spec.js"] } ]`
