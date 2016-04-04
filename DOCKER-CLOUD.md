# Docker Cloud

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
