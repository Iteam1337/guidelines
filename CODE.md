# CODE

## Purpose

This is a guide that describes how we strive to work with code at Iteam. While things may differ slightly between projects and customers, there are many similarities as well. Some common denominators in all projects are that we strive to be fast-paced, flexible and work with clear intention.

The methods and tools we use keep evolving as Iteam grows and we learn new things, one big reason for this is if course that the tech and IT world keeps changing and we need to keep up. Our motto, "There is a better way", also plays a big part in this, as it part of our nature to find newer and better ways of doing things.

## Culture

Iteam's developer culture is deeply influenced by our key values; doing good, producing value and having fun. The "having fun" part includes anything from the satisfaction of making customers happy to actually loving writing code. Doing good and producing value is about what we actually do for our customers and who they are.

Our teams are relatively small and all of our developers are expected to communicate directly with customers. We do not use the traditional project leader role in any project as proxy for day-to-day questions and work. In the same sense, we expect customers to be available and involved in what we do.

As consultants we need to keep the customer's time and money in mind. Therefore we strive to be flexible and transparent in the way we work. We are not only building software that customers are asking for, we are helping them to find out what they want and why they need it.

Iteam gives its employees a lot of space to learn, explore and grow both within and outside of their respective roles. This means that developers often get to work with unfamiliar technologies and tools. Many projects introduce new kinds of problems to solve and the need for us to learn new things as well as find new, better, ways to do things we already know.

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
