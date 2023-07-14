# Treetracker Schema Attributes

\*\*Capture\*\*

| id                              | Not null, default uuid(), immutable                  |
| ------------------------------- | ---------------------------------------------------- |
| reference\_id                   | Nullable, immutable                                  |
| session\_id                     | Not null, immutable                                  |
| tree\_id                        | Nullable, immutable but clearable                    |
| image\_url                      | Not null, immutable                                  |
| lat                             | Not null, immutable                                  |
| lon                             | Not null, immutable                                  |
| gps\_accuracy                   | Not null, immutable                                  |
| estimated\_geometric\_location  | Not null, immutable                                  |
| estimated\_geographic\_location | Not null, immutable                                  |
| _planter\_id_                   | Not null, immutable                                  |
| _planter\_photo\_url_           | Not null, immutable                                  |
| _planter\_username_             | Not null, immutable                                  |
| planting\_organization\_id      | Not null, immutable                                  |
| device\_configuration\_id       | Not null, immutable                                  |
| species\_id                     | Nullable, mutable (for now)                          |
| morphology                      | Nullable, mutable (for now)                          |
| age                             | Nullable, mutable (for now)                          |
| attributes                      | Nullable, immutable                                  |
| note                            | Nullable, immutable                                  |
| domain\_specific\_data          | Nullable, immutable                                  |
| status                          | Not null, mutable                                    |
| created\_at                     | Default now() on create, not null, immutable         |
| updated\_at                     | Default now() on create or update, not null, mutable |

\*\*Tree\*\*

| id                              | Not null, default uuid(), immutable                  |
| ------------------------------- | ---------------------------------------------------- |
| latest\_capture\_id             | Not null, mutable                                    |
| image\_url                      | Not null, mutable                                    |
| lat                             | Not null, immutable                                  |
| lon                             | Not null, immutable                                  |
| gps\_accuracy                   | Not null, immutable                                  |
| estimated\_geometric\_location  | Not null, immutable                                  |
| estimated\_geographic\_location | Not null, immutable                                  |
| species\_id                     | Nullable, mutable (for now)                          |
| morphology                      | Nullable, mutable (for now)                          |
| age                             | Nullable, mutable (for now)                          |
| attributes                      | Nullable, immutable                                  |
| status                          | Not null, mutable                                    |
| created\_at                     | Default now() on create, not null, immutable         |
| updated\_at                     | Default now() on create or update, not null, mutable |

\*\*Tag\*\*

| id          | Not null, default uuid(), immutable                  |
| ----------- | ---------------------------------------------------- |
| name        | Not null, immutable                                  |
| public      | Not null, mutable                                    |
| status      | Not null, mutable                                    |
| created\_at | Default now() on create, not null, immutable         |
| updated\_at | Default now() on create or update, not null, mutable |

\*\*Capture\_Tag\*\*

| id          | Not null, default uuid(), immutable                  |
| ----------- | ---------------------------------------------------- |
| capture\_id | Not null, immutable                                  |
| tag\_id     | Not null, immutable                                  |
| status      | Not null, mutable                                    |
| created\_at | Default now() on create, not null, immutable         |
| updated\_at | Default now() on create or update, not null, mutable |

\*\*Tree\_Tag\*\*

| id          | Not null, default uuid(), immutable                  |
| ----------- | ---------------------------------------------------- |
| tree\_id    | Not null, immutable                                  |
| tag\_id     | Not null, immutable                                  |
| status      | Not null, mutable                                    |
| created\_at | Default now() on create, not null, immutable         |
| updated\_at | Default now() on create or update, not null, mutable |

\*\*Grower\_Account\*\*

| id                      | Not null, default uuid(), immutable                               |
| ----------------------- | ----------------------------------------------------------------- |
| wallet\_id              | Not null, immutable                                               |
| wallet                  | Not null, immutable                                               |
| person\_id              | Nullable, uuid of stakeholder                                     |
| organization\_id        | Nullable, uuid of stakeholder                                     |
| name                    | Not null, mutable                                                 |
| email                   | Nullable, mutable - one of email or phone required to be non-null |
| phone                   | Nullable, mutable - one of email or phone required to be non-null |
| image\_url              | Not null, mutable                                                 |
| image\_rotation         | Default 0, not null                                               |
| status                  | Not null, default active                                          |
| first\_registration\_at | Immutable, timestamp of first field registration                  |
| created\_at             | Default now() on create, not null, immutable                      |
| updated\_at             | Default now() on create or update, not null, mutable              |

\*\*Status Enumeration\*\* active deleted Session - Field Data Schema Device Configuration - Field Data Schema
