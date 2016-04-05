# Docker Cloud

## Versioning

When using external images, always figure out which version you want. Do not simply use :latest as it might change over time and cause unexpected problems.

## Deployment

### Strategy

#### emptiest_node

Used for test/dev

#### High availability

Used for production containers, Docker Cloud will make sure these are always up.

#### every_node

Used for proxies and such helper containers.

### Container count

#### target_num_containers

Always make sure you set this attribute so that it is present in the stack file right from the start.

## Naming

### Stacks

Stacks should be named descriptively mentioning the project name and what part of the development cycle it corresponds to.

Example:
```
Iteam-se-prod
Iteam-se-develop
```

### Services

Every service should belong to a stack, orphaned services are a bit harder to manage on accounts with a large amount of services.

Servies should be named descriptile, mentioning the stack, development cycle and what they are.

For example, a stack called Iteam-prod might have these services:
```
iteam-se-web-prod
iteam-se-rethinkdb-prod
```

## Tagging

### Nodes

Nodes should have tags that describe their relevant properties and environment. For example *Amsterdam*, *Stockholm*, *Digital-Ocean*, *SSD*, *Fast-Storage*, *Redundant-Storage*

The tags *on-premise* and *off-site* should be used to describe whether a node is physically located on the site of a customer (or our office) or if located in the cloud or similar shared locations.

When it is necessary to keep environments separated, tags such as *Production* or *Development* should be used.

### Services

When deploying services, you should always plan ahead and use tags to make sure the containers will end up on the nodes intended for them.

Simply deploying a service without any tags will make Docker Cloud deploy it on whichever node that is currently the emptiest one.
