# Ragtag Infrastructure Guide

This is a guide to hosted Ragtag infrastructure, as well as recommendations for projects hosted outside of Ragtag accounts.

Currently, Ragtag has an AWS account and a [Dokku](http://dokku.viewdocs.io/dokku/) instance.

## Ragtag infrastructure goals

- Make deployment easy for developers of all skill levels.
- Cheap hosting during development
- No need for volunteers to pay for hosting
- Price effective production hosting for orgs that need it
- Smooth transition to org-hosted environments

## Recommendations

### Source control

We run a [Ragtag GitHub](https://github.com/ragtagteam) organization. Some projects use their own GitLab accounts.

### Deployment options

#### Early development / proof of concept

Ragtag-hosted Dokku (see [Dokku Development Guide](guides/Dokku.md)) for web apps. [This is brand new–please try it out if you're interested!]

Some people choose to use their own Heroku accounts.

#### Static sites

For fully static sites that don't require customer editing, we recommend either [Netlify](https://www.netlify.com)'s free plan or [GitHub Pages](https://pages.github.com/).

It's easier to configure HTTPS and a custom domain with Netlify, since you can use a CNAME record. We've used GitHub Pages with Cloudflare for HTTPS, but Cloudfare needs to control your DNS records, not just have an alias. Netlify also has the option to password protect sites.

Note: Netlify can only work with an apex domains (no subdomain) with certain DNS providers.

#### Periodic jobs

For scheduled jobs that take less than 5 minutes to execute, we recommend [AWS Lambda](https://aws.amazon.com/lambda/) using [Serverless](https://serverless.com/).

#### Other

The needs of a project are ultimately the most important factor for choosing infrastructure.

Feel free to do something different if it's a better fit for your work. We just ask that you be clear in your reasoning for choosing a different setup.

### Staging

> Everybody has a testing environment. Some people are lucky enough enough to have a totally separate environment to run production in. – [@stahnma](https://twitter.com/stahnma/status/634849376343429120)

If your app or service has any real users, or affects real data in external systems, or requires review from stakeholders, you should have a staging/test environment.

In general, it makes sense for your staging environment to be as close to production as possible.

### Production

The production environment is dependent on both the technical requirements of the project (including expected load, latency demands, etc.) as well as the technical skill, available time, and infrastructure of the organization we are working with.

Ragtag is open to the following models:

#### Ragtag-hosted

We continue to run the project on our own infrastructure, and make our own call about architecture, deployment model, etc. This assumes either low cost (in terms of both dollars and developer time/complexity), a paid contract with the organization, or a pro bono arrangement.

#### Organization-hosted, Ragtag-operated

We work with the organization's existing technical staff to determine what will work on their systems (or what new systems they should set up).

Ragtag volunteers get and maintain access to the external organization's hosting infrastructure.

#### Organization-owned

After working with the organization's technical staff to agree on the form of the project (Ruby on Rails, node, Dockerized, Heroku-compatible, simple AWS setup, CloudFormation stack, Terraform project, etc.) Ragtag delivers code that the organization hosts and operates. We may provide code updates, but we don't do any deployment or DevOps work.