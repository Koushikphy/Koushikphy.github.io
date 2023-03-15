---
title: "My thoughts on Heroku free alternatives"
tags: 
    - heroku
    - cloud
    - backend
category:
    - Cloud
date: 2023-02-26
toc: false
layout: single
classes: wide
excerpt: Heroku free alternatives pros and cons
---


As Heroku is going out, I’m searching for different free cloud backend solutions. Tried [fly.io](http://fly.io) although it's very limited and gives only one free tier app. But unlike Heroku the app never sleeps. So it can be used to run backend corn jobs. Another good one is [render.com](http://render.com). It's very similar to Heroku and sleeps after 15 minutes of inactivity. But its build time and startup time are quite slow. But the most promising one I got is definitely [railway.app](http://railway.app). It's fast, the UI feels more user-friendly and polished and gives logs about everything even the stdout/stderr of the deployed docker. What’s more, its lets you explore and query the backend PostgreSQL right inside the web UI. But presently has one major disadvantage on the free tier. It gives only 500hr monthly free usage and as the docker never sleeps, it’s not possible to even host a single app for a whole month. Although you can provide card details and use it for unlimited time without incurring any charges as the first $5 is free. If they introduce an auto sleep option on inactivity, Railway has the potential to be even better than Heroku itself 