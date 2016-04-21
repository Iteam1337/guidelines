# Docker Cloud

## TL;DR;

Here is a good stack file template.

Let's say your stack is called *IteamAPI-production* and you are deploying a production stack.

```
IteamAPI-api-production:
  expose:
    - '80'
  environment:
    - 'VIRTUAL_HOST=http://api.iteam.se'
  deployment_strategy: 'high_availability'
  target_num_containers: 2
  links:
    - 'IteamAPI-rethinkdb-production:rethinkdb'
  tags:
    - off-site
    - production
IteamAPI-rethinkdb-production:
  deployment_strategy: 'high_availability'
  target_num_containers: 1
  tags:
    - on-premise
    - production
    - ssd
```

## Image versioning/tagging

When using external images, always figure out which version/tag you want. Do not simply use :latest as it might change over time and cause unexpected problems.

When building your own images, make sure to use relevant tags such as *develop*, *test* or *production*.

## Naming

### Stacks

Stacks should be named descriptively mentioning the project name and what part of the development cycle it corresponds to.

Example:
```
IteamSE-production
IteamSE-develop
```

### Services

Every service should belong to a stack, orphaned services are a bit harder to manage on accounts with a large amount of services. We use hyphens (-) to separate words. Servies should be named descriptive, mentioning the stack, development cycle and what they are.

For example, a stack called IteamSE might have these services:
```
IteamSE-web-production
IteamSE-rethinkdb-production
```

A stack called IteamAPI-dev might have these:
```
IteamSE-api-develop
IteamSE-api-rethinkdb-develop
```

### Volumes

Data volume naming on the host

```
/data/<production|develop>/<stack>/<service>
```

## Deployment

Development and test services should have *autoredeploy: true* so that they recycle each time a new image is pushed to the registry.

### Container availability

#### target_num_containers

Always make sure you set this attribute so that it is present in the stack file right from the start.

### Strategy

#### emptiest_node

Use for test/dev - will deploy the desired number of containers to whatever nodes that are currently most available.

#### High availability

Use for production containers, Docker Cloud will make sure these are always up.

#### every_node

Used for proxies and such helper containers.

## Tagging

### Nodes

Nodes should have tags that describe their relevant properties and environment. For example *amsterdam*, *stockholm*, *digitalocean*, *ssd*, *redundantstorage*

The tags *on-premise* and *off-site* should be used to describe whether a node is physically located on the site of a customer (or our office) or if located in the cloud or similar shared locations.

When it is necessary to keep environments separated, tags such as *Production* or *Development* should be used.

### Services

When deploying services, you should always plan ahead and use tags to make sure the containers will end up on the nodes intended for them.

Simply deploying a service without any tags will make Docker Cloud deploy it on whichever node that is currently the emptiest one.

## Builds

### Tagging

```
Git branch  | Image tag
------------|----------
develop     | develop
feature/xyz | develop
test        | test
master      | production
```
