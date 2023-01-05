# API Reference

API usage and examples for features of Meltano Cloud.

The API functionalities documented here may be adjusted post-alpha phase.

## On-demand Job Runners

On-demand job runners allow users to rerun or run at any point a scheduled job.

During the onboarding process, you will receive the following information that you will need to invoke your scheduled jobs on-demand:
- An API key 
- A Meltano Runner Secret
- Your Organization's Tenant Resource Key (Tenant ID)
- Your Project's ID (if you have multiple projects, you will receive one for each)

Information that you provide to us during [onboarding](https://github.com/meltano/cloud-docs/blob/main/docs/onboarding.md#step-1-submit-project-onboarding-information):
- The name of the [Meltano Environment](https://docs.meltano.com/concepts/environments)
- The schedule name

You will need to pass them in as headers (`x-api-key` and `meltano-runner-secret`) when invoking the API as part of the authentication process.

### CURL Example

First set `API_KEY` and `MELTANO_RUNNER_SECRET` environment variables locally.

```
curl -X POST "https://cloud-runners.meltano.com/v1/<tenant_resource_key>/<project_id>/<meltano_environment_name>/<schedule_name>" -H "x-api-key": ${API_KEY}" -H "meltano-runner-secret: ${MELTANO_RUNNER_SECRET}"
```
