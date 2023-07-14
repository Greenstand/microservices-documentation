---
description: Bulk Pack Processing v2
---

# Bulk Pack

Field data schem

![](<.gitbook/assets/image (2).png>)

## Ingestion Process by Entity Type

### wallet\_registration

Wallet registrations need to be stored in the field data schema in the wallet\_registrations table, but they also need to be used to upsert (create or update) grower account records in the treetracker API.  A wallet registration also needs the grower account id field populated.

#### Suggested workflow:

1. Bulk pack transformer calls PUT on grower\_account in treetracker API for grower account with identifier that matches wallet
   1. If account exists, update&#x20;
      1. Only update the name, phone, and email for now
   2. Else, insert&#x20;
      1. Insert identifier, name, phone, email, and photo
2. POST to /planter path on bulk-pack-transformer-1 to populate legacy schema
3. Populate grower account id in wallet registration data, and POST into field data api
   1. If wallet registration id is already present, field data api will do nothing (return 200)
4. Return 200

### device\_configuration

device configuration records are simply inserted in v2, but in v1 they were upserted.&#x20;

#### Suggested Workflow

1. POST device configuration payload to bulk-pack-transformer-1
   1. bulk-pack-transformer-1 returns 200 if already present
2. POST device configuration payload to field data API
   1. field data API returns 200 if already present
3. Return 200

### session

session does not exist in the v1 bulk-pack-transformer.

#### Suggested Workflow

1. POST to session path on field data API
   1. field data API returns 200 if already present
2. Return 200

### capture

1. POST capture data to bulk-pack-transformer-1
   1. If data exists this API returns 200, else a new record is inserted
   2. This API also propagates the record to field data API, where a queue message is emitted
2. POST capture data to field data API
   1. Since step 1 already propagated to this API, a 200 should be returned based on uuid
   2. Since 200 is returned, queue message should not re-emitted



## Orchestration Diagram

Bulk Pack Format v2 : [https://app.gitbook.com/o/-MXNadx4i6aOZ12XcStA/s/-MXtAguKaWMpiXXl0UDb/upload-pack-format](http://127.0.0.1:5000/s/-MXtAguKaWMpiXXl0UDb/upload-pack-format)

#### Improved orchestration architecture

![](<.gitbook/assets/image (4).png>)

#### Deprecated proposal for orchestration

![](<.gitbook/assets/image (5).png>)



![](<.gitbook/assets/image (7).png>)



## Nullable Columns for Field Data Tables

Session

* track\_url
* organization

Wallet Registration

* phone or email is nullable, but not both

Raw Capture

* session\_id is nullable for v1 endpoints only
* reference\_id
* note
* extra\_attributes
* rejection\_reason

Device Configuration

* No nullable fields

## Workflow Notes



Insert 'tree' as 'capture' will fail until corresponding device and registration records have been inserted, because there's no session Once device and registration records are inserted, then it is possible to insert a session id using SESSION UUID = device\_identifier + planter\_identifier In v2 bulk pack endpoint /v1/tree is responsible for ensuring that the session record exists for a v1 tree. This session can then be used as the session for inserting the v1 'tree' record as a v2 'capture' record

1. process sends tree record to /v1/tree in v2
2. v2 calculates SESSION UUID = device\_identifier + planter\_identifier using uuid-string
3. v2 checks for a session that matches this
4. If no session exists, it looks up device\_configuration\_id and wallet\_registration\_id using device\_identifier and planter\_identifier, and if they exist it creates a session record. If they don't exist yet, it fails until next time.
5. Assuming a session exists or was inserted in (4), we can now insert the capture record using his session uuid.

## Release

Old versions:

* greenstand/bulk-pack-processor:1.2.7
* greenstand/bulk-pack-transformer:1.6.2
