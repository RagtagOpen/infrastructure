# Dokku Development Guide

[Dokku](http://dokku.viewdocs.io/dokku/) is an open source project that provides a Docker-based Heroku-like environment.

It is ideal for low traffic applications. This is not an environment for high traffic or high availability apps, and should not be used for production deployment.

We run an instance at dev.ragtag.tech.

## Get access to Dokku

Dokku doesn't use usernames or passwords, just ssh keys. To get access, send a Slack DM to `jkriss` with either your ssh public key or your GitHub username.

If you don't yet have an ssh key, the [GitHub guide](https://help.github.com/articles/connecting-to-github-with-ssh/) is handy.

## Request an app

To get a new app set up, DM jkriss on Slack with the name you'd like for your app, and whatever other services you'll need (Postgres, MySQL, MongoDB, Memcached, Redis, etc.).

## Configure your git repo

    git remote add dokku dokku@dev.ragtag.tech:your-app-name

## Push your code to deploy

    git push dokku master

Now your app should be available at https://your-app-name.ragtag.tech

---

## Current Dokku plugins

We currently have the following plugins installed, and can add others upon request:

- [Postgres](https://github.com/dokku/dokku-postgres)
- [Let's Encrypt](https://github.com/dokku/dokku-letsencrypt)
- [Memcached](https://github.com/dokku/dokku-memcached)
- [MongoDB](https://github.com/dokku/dokku-mongo)
- [MySQL](https://github.com/dokku/dokku-mysql)
- [Redis](https://github.com/dokku/dokku-redis)
- [HTTP Auth](https://github.com/dokku/dokku-http-auth)