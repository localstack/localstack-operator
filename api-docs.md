# API Reference

## Packages
- [api.localstack.cloud/v1alpha1](#apilocalstackcloudv1alpha1)


## api.localstack.cloud/v1alpha1

Package v1alpha1 contains API Schema definitions for the api v1alpha1 API group

### Resource Types
- [LocalStack](#localstack)
- [LocalStackList](#localstacklist)



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


#### LocalStack



LocalStack is the Schema for the localstacks API



_Appears in:_
- [LocalStackList](#localstacklist)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `api.localstack.cloud/v1alpha1` | | |
| `kind` _string_ | `LocalStack` | | |
| `kind` _string_ | Kind is a string value representing the REST resource this object represents.<br />Servers may infer this from the endpoint the client submits requests to.<br />Cannot be updated.<br />In CamelCase.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds |  |  |
| `apiVersion` _string_ | APIVersion defines the versioned schema of this representation of an object.<br />Servers should convert recognized schemas to the latest internal value, and<br />may reject unrecognized values.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources |  |  |
| `metadata` _[ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#objectmeta-v1-meta)_ | Refer to Kubernetes API documentation for fields of `metadata`. |  |  |
| `spec` _[LocalStackSpec](#localstackspec)_ |  |  |  |
| `status` _[LocalStackStatus](#localstackstatus)_ |  |  |  |


#### LocalStackList



LocalStackList contains a list of LocalStack





| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `apiVersion` _string_ | `api.localstack.cloud/v1alpha1` | | |
| `kind` _string_ | `LocalStackList` | | |
| `kind` _string_ | Kind is a string value representing the REST resource this object represents.<br />Servers may infer this from the endpoint the client submits requests to.<br />Cannot be updated.<br />In CamelCase.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#types-kinds |  |  |
| `apiVersion` _string_ | APIVersion defines the versioned schema of this representation of an object.<br />Servers should convert recognized schemas to the latest internal value, and<br />may reject unrecognized values.<br />More info: https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#resources |  |  |
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
| `hooks` _[Hooks](#hooks)_ |  |  | Optional: \{\} <br /> |
| `licenseServerConfig` _[LicenseServerConfig](#licenseserverconfig)_ |  | \{ endpoint:https://api.localstack.cloud/v1 \} | Optional: \{\} <br /> |
| `image` _string_ | Validate docker inage name (with optional tag and registry address) |  | Pattern: `(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)?(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)*[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*(:[a-zA-Z0-9_.-]+)?` <br />Required: \{\} <br /> |
| `resources` _[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#resourcerequirements-v1-core)_ |  |  | Optional: \{\} <br /> |
| `readiness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `liveness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `envFrom` _[EnvFromSource](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envfromsource-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `env` _[EnvVar](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envvar-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `dnsPolicy` _[DNSPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#dnspolicy-v1-core)_ |  | ClusterFirst | Enum: [Default ClusterFirst ClusterFirstWithHostNet None] <br />Optional: \{\} <br /> |
| `runAsUser` _integer_ |  | 0 | Enum: [0 1000] <br />Optional: \{\} <br /> |


#### LocalStackStatus



LocalStackStatus defines the observed state of LocalStack



_Appears in:_
- [LocalStack](#localstack)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `ready` _boolean_ |  |  |  |
| `ip` _string_ |  |  |  |
| `dns` _string_ |  |  |  |


#### PodSpec







_Appears in:_
- [LocalStackSpec](#localstackspec)

| Field | Description | Default | Validation |
| --- | --- | --- | --- |
| `image` _string_ | Validate docker inage name (with optional tag and registry address) |  | Pattern: `(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)?(?:[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*\/)*[a-zA-Z0-9]+(?:[._-][a-zA-Z0-9]+)*(:[a-zA-Z0-9_.-]+)?` <br />Required: \{\} <br /> |
| `resources` _[ResourceRequirements](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#resourcerequirements-v1-core)_ |  |  | Optional: \{\} <br /> |
| `readiness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `liveness_probe` _[Probe](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#probe-v1-core)_ |  |  | Optional: \{\} <br /> |
| `envFrom` _[EnvFromSource](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envfromsource-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `env` _[EnvVar](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#envvar-v1-core) array_ |  |  | Optional: \{\} <br /> |
| `dnsPolicy` _[DNSPolicy](https://kubernetes.io/docs/reference/generated/kubernetes-api/v/#dnspolicy-v1-core)_ |  | ClusterFirst | Enum: [Default ClusterFirst ClusterFirstWithHostNet None] <br />Optional: \{\} <br /> |
| `runAsUser` _integer_ |  | 0 | Enum: [0 1000] <br />Optional: \{\} <br /> |


