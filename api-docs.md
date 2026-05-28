# API Reference

## Packages
- [api.localstack.cloud/v1alpha1](#apilocalstackcloudv1alpha1)


## api.localstack.cloud/v1alpha1

Package v1alpha1 contains API Schema definitions for the api v1alpha1 API group

### Resource Types
- [LocalStack](#localstack)
- [LocalStackList](#localstacklist)



#### CaCertificate



CaCertificate provides options for providing a custom CA certificate for outbound requests



_Appears in:_
- [LicenseServerConfig](#licenseserverconfig)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `configMap` _[CaCertificateConfigMap](#cacertificateconfigmap)_ |  |  | Optional: \{\} <br /> |


#### CaCertificateConfigMap







_Appears in:_
- [CaCertificate](#cacertificate)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `name` _string_ |  |  | Optional: \{\} <br /> |
| `namespace` _string_ |  |  | Optional: \{\} <br /> |
| `key` _string_ |  |  | Optional: \{\} <br /> |


#### Hooks







_Appears in:_
- [LocalStackSpec](#localstackspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `readyConfigName` _string_ |  |  | Optional: \{\} <br /> |
| `bootConfigName` _string_ |  |  | Optional: \{\} <br /> |
| `shutdownConfigName` _string_ |  |  | Optional: \{\} <br /> |
| `startConfigName` _string_ |  |  | Optional: \{\} <br /> |


#### LicenseServerConfig







_Appears in:_
- [LocalStackSpec](#localstackspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `proxies` _object (keys:string, values:string)_ |  | \{  \} | Optional: \{\} <br /> |
| `endpoint` _string_ |  | https://api.localstack.cloud/v1 | Required: \{\} <br /> |
| `caCertificate` _[CaCertificate](#cacertificate)_ |  |  | Optional: \{\} <br /> |


#### LocalStack



LocalStack is the Schema for the localstacks API



_Appears in:_
- [LocalStackList](#localstacklist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `api.localstack.cloud/v1alpha1` | | |
| `kind` _string_ | `LocalStack` | | |
| `kind` _string_ | Kind is a string value representing the REST resource this object represents.<br />Servers may infer this from the endpoint the client submits requests to.<br />Cannot be updated.<br />In CamelCase.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds |  | Optional: \{\} <br /> |
| `apiVersion` _string_ | APIVersion defines the versioned schema of this representation of an object.<br />Servers should convert recognized schemas to the latest internal value, and<br />may reject unrecognized values.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources |  | Optional: \{\} <br /> |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[LocalStackSpec](#localstackspec)_ |  |  |  |
| `status` _[LocalStackStatus](#localstackstatus)_ |  |  |  |


#### LocalStackList



LocalStackList contains a list of LocalStack





| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `api.localstack.cloud/v1alpha1` | | |
| `kind` _string_ | `LocalStackList` | | |
| `kind` _string_ | Kind is a string value representing the REST resource this object represents.<br />Servers may infer this from the endpoint the client submits requests to.<br />Cannot be updated.<br />In CamelCase.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds |  | Optional: \{\} <br /> |
| `apiVersion` _string_ | APIVersion defines the versioned schema of this representation of an object.<br />Servers should convert recognized schemas to the latest internal value, and<br />may reject unrecognized values.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources |  | Optional: \{\} <br /> |
| `metadata` _[ListMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#listmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `items` _[LocalStack](#localstack) array_ |  |  |  |


#### LocalStackSpec



LocalStackSpec defines the desired state of LocalStack



_Appears in:_
- [LocalStack](#localstack)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `dnsProvider` _string_ |  |  | Enum: [none coredns] <br />Required: \{\} <br /> |
| `dnsConfigName` _string_ |  |  | Required: \{\} <br /> |
| `dnsConfigNamespace` _string_ |  |  | Required: \{\} <br /> |
| `debug` _string_ |  | info | Enum: [trace trace-internal debug info warn error warning] <br />Optional: \{\} <br /> |
| `autoLoadPods` _string array_ |  |  | Optional: \{\} <br /> |
| `authToken` _string_ |  |  | MaxLength: 39 <br />MinLength: 39 <br />Optional: \{\} <br />Pattern: `^ls-[a-zA-Z0-9]\{8\}-[a-zA-Z0-9]\{4\}-[a-zA-Z0-9]\{4\}-[a-zA-Z0-9]\{4\}-[a-zA-Z0-9]\{12\}$` <br /> |
| `pvcName` _string_ | Mount a PVC at /var/lib/localstack providing caching between LocalStack lifetimes |  | Optional: \{\} <br /> |
| `hooks` _[Hooks](#hooks)_ |  |  | Optional: \{\} <br /> |
| `podSchedulingConfig` _[PodSchedulingConfig](#podschedulingconfig)_ | Pod scheduling configuration for services spawned by LocalStack (e.g., Lambda, ECS tasks).<br />Allows configuring tolerations, nodeSelector, and affinity. |  | Optional: \{\} <br /> |
| `licenseServerConfig` _[LicenseServerConfig](#licenseserverconfig)_ |  | \{ endpoint:https://api.localstack.cloud/v1 \} | Optional: \{\} <br /> |
| `image` _string_ | Validate docker inage name (with optional tag and registry address) |  | Pattern: `(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)?(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)*[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*(:[a-zA-Z0-9_.-]+)?` <br />Required: \{\} <br /> |
| `imagePullPolicy` _[PullPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#pullpolicy-v1-core)_ | PullPolicy describes a policy for if/when to pull a container image.<br />If providing an image tag of "latest", the default will be set to "Always", otherwise "IfNotPresent" |  | Enum: [Always IfNotPresent Never] <br />Optional: \{\} <br /> |
| `resources` _[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#resourcerequirements-v1-core)_ |  |  | Optional: \{\} <br /> |
| `readiness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `liveness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `envFrom` _[EnvFromSource](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envfromsource-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `env` _[EnvVar](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envvar-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `dnsPolicy` _[DNSPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#dnspolicy-v1-core)_ |  | ClusterFirst | Enum: [Default ClusterFirst ClusterFirstWithHostNet None] <br />Optional: \{\} <br /> |
| `runAsUser` _integer_ |  | 0 | Enum: [0 1000] <br />Optional: \{\} <br /> |
| `podSecurityContext` _[PodSecurityContext](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#podsecuritycontext-v1-core)_ |  |  | Optional: \{\} <br /> |
| `containerSecurityContext` _[SecurityContext](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#securitycontext-v1-core)_ |  |  | Optional: \{\} <br /> |


#### LocalStackStatus



LocalStackStatus defines the observed state of LocalStack



_Appears in:_
- [LocalStack](#localstack)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `ready` _boolean_ |  |  |  |
| `ip` _string_ |  |  |  |
| `dns` _string_ |  |  |  |


#### PodSchedulingConfig



PodSchedulingConfig defines pod scheduling configuration for services spawned by LocalStack.
This allows configuring tolerations, nodeSelector, and affinity for service-specific pods
(e.g., Lambda, ECS tasks).



_Appears in:_
- [LocalStackSpec](#localstackspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `profiles` _object (keys:string, values:[ServiceSchedulingConfig](#serviceschedulingconfig))_ | Scheduling profiles |  | Optional: \{\} <br /> |
| `services` _object (keys:string, values:[ServiceSchedulingConfig](#serviceschedulingconfig))_ | Service-specific scheduling configuration that overrides defaults.<br />Keys are service names (e.g., "lambda", "ecs", "rds"). |  | Optional: \{\} <br /> |


#### PodSpec







_Appears in:_
- [LocalStackSpec](#localstackspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `image` _string_ | Validate docker inage name (with optional tag and registry address) |  | Pattern: `(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)?(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)*[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*(:[a-zA-Z0-9_.-]+)?` <br />Required: \{\} <br /> |
| `imagePullPolicy` _[PullPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#pullpolicy-v1-core)_ | PullPolicy describes a policy for if/when to pull a container image.<br />If providing an image tag of "latest", the default will be set to "Always", otherwise "IfNotPresent" |  | Enum: [Always IfNotPresent Never] <br />Optional: \{\} <br /> |
| `resources` _[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#resourcerequirements-v1-core)_ |  |  | Optional: \{\} <br /> |
| `readiness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `liveness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `envFrom` _[EnvFromSource](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envfromsource-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `env` _[EnvVar](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envvar-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `dnsPolicy` _[DNSPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#dnspolicy-v1-core)_ |  | ClusterFirst | Enum: [Default ClusterFirst ClusterFirstWithHostNet None] <br />Optional: \{\} <br /> |
| `runAsUser` _integer_ |  | 0 | Enum: [0 1000] <br />Optional: \{\} <br /> |
| `podSecurityContext` _[PodSecurityContext](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#podsecuritycontext-v1-core)_ |  |  | Optional: \{\} <br /> |
| `containerSecurityContext` _[SecurityContext](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#securitycontext-v1-core)_ |  |  | Optional: \{\} <br /> |


#### ServiceSchedulingConfig



ServiceSchedulingConfig defines scheduling configuration for pods spawned by LocalStack services



_Appears in:_
- [PodSchedulingConfig](#podschedulingconfig)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `tolerations` _[Toleration](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#toleration-v1-core) array_ | Tolerations for the pods |  | Optional: \{\} <br /> |
| `nodeSelector` _object (keys:string, values:string)_ | NodeSelector for the pods |  | Optional: \{\} <br /> |
| `affinity` _[Affinity](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#affinity-v1-core)_ | Affinity for the pods |  | Optional: \{\} <br /> |
| `topologySpreadConstraint` _[TopologySpreadConstraint](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#topologyspreadconstraint-v1-core)_ | TopologySpreadConstraint |  | Optional: \{\} <br /> |
| `priorityClassName` _string_ | Priority class name for workloads |  | Optional: \{\} <br /> |
| `resources` _[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#resourcerequirements-v1-core)_ | Pod resources |  | Optional: \{\} <br /> |
| `labels` _object (keys:string, values:string)_ | Custom pod labels |  | Optional: \{\} <br /> |
| `annotations` _object (keys:string, values:string)_ | Custom pod annotations |  | Optional: \{\} <br /> |


