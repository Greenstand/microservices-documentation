# Capture Verification

![](<.gitbook/assets/image (3).png>)



1. Update to 'verified' status requested to treetracker API
2. Start transaction against treetracker schema to insert a new capture record
   1. If the record already exists, that's OK, just accept.
3. Call legacy API and update capture (trees table record) to approved
4. Commit transaction on treetracker schema
5. Call field data API and update raw\_capture record to approved

if (3) fails, we rollback the treetracker schema transaction, therefore the raw\_capture record remains unprocessed, and will be reprocessed by an operator in the future,  **should** bring data into consistency.

if (4) fails, same as if (3) fails, we no update.  Will be reprocessed

if (5) fails, the record will be reprocessed



When we POST to captures/, send the UUID of the raw\_capture to become the UUID of the approved capture record - these should always be unique.

* Allows for easy reprocessing when there are outages
* Allows for multiple concurrent POST messages to be collapsed and only create 1 capture record

