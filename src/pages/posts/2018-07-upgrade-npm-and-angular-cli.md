---
layout: "../../layouts/BlogPost.astro"
title: "Upgrade NPM and Angular CLI"
description: "How to upgrage NPM and Angular CLI"
publishDate: "25 Jul 2018"
categories: 
  - "angular"
---

To upgrade NPM:

Run PowerShell as Administrator

`Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force`

`npm install -g npm-windows-upgrade`

`npm-windows-upgrade`

To upgrade Angular CLI:

`npm uninstall -g @angular/cli`

`npm cache verify`

`npm install -g @angular/cli@latest`
