---
title: "System Status Checker"
tags: 
    - django
    - system
category:
    - Django-Apps
date: 2022-02-13
toc: false
layout: single
classes: wide
excerpt: "A dashboard like webserver to check system status of multiple PC/Workstation/Cluster in a single place."
# link: https://github.com/Koushikphy/System-Status-Checker

---

_A dashboard like webserver built with django to check system status of multiple PC/Workstation/Cluster in a single place._


## Get Started:
1. Install Django-3 and clone [this repo](https://github.com/Koushikphy/System-Status-Checker).
2. Make database migrations and create a superuser.
3. From the admin panel (`/admin/`) add your server, ip address, commands to run etc.
4. A list of predefined commands is already given in the `models.py` and they can be set using server type option.
5. Now go to home (`/home/`) to check the status of the added systems. Use refresh to get latest status.




## Project Link
<a href='https://github.com/Koushikphy/System-Status-Checker'>https://github.com/Koushikphy/System-Status-Checker</a>