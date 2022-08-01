---
layout: "../../layouts/BlogPost.astro"
title: "PostgreSQL Docker container for development"
description: "How to run a PostgreSQL Docker container for local development"
publishDate: "08 May 2018"
categories: 
  - "docker"
---

I use PostgreSQL for development and I keep it installed on my machine, since I usually make the DB tables first and then start coding on the application. Also I populate the tables with test data to have something to actually see when I'm retrieving data.

With Docker there's the option not to install databases locally and instead run containers with or without persistent volumes. It's also the best option to collaborate with someone, if there's not an online database to use.

I don't particularly like the idea of persistent volumes, although I see their appeal. It's just for me, I could much easier install the actual database on my machine and not mess with Docker. I think I prefer to just run the DB container and manually add my test data via a GUI. Not a big issue really although it's manual.

I'm using Docker Compose because I can just go in the directory and run "docker-compose up" to start the db, without having to remember the "docker run" command. Plus, I can add my app service if I want to. And the handy thing with Docker Compose is that it removes the container upon stopping it.

![carbon (1)](/assets/2018-05-postgresql-docker-container-for-development/carbon-1.png)

Clearly these values can be customized, I'm opening the port 5433 because I have PostgreSQL installed on 5432, and I'm using a silly password.
