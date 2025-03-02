<!--- app-name: DeepSpeed -->

# DeepSpeed packaged by Bitnami

DeepSpeed is deep learning software suite for empowering ChatGPT-like model training. Features dense or sparse model inference, high throughput and high compression.

[Overview of DeepSpeed](https://www.deepspeed.ai/)

Trademarks: This software listing is packaged by Bitnami. The respective trademarks mentioned in the offering are owned by the respective companies, and use of them does not imply any affiliation or endorsement.

## TL;DR

```console
helm install my-release oci://registry-1.docker.io/bitnamicharts/deepspeed
```

## Introduction

This chart bootstraps a [DeepSpeed](https://github.com/bitnami/containers/tree/main/bitnami/deepspeed) deployment on a [Kubernetes](https://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

Python is built for full integration into Python that enables you to use it with its libraries and main packages.

Bitnami charts can be used with [Kubeapps](https://kubeapps.dev/) for deployment and management of Helm Charts in clusters.

Looking to use DeepSpeed in production? Try [VMware Application Catalog](https://bitnami.com/enterprise), the enterprise edition of Bitnami Application Catalog.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.2.0+
- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install my-release oci://registry-1.docker.io/bitnamicharts/deepspeed
```

These commands deploy DeepSpeed on the Kubernetes cluster in the default configuration. The [Parameters](#parameters) section lists the parameters that can be configured.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Parameters

### Global parameters

| Name                      | Description                                     | Value |
| ------------------------- | ----------------------------------------------- | ----- |
| `global.imageRegistry`    | Global Docker image registry                    | `""`  |
| `global.imagePullSecrets` | Global Docker registry secret names as an array | `[]`  |
| `global.storageClass`     | Global StorageClass for Persistent Volume(s)    | `""`  |

### Common parameters

| Name                     | Description                                                                             | Value           |
| ------------------------ | --------------------------------------------------------------------------------------- | --------------- |
| `kubeVersion`            | Override Kubernetes version                                                             | `""`            |
| `nameOverride`           | String to partially override common.names.fullname                                      | `""`            |
| `fullnameOverride`       | String to fully override common.names.fullname                                          | `""`            |
| `commonLabels`           | Labels to add to all deployed objects                                                   | `{}`            |
| `commonAnnotations`      | Annotations to add to all deployed objects                                              | `{}`            |
| `clusterDomain`          | Kubernetes cluster domain name                                                          | `cluster.local` |
| `extraDeploy`            | Array of extra objects to deploy with the release                                       | `[]`            |
| `diagnosticMode.enabled` | Enable diagnostic mode (all probes will be disabled and the command will be overridden) | `false`         |
| `diagnosticMode.command` | Command to override all containers in the deployments/statefulsets                      | `["sleep"]`     |
| `diagnosticMode.args`    | Args to override all containers in the deployments/statefulsets                         | `["infinity"]`  |

### Source code parameters

| Name                                | Description                                                                                               | Value                 |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------- | --------------------- |
| `image.registry`                    | Deepspeed image registry                                                                                  | `docker.io`           |
| `image.repository`                  | Deepspeed image repository                                                                                | `bitnami/deepspeed`   |
| `image.tag`                         | Deepspeed image tag (immutable tags are recommended)                                                      | `0.10.3-debian-11-r0` |
| `image.digest`                      | Deepspeed image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag | `""`                  |
| `image.pullPolicy`                  | Deepspeed image pull policy                                                                               | `IfNotPresent`        |
| `image.pullSecrets`                 | Specify docker-registry secret names as an array                                                          | `[]`                  |
| `source.type`                       | Where the source comes from: Possible values: configmap, git, custom                                      | `configmap`           |
| `source.launchCommand`              | deepspeed command to run over the project                                                                 | `""`                  |
| `source.configMap`                  | List of files of the project                                                                              | `{}`                  |
| `source.existingConfigMap`          | Name of a configmap containing the files of the project                                                   | `""`                  |
| `source.git.repository`             | Repository that holds the files                                                                           | `""`                  |
| `source.git.revision`               | Revision from the repository to checkout                                                                  | `""`                  |
| `source.git.extraVolumeMounts`      | Add extra volume mounts for the Git container                                                             | `[]`                  |
| `config.defaultHostFile`            | Host file generated by default (only edit if you know what you are doing)                                 | `""`                  |
| `config.overrideHostFile`           | Override default host file with the content in this value                                                 | `""`                  |
| `config.existingHostFileConfigMap`  | Name of a ConfigMap containing the hostfile                                                               | `""`                  |
| `config.defaultSSHClient`           | Default SSH client configuration for the client node (only edit if you know what you are doing)           | `""`                  |
| `config.overrideSSHClient`          | Override default SSH cliient configuration with the content in this value                                 | `""`                  |
| `config.existingSSHClientConfigMap` | Name of a ConfigMap containing the SSH client configuration                                               | `""`                  |
| `config.defaultSSHServer`           | Default SSH Server configuration for the worker nodes (only edit if you know what you are doing)          | `""`                  |
| `config.overrideSSHServer`          | Overidde SSH Server configuration with the content in this value                                          | `""`                  |
| `config.existingSSHServerConfigMap` | Name of a ConfigMap with with the SSH Server configuration                                                | `""`                  |
| `config.sshPrivateKey`              | Private key for the client node to connect to the worker nodes                                            | `""`                  |
| `config.existingSSHKeySecret`       | Name of a secret containing the ssh private key                                                           | `""`                  |

### Client Deployment Parameters

| Name                                                       | Description                                                                                      | Value            |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ---------------- |
| `client.enabled`                                           | Enable Client deployment                                                                         | `true`           |
| `client.useJob`                                            | Deploy as job                                                                                    | `false`          |
| `client.backoffLimit`                                      | set backoff limit of the job                                                                     | `10`             |
| `client.extraEnvVars`                                      | Array with extra environment variables to add to client nodes                                    | `[]`             |
| `client.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for client nodes                            | `""`             |
| `client.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for client nodes                               | `""`             |
| `client.annotations`                                       | Annotations for the client deployment                                                            | `{}`             |
| `client.command`                                           | Override default container command (useful when using custom images)                             | `[]`             |
| `client.args`                                              | Override default container args (useful when using custom images)                                | `[]`             |
| `client.terminationGracePeriodSeconds`                     | Client termination grace period (in seconds)                                                     | `""`             |
| `client.livenessProbe.enabled`                             | Enable livenessProbe on Client nodes                                                             | `true`           |
| `client.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                          | `5`              |
| `client.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                 | `30`             |
| `client.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                | `20`             |
| `client.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                              | `5`              |
| `client.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                              | `1`              |
| `client.readinessProbe.enabled`                            | Enable readinessProbe on Client nodes                                                            | `true`           |
| `client.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                         | `5`              |
| `client.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                | `30`             |
| `client.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                               | `20`             |
| `client.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                             | `5`              |
| `client.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                             | `1`              |
| `client.startupProbe.enabled`                              | Enable startupProbe on Client containers                                                         | `false`          |
| `client.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                           | `5`              |
| `client.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                  | `30`             |
| `client.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                 | `5`              |
| `client.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                               | `5`              |
| `client.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                               | `1`              |
| `client.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                              | `{}`             |
| `client.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                             | `{}`             |
| `client.customStartupProbe`                                | Custom startupProbe that overrides the default one                                               | `{}`             |
| `client.resources.limits`                                  | The resources limits for the client containers                                                   | `{}`             |
| `client.resources.requests`                                | The requested resources for the client containers                                                | `{}`             |
| `client.podSecurityContext.enabled`                        | Enabled Client pods' Security Context                                                            | `true`           |
| `client.podSecurityContext.fsGroup`                        | Set Client pod's Security Context fsGroup                                                        | `1001`           |
| `client.podSecurityContext.seccompProfile.type`            | Set Client container's Security Context seccomp profile                                          | `RuntimeDefault` |
| `client.containerSecurityContext.enabled`                  | Enabled Client containers' Security Context                                                      | `true`           |
| `client.containerSecurityContext.runAsUser`                | Set Client containers' Security Context runAsUser                                                | `1001`           |
| `client.containerSecurityContext.runAsGroup`               | Set Client containers' Security Context runAsGroup                                               | `1001`           |
| `client.containerSecurityContext.runAsNonRoot`             | Set Client containers' Security Context runAsNonRoot                                             | `true`           |
| `client.containerSecurityContext.readOnlyRootFilesystem`   | Set Client containers' Security Context runAsNonRoot                                             | `true`           |
| `client.containerSecurityContext.allowPrivilegeEscalation` | Set Client container's privilege escalation                                                      | `false`          |
| `client.containerSecurityContext.capabilities.drop`        | Set Client container's Security Context runAsNonRoot                                             | `["ALL"]`        |
| `client.lifecycleHooks`                                    | for the client container(s) to automate configuration before or after startup                    | `{}`             |
| `client.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                   | `""`             |
| `client.hostAliases`                                       | client pods host aliases                                                                         | `[]`             |
| `client.labels`                                            | Extra labels for the client deployment                                                           | `{}`             |
| `client.podLabels`                                         | Extra labels for client pods                                                                     | `{}`             |
| `client.podAnnotations`                                    | Annotations for client pods                                                                      | `{}`             |
| `client.podAffinityPreset`                                 | Pod affinity preset. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard`       | `""`             |
| `client.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard`  | `soft`           |
| `client.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard` | `""`             |
| `client.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `client.affinity` is set                                     | `""`             |
| `client.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `client.affinity` is set                                  | `[]`             |
| `client.affinity`                                          | Affinity for Client pods assignment                                                              | `{}`             |
| `client.nodeSelector`                                      | Node labels for Client pods assignment                                                           | `{}`             |
| `client.tolerations`                                       | Tolerations for Client pods assignment                                                           | `[]`             |
| `client.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains  | `[]`             |
| `client.priorityClassName`                                 | Client pods' priorityClassName                                                                   | `""`             |
| `client.schedulerName`                                     | Kubernetes pod scheduler registry                                                                | `""`             |
| `client.updateStrategy.type`                               | Client statefulset strategy type                                                                 | `RollingUpdate`  |
| `client.updateStrategy.rollingUpdate`                      | Client statefulset rolling update configuration parameters                                       | `{}`             |
| `client.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Client pod(s)                        | `[]`             |
| `client.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Client container(s)             | `[]`             |
| `client.sidecars`                                          | Add additional sidecar containers to the Client pod(s)                                           | `[]`             |
| `client.enableDefaultInitContainers`                       | Deploy default init containers                                                                   | `true`           |
| `client.initContainers`                                    | Add additional init containers to the Client pod(s)                                              | `[]`             |
| `client.networkPolicy.enabled`                             | Enable creation of NetworkPolicy resources                                                       | `false`          |
| `client.networkPolicy.extraIngress`                        | Add extra ingress rules to the NetworkPolicy                                                     | `[]`             |
| `client.networkPolicy.extraEgress`                         | Add extra ingress rules to the NetworkPolicy                                                     | `[]`             |
| `client.serviceAccount.create`                             | Enable creation of ServiceAccount for Client pods                                                | `false`          |
| `client.serviceAccount.name`                               | The name of the ServiceAccount to use                                                            | `""`             |
| `client.serviceAccount.automountServiceAccountToken`       | Allows auto mount of ServiceAccountToken on the serviceAccount created                           | `false`          |
| `client.serviceAccount.annotations`                        | Additional custom annotations for the ServiceAccount                                             | `{}`             |

### Deepspeed Client persistence paramaters

| Name                               | Description                                                             | Value                     |
| ---------------------------------- | ----------------------------------------------------------------------- | ------------------------- |
| `client.persistence.enabled`       | Use a PVC to persist data                                               | `false`                   |
| `client.persistence.storageClass`  | discourse & sidekiq data Persistent Volume Storage Class                | `""`                      |
| `client.persistence.existingClaim` | Use a existing PVC which must be created manually before bound          | `""`                      |
| `client.persistence.mountPath`     | Path to mount the volume at                                             | `/bitnami/deepspeed/data` |
| `client.persistence.accessModes`   | Persistent Volume Access Mode                                           | `["ReadWriteOnce"]`       |
| `client.persistence.dataSource`    | Custom PVC data source                                                  | `{}`                      |
| `client.persistence.selector`      | Selector to match an existing Persistent Volume for the client data PVC | `{}`                      |
| `client.persistence.size`          | Size of data volume                                                     | `8Gi`                     |
| `client.persistence.labels`        | Persistent Volume labels                                                | `{}`                      |
| `client.persistence.annotations`   | Persistent Volume annotations                                           | `{}`                      |

### Worker Deployment Parameters

| Name                                                       | Description                                                                                        | Value            |
| ---------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ---------------- |
| `worker.enabled`                                           | Enable Worker deployment                                                                           | `true`           |
| `worker.slotsPerNode`                                      | Number of slots available per worker node                                                          | `1`              |
| `worker.extraEnvVars`                                      | Array with extra environment variables to add to client nodes                                      | `[]`             |
| `worker.extraEnvVarsCM`                                    | Name of existing ConfigMap containing extra env vars for client nodes                              | `""`             |
| `worker.extraEnvVarsSecret`                                | Name of existing Secret containing extra env vars for client nodes                                 | `""`             |
| `worker.command`                                           | Override default container command (useful when using custom images)                               | `[]`             |
| `worker.args`                                              | Override default container args (useful when using custom images)                                  | `[]`             |
| `worker.replicaCount`                                      | Number of Worker replicas to deploy                                                                | `3`              |
| `worker.terminationGracePeriodSeconds`                     | Worker termination grace period (in seconds)                                                       | `""`             |
| `worker.containerPorts.ssh`                                | SSH port for Worker                                                                                | `2222`           |
| `worker.livenessProbe.enabled`                             | Enable livenessProbe on Worker nodes                                                               | `true`           |
| `worker.livenessProbe.initialDelaySeconds`                 | Initial delay seconds for livenessProbe                                                            | `5`              |
| `worker.livenessProbe.periodSeconds`                       | Period seconds for livenessProbe                                                                   | `30`             |
| `worker.livenessProbe.timeoutSeconds`                      | Timeout seconds for livenessProbe                                                                  | `5`              |
| `worker.livenessProbe.failureThreshold`                    | Failure threshold for livenessProbe                                                                | `5`              |
| `worker.livenessProbe.successThreshold`                    | Success threshold for livenessProbe                                                                | `1`              |
| `worker.readinessProbe.enabled`                            | Enable readinessProbe on Worker nodes                                                              | `true`           |
| `worker.readinessProbe.initialDelaySeconds`                | Initial delay seconds for readinessProbe                                                           | `5`              |
| `worker.readinessProbe.periodSeconds`                      | Period seconds for readinessProbe                                                                  | `30`             |
| `worker.readinessProbe.timeoutSeconds`                     | Timeout seconds for readinessProbe                                                                 | `5`              |
| `worker.readinessProbe.failureThreshold`                   | Failure threshold for readinessProbe                                                               | `5`              |
| `worker.readinessProbe.successThreshold`                   | Success threshold for readinessProbe                                                               | `1`              |
| `worker.startupProbe.enabled`                              | Enable startupProbe on Worker containers                                                           | `false`          |
| `worker.startupProbe.initialDelaySeconds`                  | Initial delay seconds for startupProbe                                                             | `5`              |
| `worker.startupProbe.periodSeconds`                        | Period seconds for startupProbe                                                                    | `30`             |
| `worker.startupProbe.timeoutSeconds`                       | Timeout seconds for startupProbe                                                                   | `5`              |
| `worker.startupProbe.failureThreshold`                     | Failure threshold for startupProbe                                                                 | `5`              |
| `worker.startupProbe.successThreshold`                     | Success threshold for startupProbe                                                                 | `1`              |
| `worker.customLivenessProbe`                               | Custom livenessProbe that overrides the default one                                                | `{}`             |
| `worker.customReadinessProbe`                              | Custom readinessProbe that overrides the default one                                               | `{}`             |
| `worker.customStartupProbe`                                | Custom startupProbe that overrides the default one                                                 | `{}`             |
| `worker.resources.limits`                                  | The resources limits for the client containers                                                     | `{}`             |
| `worker.resources.requests`                                | The requested resources for the client containers                                                  | `{}`             |
| `worker.podSecurityContext.enabled`                        | Enabled Worker pods' Security Context                                                              | `true`           |
| `worker.podSecurityContext.fsGroup`                        | Set Worker pod's Security Context fsGroup                                                          | `1001`           |
| `worker.podSecurityContext.seccompProfile.type`            | Set Worker container's Security Context seccomp profile                                            | `RuntimeDefault` |
| `worker.containerSecurityContext.enabled`                  | Enabled Worker containers' Security Context                                                        | `true`           |
| `worker.containerSecurityContext.runAsUser`                | Set Worker containers' Security Context runAsUser                                                  | `1001`           |
| `worker.containerSecurityContext.runAsGroup`               | Set Worker containers' Security Context runAsGroup                                                 | `1001`           |
| `worker.containerSecurityContext.runAsNonRoot`             | Set Worker containers' Security Context runAsNonRoot                                               | `true`           |
| `worker.containerSecurityContext.readOnlyRootFilesystem`   | Set Worker containers' Security Context runAsNonRoot                                               | `true`           |
| `worker.containerSecurityContext.allowPrivilegeEscalation` | Set Worker container's privilege escalation                                                        | `false`          |
| `worker.containerSecurityContext.capabilities.drop`        | Set Worker container's Security Context runAsNonRoot                                               | `["ALL"]`        |
| `worker.lifecycleHooks`                                    | for the client container(s) to automate configuration before or after startup                      | `{}`             |
| `worker.runtimeClassName`                                  | Name of the runtime class to be used by pod(s)                                                     | `""`             |
| `worker.hostAliases`                                       | client pods host aliases                                                                           | `[]`             |
| `worker.labels`                                            | Labels for the worker deployment                                                                   | `{}`             |
| `worker.annotations`                                       | Annotations for the worker deployment                                                              | `{}`             |
| `worker.podLabels`                                         | Extra labels for client pods                                                                       | `{}`             |
| `worker.podAnnotations`                                    | Annotations for client pods                                                                        | `{}`             |
| `worker.podAffinityPreset`                                 | Pod affinity preset. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard`         | `""`             |
| `worker.podAntiAffinityPreset`                             | Pod anti-affinity preset. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard`    | `soft`           |
| `worker.nodeAffinityPreset.type`                           | Node affinity preset type. Ignored if `client.affinity` is set. Allowed values: `soft` or `hard`   | `""`             |
| `worker.nodeAffinityPreset.key`                            | Node label key to match. Ignored if `client.affinity` is set                                       | `""`             |
| `worker.nodeAffinityPreset.values`                         | Node label values to match. Ignored if `client.affinity` is set                                    | `[]`             |
| `worker.affinity`                                          | Affinity for Worker pods assignment                                                                | `{}`             |
| `worker.nodeSelector`                                      | Node labels for Worker pods assignment                                                             | `{}`             |
| `worker.tolerations`                                       | Tolerations for Worker pods assignment                                                             | `[]`             |
| `worker.topologySpreadConstraints`                         | Topology Spread Constraints for pod assignment spread across your cluster among failure-domains    | `[]`             |
| `worker.podManagementPolicy`                               | Statefulset Pod management policy, it needs to be Parallel to be able to complete the cluster join | `Parallel`       |
| `worker.priorityClassName`                                 | Worker pods' priorityClassName                                                                     | `""`             |
| `worker.schedulerName`                                     | Kubernetes pod scheduler registry                                                                  | `""`             |
| `worker.updateStrategy.type`                               | Worker statefulset strategy type                                                                   | `RollingUpdate`  |
| `worker.updateStrategy.rollingUpdate`                      | Worker statefulset rolling update configuration parameters                                         | `{}`             |
| `worker.extraVolumes`                                      | Optionally specify extra list of additional volumes for the Worker pod(s)                          | `[]`             |
| `worker.extraVolumeMounts`                                 | Optionally specify extra list of additional volumeMounts for the Worker container(s)               | `[]`             |
| `worker.sidecars`                                          | Add additional sidecar containers to the Worker pod(s)                                             | `[]`             |
| `worker.enableDefaultInitContainers`                       | Deploy default init containers                                                                     | `true`           |
| `worker.initContainers`                                    | Add additional init containers to the Worker pod(s)                                                | `[]`             |
| `worker.headlessServiceAnnotations`                        | Annotations for the headless service                                                               | `{}`             |

### Worker Traffic Exposure Parameters

| Name                                                     | Description                                                                                                                               | Value       |
| -------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| `worker.externalAccess.enabled`                          | Create a service per worker node                                                                                                          | `false`     |
| `worker.externalAccess.service.type`                     | Worker service type                                                                                                                       | `ClusterIP` |
| `worker.externalAccess.service.loadBalancerIPs`          | Array of load balancer IPs for each Kafka broker. Length must be the same as replicaCount                                                 | `[]`        |
| `worker.externalAccess.service.externalIPs`              | Use distinct service host IPs to configure Kafka external listener when service type is NodePort. Length must be the same as replicaCount | `[]`        |
| `worker.externalAccess.service.loadBalancerAnnotations`  | Array of load balancer annotations for each Kafka broker. Length must be the same as replicaCount                                         | `[]`        |
| `worker.externalAccess.service.publishNotReadyAddresses` | Indicates that any agent which deals with endpoints for this Service should disregard any indications of ready/not-ready                  | `false`     |
| `worker.externalAccess.service.ports.ssh`                | Worker GRPC service port                                                                                                                  | `22`        |
| `worker.externalAccess.service.nodePorts`                | Array of node ports used for each Kafka broker. Length must be the same as replicaCount                                                   | `[]`        |
| `worker.externalAccess.service.sessionAffinityConfig`    | Additional settings for the sessionAffinity                                                                                               | `{}`        |
| `worker.externalAccess.service.sessionAffinity`          | Control where client requests go, to the same pod or round-robin                                                                          | `None`      |
| `worker.externalAccess.service.loadBalancerSourceRanges` | Worker service Load Balancer sources                                                                                                      | `[]`        |
| `worker.externalAccess.service.externalTrafficPolicy`    | Worker service external traffic policy                                                                                                    | `Cluster`   |
| `worker.externalAccess.service.labels`                   | Additional custom labels for Worker service                                                                                               | `{}`        |
| `worker.externalAccess.service.annotations`              | Additional custom annotations for Worker service                                                                                          | `{}`        |
| `worker.externalAccess.service.extraPorts`               | Extra ports to expose in the Worker service                                                                                               | `[]`        |
| `worker.serviceAccount.create`                           | Enable creation of ServiceAccount for Data Coordinator pods                                                                               | `false`     |
| `worker.serviceAccount.name`                             | The name of the ServiceAccount to use                                                                                                     | `""`        |
| `worker.serviceAccount.automountServiceAccountToken`     | Allows auto mount of ServiceAccountToken on the serviceAccount created                                                                    | `false`     |
| `worker.serviceAccount.annotations`                      | Additional custom annotations for the ServiceAccount                                                                                      | `{}`        |
| `worker.networkPolicy.enabled`                           | Enable creation of NetworkPolicy resources                                                                                                | `false`     |
| `worker.networkPolicy.allowExternal`                     | The Policy model to apply                                                                                                                 | `true`      |
| `worker.networkPolicy.extraIngress`                      | Add extra ingress rules to the NetworkPolicy                                                                                              | `[]`        |
| `worker.networkPolicy.extraEgress`                       | Add extra ingress rules to the NetworkPolicy                                                                                              | `[]`        |
| `worker.networkPolicy.ingressNSMatchLabels`              | Labels to match to allow traffic from other namespaces                                                                                    | `{}`        |
| `worker.networkPolicy.ingressNSPodMatchLabels`           | Pod labels to match to allow traffic from other namespaces                                                                                | `{}`        |

### Deepspeed Worker persistence paramaters

| Name                                   | Description                                                                                                                       | Value                     |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| `worker.persistence.enabled`           | Use a PVC to persist data                                                                                                         | `false`                   |
| `worker.persistence.storageClass`      | discourse & sidekiq data Persistent Volume Storage Class                                                                          | `""`                      |
| `worker.persistence.existingClaim`     | Use a existing PVC which must be created manually before bound                                                                    | `""`                      |
| `worker.persistence.mountPath`         | Path to mount the volume at                                                                                                       | `/bitnami/deepspeed/data` |
| `worker.persistence.accessModes`       | Persistent Volume Access Mode                                                                                                     | `["ReadWriteOnce"]`       |
| `worker.persistence.selector`          | Selector to match an existing Persistent Volume for the worker data PVC                                                           | `{}`                      |
| `worker.persistence.dataSource`        | Custom PVC data source                                                                                                            | `{}`                      |
| `worker.persistence.size`              | Size of data volume                                                                                                               | `8Gi`                     |
| `worker.persistence.labels`            | Persistent Volume labels                                                                                                          | `{}`                      |
| `worker.persistence.annotations`       | Persistent Volume annotations                                                                                                     | `{}`                      |
| `gitImage.registry`                    | Git image registry                                                                                                                | `docker.io`               |
| `gitImage.repository`                  | Git image repository                                                                                                              | `bitnami/git`             |
| `gitImage.tag`                         | Git image tag (immutable tags are recommended)                                                                                    | `2.42.0-debian-11-r20`    |
| `gitImage.digest`                      | Git image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag                               | `""`                      |
| `gitImage.pullPolicy`                  | Git image pull policy                                                                                                             | `IfNotPresent`            |
| `gitImage.pullSecrets`                 | Specify docker-registry secret names as an array                                                                                  | `[]`                      |
| `volumePermissions.enabled`            | Enable init container that changes volume permissions in the data directory                                                       | `false`                   |
| `volumePermissions.image.registry`     | Init container volume-permissions image registry                                                                                  | `docker.io`               |
| `volumePermissions.image.repository`   | Init container volume-permissions image repository                                                                                | `bitnami/os-shell`        |
| `volumePermissions.image.tag`          | Init container volume-permissions image tag (immutable tags are recommended)                                                      | `11-debian-11-r63`        |
| `volumePermissions.image.digest`       | Init container volume-permissions image digest in the way sha256:aa.... Please note this parameter, if set, will override the tag | `""`                      |
| `volumePermissions.image.pullPolicy`   | Init container volume-permissions image pull policy                                                                               | `IfNotPresent`            |
| `volumePermissions.image.pullSecrets`  | Specify docker-registry secret names as an array                                                                                  | `[]`                      |
| `volumePermissions.resources.limits`   | The resources limits for the container                                                                                            | `{}`                      |
| `volumePermissions.resources.requests` | The requested resources for the container                                                                                         | `{}`                      |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install my-release \
  --set worker.replicaCount=4 \
    oci://registry-1.docker.io/bitnamicharts/deepspeed
```

The above command create 4 pods for DeepSpeed workers.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml oci://registry-1.docker.io/bitnamicharts/deepspeed
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Configuration and installation details

### [Rolling VS Immutable tags](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/)

It is strongly recommended to use immutable tags in a production environment. This ensures your deployment does not change automatically if the same tag is updated with a different image.

Bitnami will release a new chart updating its containers if a new version of the main container, significant changes, or critical vulnerabilities exist.

### Deploy as Job

By default, the chart will deploy the client container (the one that connects to the Deepspeed workers) as a Deployment. This allows you to enter the container via `kubectl exec` and perform operations. In case you want to deploy it as a Kubernetes job, set the `client.useJob=true` value.

### Loading your files

The DeepSpeed chart supports three different ways to load your files. In order of priority, they are:

1. Existing config map
2. Add files in the values.yaml
3. Cloning a git repository

This means that if you specify a config map with your files, it won't check the files defined in `values.yaml` directory nor the git repository.

In order to use an existing config map, set the `source.existingConfigMap=my-config-map` parameter.

To add your files in the values.yaml file, set the `source.configmap` object with the files.

Finally, if you want to clone a git repository you can use those parameters:

```console
source.type=git
source.git.repository=https://github.com/my-user/oci://registry-1.docker.io/bitnamicharts
source.git.revision=master
```

## Persistence

The [Bitnami DeepSpeed](https://github.com/bitnami/containers/tree/main/bitnami/deepspeed) image can persist data. If enabled, the persisted path is `/bitnami/deepspeed/data` by default.

The chart mounts a [Persistent Volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) at this location. The volume is created using dynamic volume provisioning.

### Adjust permissions of persistent volume mountpoint

As the image run as non-root by default, it is necessary to adjust the ownership of the persistent volume so that the container can write data into it.

By default, the chart is configured to use Kubernetes Security Context to automatically change the ownership of the volume. However, this feature does not work in all Kubernetes distributions.
As an alternative, this chart supports using an initContainer to change the ownership of the volume before mounting it in the final destination.

You can enable this initContainer by setting `volumePermissions.enabled` to `true`.

### Setting Pod's affinity

This chart allows you to set your custom affinity using the `affinity` parameter. Find more information about Pod's affinity in the [kubernetes documentation](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity).

As an alternative, you can use of the preset configurations for pod affinity, pod anti-affinity, and node affinity available at the [bitnami/common](https://github.com/bitnami/charts/tree/main/bitnami/common#affinities) chart. To do so, set the `podAffinityPreset`, `podAntiAffinityPreset`, or `nodeAffinityPreset` parameters.

### Additional environment variables

In case you want to add extra environment variables (useful for advanced operations like custom init scripts), you can use the `extraEnvVars` property inside each of the subsections: `client`, `worker`.

```yaml
client:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error

worker:
  extraEnvVars:
    - name: LOG_LEVEL
      value: error
```

Alternatively, you can use a ConfigMap or a Secret with the environment variables. To do so, use the `extraEnvVarsCM` or the `extraEnvVarsSecret` values.

### Sidecars

If additional containers are needed in the same pod as milvus (such as additional metrics or logging exporters), they can be defined using the `sidecars` parameter inside each of the subsections: `client`, `worker`. If these sidecars export extra ports, extra port definitions can be added using the `service.extraPorts` parameter. [Learn more about configuring and using sidecar containers](https://docs.bitnami.com/kubernetes/infrastructure/deepspeed/configuration/configure-sidecar-init-containers/).

## Troubleshooting

Find more information about how to deal with common errors related to Bitnami's Helm charts in [this troubleshooting guide](https://docs.bitnami.com/general/how-to/troubleshoot-helm-chart-issues).

## License

Copyright &copy; 2023 VMware, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.