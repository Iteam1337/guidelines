# CODE

## Purpose

This is a guide that describes how we strive to work with code at Iteam. While things may differ slightly between projects and customers, there are many similarities as well. Some common denominators in all projects are that we strive to be fast-paced, flexible and work with clear intention.

The methods and tools we use keep evolving as Iteam grows and we learn new things, one big reason for this is if course that the tech and IT world keeps changing and we need to keep up. Our motto, "There is a better way", also plays a big part in this, as it part of our nature to find newer and better ways of doing things.

## Overview

TODO: Graphics, development workflow

We are using Docker and Docker Cloud (previously Tutum) to support our entire development chain all the way up to production hosting.

 - Each project has a docker-compose yaml that is runnable locally by developers
 - Development is done locally, unit tests are written and run locally as well to ensure no bad code is pushed
 - Code is stored at GitHub, usually in a repository owned by the customer
 - When code is pushed to develop or master branch, Docker Cloud builds a new image (and runs tests)
 - When a new image is created, the Docker service that corresponds to that branch/tag is updated
 - When a new feature is to be released, it is merged to the master branch

## Docker

### Development

### Automatic builds/deployment

### DevOps
