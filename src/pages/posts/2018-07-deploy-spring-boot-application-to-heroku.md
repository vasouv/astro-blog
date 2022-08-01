---
layout: "../../layouts/BlogPost.astro"
title: "Deploying Spring Boot to Heroku"
description: "How to deploy a Spring Boot application to Heroku"
publishDate: "12 Jul 2018"
categories: 
  - "heroku"
---

Heroku supports a couple of ways to deploy an application. One is with the Heroku CLI and another is by using a GitHub repository.

Since I don't have private repositories on GitHub and I don't want to show "production" info publicly, I'm probably going the CLI way to deploy applications.

In case I lose my heroku remote from the repo, these steps must be followed for my diet-logs backend project.

Steps:

1. remove application.properties active profile
2. add to application-prod.properties
3. change CORS in controllers to show the Angular URL
4. create Procfile

`web java -Dserver.port=$PORT -Dspring.profiles.active=prod $JAVA\_OPTS -jar target/diet-logs-0.0.1-SNAPSHOT.jar`

To push the local master branch to heroku:

`git push heroku master`

To push the current (non-master) branch to the heroku master:

`git push heroku testBranch:master`
