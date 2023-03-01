# Meltano Cloud Concepts

## Meltano Cloud Users

Your Meltano Cloud user account is associated with a GitHub account for single-sign-on. If you do not have a GitHub account, you can create a free account at [github.com](https://github.com).

> **Note**
>
> During the Private and Public Beta phases, we will be collecting feedback from users regarding the login and account creation experience overall. Post-GA, we plan to offer SAML on Cloud. If you have a use case to support alternate forms of login besides GitHub auth and SAML (e.g. GitLab, or user/password auth), please let your account manager know or log an issue in our [issue tracker](https://github.com/meltano/cloud-docs/issues).

## Meltano Cloud Organizations

Your Meltano Cloud Organization is the top-level entity associated with your payment info. Each organization will be issued a unique billing account number.

> **Note**
>
> Meltano Cloud Organizations should not be confused with GitHub Organizations (or "GitHub Orgs"). Each Meltano Cloud Organization can include projects from multiple GitHub Orgs.
>
> Meltano Cloud users grant access to specific public and private repositories using the standard GitHub App authorization flow.

## Meltano Cloud Projects

A "Cloud Project" is any Meltano project you have registered on Meltano Cloud. The project definition consists of a git repo and a relative project directory within the git repo.

## Meltano Cloud Deployments

Within each Cloud Project, you can deploy zero or more named [Meltano Environments](https://docs.meltano.com/concepts/environments) to Meltano Cloud. These are called Cloud Deployments.

Each Cloud Deployment must specify an environment name to deploy and a git branch to use when tracking project updates.

> **Note**
>
> All operations that perform compute require a deployed environment - including: ad-hoc job execution, EL pipelines, scheduled tasks, etc.

## Meltano Cloud Schedules

Schedules within Meltano Cloud map directly to schedules defined in `meltano.yml`. However, in Meltano Cloud, each schedule starts off disabled by default, and each schedule is enabled or disabled on a per-Deployment basis.
For example: The Acme Data Project has a schedule named `daily-transforms` and two environments named `prod` and `staging` respectively. Upon onboarding to Meltano Cloud, the Acme team can choose to enable `daily-transforms` on the `prod` environment only. Alternatively, the Acme team can choose to enable the schedule for both environments or neither environment. Whenever changing the status on a schedule, the action to enable or disable the schedule is in the context of one specific [Deployed Environment](#meltano-cloud-deployments) and one specified schedule name.
