---
layout: layout.pug
title: Uninstall
menuWeight: 20
excerpt:
featureMaturity: preview
enterprise: false
navigationTitle:  Uninstall
---

<!-- This source repo for this topic is https://github.com/mesosphere/dcos-commons -->


<!-- THIS CONTENT DUPLICATES THE DC/OS OPERATION GUIDE -->

### DC/OS 1.10

If you are using DC/OS 1.10 and the installed service has a version greater than 2.0.0-x:

1. Uninstall the service. From the DC/OS CLI, enter `dcos package uninstall --app-id=<instancename> beta-elastic`.

For example, to uninstall an Elastic instance named `elastic-dev`, run:

```bash
dcos package uninstall --app-id=elastic-dev beta-elastic
```

### Older versions

If you are running DC/OS 1.9 or older, or a version of the service that is older than 2.0.0-x, follow these steps:

1. Stop the service. From the DC/OS CLI, enter `dcos package uninstall --app-id=<instancename> <packagename>`.
   For example, `dcos package uninstall --app-id=elastic-dev beta-elastic`.
1. Clean up remaining reserved resources with the framework cleaner script, `janitor.py`. See [DC/OS documentation](/docs/1.10/deploying-services/uninstall/#framework-cleaner) for more information about the framework cleaner script.

For example, to uninstall an Elastic instance named `elastic-dev`, run:

```bash
$ MY_SERVICE_NAME=elastic-dev
$ dcos package uninstall --app-id=$MY_SERVICE_NAME beta-elastic`.
$ dcos node ssh --master-proxy --leader "docker run mesosphere/janitor /janitor.py \
    -r $MY_SERVICE_NAME-role \
    -p $MY_SERVICE_NAME-principal \
    -z dcos-service-$MY_SERVICE_NAME"
```

<!-- END DUPLICATE BLOCK -->