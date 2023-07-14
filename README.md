# Microservices Directory

## Domain Services

### Treetracker API

Source Code: [https://github.com/Greenstand/treetracker-api](https://github.com/Greenstand/treetracker-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/treetracker/](https://{env}-k8s.treetracker.org/treetracker/)

Internal Endpoint: [http://treetracker-api.treetracker-api](http://treetracker-api.treetracker-api)



### Field Data API

Source Code: [https://github.com/Greenstand/treetracker-field-data](https://github.com/Greenstand/treetracker-field-data)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/field-data/](https://{env}-k8s.treetracker.org/field-data/)

Internal Endpoint: [http://treetracker-field-data.field-data-api/](http://treetracker-field-data.field-data-api/)



### Stakeholder API

Source Code: [https://github.com/Greenstand/treetracker-stakeholder-api](https://github.com/Greenstand/treetracker-stakeholder-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/stakeholder/](https://{env}-k8s.treetracker.org/stakeholder/)

Internal Endpoint: [http://treetracker-stakeholder-api.stakeholder-api/](http://treetracker-stakeholder-api.stakeholder-api/)



### Earnings API

Source Code: [https://github.com/Greenstand/treetracker-earnings-api](https://github.com/Greenstand/treetracker-earnings-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/earnings/](https://{env}-k8s.treetracker.org/earnings/)

Internal Endpoint: [http://treetracker-earnings-api.earnings-api/](http://treetracker-earnings-api.earnings-api/)



### Regions API

Source Code: [https://github.com/Greenstand/treetracker-regions-api](https://github.com/Greenstand/treetracker-regions-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/regions/](https://{env}-k8s.treetracker.org/regions/)

Internal Endpoint: [http://treetracker-regions-api.regions-api/](http://treetracker-regions-api.regions-api/)



### Messaging API

Source Code: [https://github.com/Greenstand/treetracker-messaging-api](https://github.com/Greenstand/treetracker-messaging-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/messaging/](https://{env}-k8s.treetracker.org/messaging/)

Internal Endpoint: [http://treetracker-messaging-api.messaging-api/](http://treetracker-messaging-api.messaging-api/)



### Map Tile Service

Source Code: [https://github.com/Greenstand/node-mapnik-1](https://github.com/Greenstand/node-mapnik-1)

CDN Endpoint:  [https://tiles1.treetracker.org/](https://tiles1.treetracker.org/), also tiles2, tiles3, tiles4

Mounted Endpoint: [https://{env}-k8s.treetracker.org/tiles/](https://{env}-k8s.treetracker.org/tiles/)

### Grower Account Query Service

Source Code: [https://github.com/Greenstand/treetracker-grower-account-query](https://github.com/Greenstand/treetracker-grower-account-query)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/query/](https://{env}-k8s.treetracker.org/query/)

Internal Endpoint: [http://treetracker-grower-account-query.query/](http://treetracker-grower-account-query.query/)



### Web Map Query Service Consumer

Source Code: [https://github.com/Greenstand/webmap-query-service-consumer](https://github.com/Greenstand/webmap-query-service-consumer)

This queue message consumer exposes no API



## Bulk Pack Services

### Bulk Pack Consumer

Source Code: [https://github.com/Greenstand/bulk-pack-consumer](https://github.com/Greenstand/bulk-pack-consumer)

This queue message consumer exposes no API



### Bulk Pack Processor

Source Code: [https://github.com/Greenstand/bulk-pack-processor](https://github.com/Greenstand/bulk-pack-processor)

This scheduled job exposes no API



### Bulk Pack Transformer V1

Source Code: [https://github.com/Greenstand/bulk-pack-transformer](https://github.com/Greenstand/bulk-pack-transformer)

Mounted Endpoint: not mounted

Internal Endpoint: [http://bulk-pack-transformer.bulk-pack-services/](http://bulk-pack-transformer.bulk-pack-services/)



### Bulk Pack Transformer V2

Source Code: [https://github.com/Greenstand/bulk-pack-transformer-v2](https://github.com/Greenstand/bulk-pack-transformer-v2)

Mounted Endpoint: not mounted

Internal Endpoint: [http://bulk-pack-transformer-v2.bulk-pack-services/](http://bulk-pack-transformer-v2.bulk-pack-services/)

## Legacy Services

### Admin API

Source Code: [https://github.com/Greenstand/treetracker-admin-api](https://github.com/Greenstand/treetracker-admin-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/api/admin/](https://{env}-k8s.treetracker.org/api/admin/)

Internal Endpoint: [http://treetracker-admin-api.admin-api/](http://treetracker-admin-api.admin-api/)



### Web Map API

Source Code: [https://github.com/Greenstand/treetracker-web-map-api](https://github.com/Greenstand/treetracker-web-map-api)

Mounted Endpoint: [https://{env}-k8s.treetracker.org/webmap/](https://{env}-k8s.treetracker.org/webmap/)

Internal Endpoint: [http://treetracker-webmap-api-ambassador-svc.webmap/](http://treetracker-webmap-api-ambassador-svc.webmap/)

## Cloud Services

### Airflow API

### CKAN API

