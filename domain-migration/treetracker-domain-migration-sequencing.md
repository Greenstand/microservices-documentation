# Treetracker Domain Migration Sequencing

#### Migration Sequence

1. Migrate all legacy 'tree' table data into the field_data.raw\__capture table
   1. Includes creation session and device records for these captures
2. Admin panel application: split capture verification tool from capture search tools.
3. Go through the migration process for capture verification
   1. Documentation: [https://github.com/Greenstand/system-design-docs/blob/master/domain-migration/project\_plan.md](https://github.com/Greenstand/system-design-docs/blob/master/domain-migration/project\_plan.md)
   2. Steps
      1. Milestone 1: Get rabbitmq verification messages functioning all the way through into production&#x20;
         1. Get it working on dev infra
         2. Release and test on test infra
         3. Release and test on beta and prod infra
      2. Milestone 2: Update admin panel to move approved data from field\_data.raw\_capture to treetracker.capture in the verification process (using the treetracker API), but for capture search still pulls from legacy database (using the legacy API)
         1. Get it working on dev infra
         2. Release and test on test infra
         3. Release and test on beta and prod infra
4. Migrate all remaining approved legacy 'tree' table data into the treetracker.capture table
   1. Apply to dev
   2. Apply to test
   3. Apply to prod
5. Consolidation step to fix all planting organization assignments
   1. Priority between planting org per planter, per tree, and reported in field data to be determined
   2. Clean up all capture records to have valid organization assignments in the stakeholder tool.
6. Update admin panel to using treetracker API for capture search tools.
7. \*Now, ready to get the capture matching tool working in deployment\*
8. GIS task: Identify very small geographic area in Freetown as a pilot for capture matching, and supply this as a spatial shape file (.geojson or .shp)
9. GIS task: Identify all the capture records in the small geographic area that are the initial captures of the tree.
10. Extract production data from small geographic area and add that data to dev and test database.
11. Data task: insert treetracker.tree records for each initial capture.  Now we have trees to capture match against.
    1. Perform in dev, test, and prod
12. Implement capture matching frontend feature to allow filtering trees _and_ captures by named geographic area.  We will filter for initial use by the small geographic area defined above, which should be loaded into the regions API.
13. Now we can deploy the capture matching tool to the beta infrastructure and try it out.

#### Notes:&#x20;

1. Some legacy planter registrations reported to not have device identifier. &#x20;
   1. This is inconvenient but not fixable with the v2 bulk pack format
