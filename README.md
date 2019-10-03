# rrfortune

[![Build Status](https://travis-ci.org/xhh09a/rrfortune.svg?branch=master)](https://travis-ci.org/xhh09a/rrfortune)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

## Why

Believe it or not, my wife is still obsessed with the login streak on [RenRen](http://renren.com/).
She will be unhappy if I forget to login and collect RenRen fortune.
Most of the time, let alone when you travel, it's hard to remember.
So I have to improvise.

## Solution

- Consider logging in and clicking the button a UI test
- Have Travis CI run a daily build to trigger that test

## Prerequisites

Assuming you have access the following services

- A RenRen account
- A GitHub account
- A Rollbar account (lazy error tracking)
- A Travis CI account (daily cron job)

## Setup

### Rollbar

1. Create a new project
2. Markdown the access token (rollbar key)

### GitHub

1. Fork this repo

### Travis CI

1. Enable build on Travis CI
2. Set the environment variables on Travis CI
   - Rollbar: rollbar_key
   - RenRen: email / password
3. Set a daily cron job

All set!

## Develop

Setup chromedriver

    curl -O https://chromedriver.storage.googleapis.com/2.46/chromedriver_mac64.zip
    unzip -o chromedriver_mac64.zip
    mv -f chromedriver /usr/local/bin/chromedriver

Export credentials

    export email="..."
    export password="..."
    export rollbar="..."

Run test

    cd rrfortune
    python -m venv venv
    source venv/bin/activate
    pip install -U pip
    pip install -r requirements-dev.txt
    pytest
