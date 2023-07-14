# Messaging System Rollout Decisions

1. We will control available authors manually at first, by populating the authors table
2. We will control access to admins using our normal process
3. For announce and survey messages, we look up associated Grower Accounts in the treetracker API, and then match those against enabled authors
   1. We need to extend this approach to respect the organizational hierarchy, which may mean a query service for grower accounts.
   2. A query service for grower accounts would also more easily respect the region filters
