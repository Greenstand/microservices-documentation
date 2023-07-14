# Domain Migration M2



Goal: Admin panel to not read `trees` table directly. Build new treetracker service with API to create capture records.

### **Build a new service to be the source of truth of all approved captures.**&#x20;

#### This service is to own all the capture records along with tagging and other details created during the approval in the admin panel.&#x20;

* Service is already created, known as treetracker-api. &#x20;
* Some verbs (GET/POST/PATCH) may be missing but capture, tree, and planter resources have been defined.
* We may need to add additional search parameters as needed by other services or for domain goals.

#### On creation of a capture record, emit events indicating the creation of the capture record to a Topic.  This event is meant for web-map to build a view of all approved captures.&#x20;

* This appears to be implemented, but has not been tested or operated

#### The scope of this capture service is yet to be determined if it can own more than just capture records. We could call this as captures service or treetracker-capture-records.

* We added planter (ground\__user)_ and tree to this service already.  That will be the scope of the service.  The service is called treetracker serivce, and is stored in the treetracker-api repository



### Change Admin panel

#### Change Admin panel to use field data API instead of directly reading `trees` table for tree capture verification.&#x20;

* Data populated in the admin panel verify tool, should ONLY be raw captures from the field data service that has not been verified (status=unprocessed)
* This will require the admin panel frontend team to split the current verify tool into a 'verification' tool and a 'capture edit' tool.
* Only verified captures can be 'edited' through the 'capture edit' tool, and only very limited fields can be edited. mostly this is tagging.
* Later, there will also be some tools for cleaning field data, but that's out of scope for now.

#### Admin panel to invoke capture service API to record the approved capture, update the trees table as usual and then update field data service to mark the data as approved/rejected.&#x20;

* (1) POST to treetracker/capture&#x20;
* (2) PATCH to the legacy admin panel API
* (3) PATCH back to the field service to mark as approved/rejected in field data schema.
* TODO: Think through what happens if one of these calls fails.
  * I think it's ok, it just causes some work to be repeated.
  * For instance, if POST to (1) succeeds but PATCH to (2) fails,&#x20;
    * Then raw capture will need to be reverified (because (3) did not execute)
    * So the data will just be reprocessed by the operator in this case
  * We will probably resolve this by using an orchestration layer
    * The treetracker service itself can handle the orchestration, and also keep track of failed requests to (2) and (3) to retry.
    * This could also use a queue, or implement a separate service to handle the orchestration.
    * To some extent, this decision is up to the engineer implementing this step of the domain migration.
    * ![](<../.gitbook/assets/image (13).png>)



* Remove the feature that emitted event for approved captures from Change 1 earlier (in the legacy API). The reason we will write to trees table from admin panel (or orchestration layer) is for back-ward compatability with web-map.

#### Add a consumer for the capture creation events in the web-map layer and build a view for all captures in web-map specific db.

* This appears to already be complete.  Need to be tested and operated.

**Migrate data from `trees` table in main db to `captures` table in the new captures service of all approved tree entries.**

* ETL job.  Can be implemented as one-off airflow job.

**Update token generation process and refer to ids from captures instead of trees as reference association.**&#x20;

* This refers to the token minting scripts, now being run in airflow
* capture\_id for each token needs to reference the id of treetracker.capture rather than public.trees.  This also requires updating the HATEOAS link in the token payload (wallet API) to point to the new capture service.
* Update all existing tokens to use treetracker.capture.id as capture\_id

#### Wallet API service to emit events when transfer of tokens occur to be consumed by web-map layer for Impact owner view.&#x20;

* The events consumed in web-map layer will trigger api calls to get the tokens impacted and update the capture view in the web-layer to assign the updated wallet owner.
* Requires endpoint to look up all tokens in any transfer by transfer id.

#### Trigger discussion about impact manager map (the view in web-map for planter orgs) in the web-map layer and its needs to shape and update milestone 3.

* Discuss how organizational hierarchy is captured in the webmap schema (JSON blob or table structure)

#### Address domain naming issues (variable and class names)

* Breaking changes will trigger a new major revision, and a new deployment mount point&#x20;
  * Frontend engineers will be responsible for migrating to the new mount point
  * If database changes are necessary, if the service is not in production it's ok to make a breaking change.  Otherwise check with engineering leadership.
* planter, grower, and fielduser should all become 'ground\_user'
* planteridentifier should become  'ground\_username'
* planter class, table, and API resource should become 'ground\_user'
