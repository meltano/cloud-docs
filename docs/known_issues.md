# Meltano Cloud - Known Issues

## Limitations during Alpha

### Limited secrets management features

Within the Alpha phase, there will only be limited support for secrets management. Future Meltano Core and Meltano Cloud features will enable additional secrets management options.

### Manually-submitted schedules lists

During the Alpha, Meltano Cloud will only run schedules which you have explicitly declared and requested.

In future, Meltano Cloud will automatically run any schedules you have configured to run within the named environment.

See related issue: [#6853](https://github.com/meltano/meltano/issues/6853).

## Other Unsupported Features in Meltano Cloud

The following features are not currently scoped for inclusion for the Meltano Cloud GA.

1. Hosted Airflow as orchestrator
   - At launch, Meltano will not support hosted Airflow orchestration. Instead, Meltano Cloud provides its own built-in managed scheduler and orchestrator.
   - Workaround:
     - We are evaluating options for users to invoke workloads from external services and from the command line. These could provide a method of remote execution from a self-managed Airflow server, for instance.
1. Hosting of BYO web services and other stateful service backends
   - At launch, Meltano will not allow incoming traffic to any running container. This is for security reasons.
   - Workarounds:
     - We may in the future offer BYO-services when defined as Meltano plugins. Due to the additional security provisions required, this additional functionality may only be available for premium service tiers.

Based upon user feedback, we will continue to reevaluate the list of supported and non-supported features for Meltano Cloud. If you have an urgenct need for any of the above features, please let us know!
