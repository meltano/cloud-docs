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

### Internal Organization ID

Meltano Cloud uses an internal alpha-numeric string (randomly generated) to uniquely identify your cloud organization's identify. This ID may occassionally be shared during Cloud debugging and you may find references to it in the internal workings of Meltano Cloud CLI.

> **Warning**
> The "Internal Organization ID" should not be considered a permanent identifier, and may change at any time without notice.

## Meltano Cloud Projects

A "Cloud Project" is any Meltano project you have registered on Meltano Cloud. The project definition consists of a git repo and a relative project directory within the git repo.

### Internal Project ID

Meltano Cloud uses an internal alpha-numeric string (randomly generated) to uniquely identify your project's deployment. This ID may occassionally be shared during Cloud debugging and you may find references to it in the internal workings of Meltano Cloud CLI.

> **Warning**
> The "Internal Project ID" should not be confused with the Project ID that is defined within `meltano.yml`.

> **Note**
> The "Internal Project ID" should not be considered a permanent identifier, and may change at any time without notice.

## Meltano Cloud Deployments

Within each Cloud Project, you can deploy zero or more named [Meltano Environments](https://docs.meltano.com/concepts/environments) to Meltano Cloud. These are called Cloud Deployments.

Each Cloud Deployment must specify an environment name to deploy and a git branch to use when tracking project updates.

> **Note**
>
> All operations that perform compute require a deployed environment - including: ad-hoc job execution, EL pipelines, scheduled tasks, etc.

### Deployment Names

Each deployment has a "Deployment Name", which defaults to the "Environment Name" for the Meltano Environment that was deployed.

> **Note**
>
> At the current time, the Deployment Name will always be equivalent to the name of the environment that was deployed - and we do not yet support deploying the same environment twice as two different deployments. In future versions of Meltano, we plan to allow Environments to be deployed more than once (for example, for CI use cases), and for Deployment to be renamed.

## Meltano Cloud Runs

A "run" within Meltano is an instance of a Meltano operation that performed some compute. If you execute any of the following CLI commands, that is considered a Run:

* invoke
* elt
* run
* test

Each run has additional adjectives that give more information about what kind of run it is.

### On-demand, Unnamed Runs

An unnamed run is one that is specified directly on the command line. If a user executes `invoke` or `test`, that is always an on-demand unnamed run. If a user executes `meltano run` or `meltano elt` and specifies each plugin on the command line, that is an unnamed run.

### On-demand, Named Runs

A named run is defined in the meltano.yml file either under the `jobs` key in the case of `meltano run` or via the `schedules` key in the case of `meltano elt`.

On-demand, named run can be triggered via the following commands:

* `meltano schedule run <schedule_name>` (this works for `meltano elt` or `meltano run`)
* `meltano run <job_name>` (this works only for `meltano run`)

### Scheduled Runs

Scheduled runs are named jobs that have been set to execute on an interval and have been triggered automatically according to that schedule. These are defined under the `schedules` key in the meltano.yml file. [Documentation here.](https://docs.meltano.com/concepts/project#schedules)

All scheduled runs are named runs.

## Meltano Cloud Schedules

Schedules within Meltano Cloud map directly to schedules defined in `meltano.yml`. However, in Meltano Cloud, each schedule starts off disabled by default, and each schedule is enabled or disabled on a per-Deployment basis.
For example: The Acme Data Project has a schedule named `daily-transforms` and two environments named `prod` and `staging` respectively. Upon onboarding to Meltano Cloud, the Acme team can choose to enable `daily-transforms` on the `prod` environment only. Alternatively, the Acme team can choose to enable the schedule for both environments or neither environment. Whenever changing the status on a schedule, the action to enable or disable the schedule is in the context of one specific [Deployed Environment](#meltano-cloud-deployments) and one specified schedule name.
