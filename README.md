# fluent-bit-logrotate

Fluent-bit file output doesn't provide logrotate functionality so inside my Kubernetes deployment I had to create a [cronjob type](https://v1-20.docs.kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/) job that will scale down to zero the fluent-bit deployment, create a today folder, move the logs and scale up the fluent-bit deployment. The logrotate script is added to generic image using a configMap so not ideal.

In main branch I plan to have a custom container image that will include the script and xz to compress the logs
