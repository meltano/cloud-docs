# Meltano Cloud Concepts

## Meltano Cloud Users

Your Meltano Cloud user account is associated with a GitHub account for single-signon. If you do not have a GitHub account, you can create a free account at [github.com](https://github.com).

> **Note**
> During the Private and Public Beta, we will be collecting feedback from users regarding the overall login experience. We also plan to offer SAML as a premium feature for Enterprise users. If would have a use case to support alternate forms of login besides GitHub auth and SAML (e.g. GitLab, or user/password auth), please let your account manager know or log an issue in our [issue tracker](https://github.com/meltano/cloud-docs/issues).

## Meltano Cloud Organizations

Your Meltano Cloud Organization is the top-level entity associated with your payment info. Each organization will be issued a unique billing account number.

> **Note**
> Each Meltano Cloud Organization can be mapped to zero or more GitHub organizations. See [Meltano Project Groups](#meltano-project-groups-and-github-orgs) below for more information.

## Meltano Project Groups and "GitHub Orgs"

Within each Meltano Cloud Organization, you can authorize Meltano Cloud to access your GitHub organizations. Internally, we refer to these as Meltano Cloud "project groups". Projects within a project group may share certain aspects, such as shared encryption/decryption keys and a shared set of role-based access permissions.

## Meltano Cloud Projects

A "Cloud Project" is any Meltano project you have registered on Meltano Cloud. The project definition consists of a git repo and a relative project directory within the git repo.

## Meltano Cloud Environments (aka "Deployments")

Within each Cloud Project, you can deploy zero or more named [Meltano Environments](https://docs.meltano.com/concepts/environments) to Meltano Cloud. Internally, we often refer to these as "deployments" since they are isolated environments deployed to the Cloud.

Each Cloud Environment Deployment must specify the environment name to deploy and the git branch to use when tracking project updates.

> **Note**
> All compute operations require a deployed environment - including: job execution, EL pipelines, scheduled workloads, etc.

## Meltano Cloud Schedules

Schedules within Meltano Cloud map directly to schedules defined in `meltano.yml`. However, in Meltano Cloud, each schedule starts off disabled by default, and should be enabled and disabled on a per-environment basis.

For example: The Acme Data Project has a schedule named `daily-transforms` and two environments named `prod` and `staging` respectively. Upon onboarding to Meltano Cloud, the Acme team can choose to enable `daily-transforms` on the `prod` environment only. Alternatively, the Acme team can choose to enable the schedule for both environments or neither environment. Whenever changing the status on a schedule, the action to enable or disable the schedule is in the context of one specific [Deployed Environment](#meltano-cloud-environments-aka-deployments) and one specified schedule name.
