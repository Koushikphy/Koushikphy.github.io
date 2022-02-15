---
title: "TeleJobReminder: A Telegram Job Reminder Bot"
tags: 
    - Telegram-bot
    - heroku
    - job-submission
date: 2022-02-13
toc: false
layout: single
classes: wide
category: TelegramBot
excerpt: "A Telegram bot that keeps track of your computer jobs."
# link: https://github.com/Koushikphy/TeleJobReminder

---

_A Telegram bot that keeps track of your computer jobs._


Telegram bots are an extremely handy tool to send automated notifications/messages directly to the phone. It's completely free, easy to set up, and you can send any kind of message, including documents, pictures, videos etc. Here, I have made a bot to keep track of my long-running computer jobs so that it can send me a notification when the job finishes/fails.


## Getting Started:
- Open the Telegram bot at [https://t.me/JobReminderBot](https://t.me/JobReminderBot) and press `start` to get started. Wait for the admin to authorize you.
- Download the `telebot` script (only written for bash atm), make it executable and keep it in your `PATH`.
- Submit your job with the shell script as
    ```
    telebot -u USER_ID -n JOB_Name -j JOB_Command
    ```


## Project Link
<a href='https://github.com/Koushikphy/TeleJobReminder'>https://github.com/Koushikphy/TeleJobReminder</a>