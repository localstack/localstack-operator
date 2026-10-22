# LocalStack Kubernetes Operator

## Requirements

The LocalStack operator requires a LocalStack [auth token](https://docs.localstack.cloud/aws/getting-started/auth-token/) to authorize the use of the operator.

## Installation

You can use `kubectl` to install the LocalStack Operator into your cluster:

```bash
# latest version
kubectl apply -f https://github.com/localstack/localstack-operator/releases/latest/download/controller.yaml

# or specific version, e.g. v0.4.1
kubectl apply -f https://github.com/localstack/localstack-operator/releases/download/v0.4.1/controller.yaml
```
## Upgrading to v0.5.0 or later

> [!WARNING]
> Version 0.5.0 changes the `LocalStack` CRD. Re-apply `controller.yaml` when you upgrade. Updating only the controller image is not enough.

### If you are upgrading from a version before v0.5.0

Apply the new `controller.yaml` the same way you installed the operator. The file contains both the CRD and the controller, so one command updates both:

```bash
kubectl apply -f https://github.com/localstack/localstack-operator/releases/download/v0.5.0/controller.yaml
```

If you only update the controller image and keep the old CRD, Kubernetes drops the new `profile` field as unknown and your per-service settings never reach LocalStack.

### If you used `services` or `topologySpreadConstraint` in `spec.podSchedulingConfig`

Before v0.5.0, the CRD let you write pod settings such as tolerations or resources directly under `services.<name>`. It also had a field called `topologySpreadConstraint` that took a single object. LocalStack never read either of them. After you upgrade, Kubernetes silently removes those fields from your resource, and LocalStack starts without the settings. Your resource will look fine, but the settings will not be applied.

To keep the settings, move them into a named profile under `profiles` and point the service at that profile. Rename `topologySpreadConstraint` to `topologySpreadConstraints` and make it a list.

Before:

```yaml
spec:
  podSchedulingConfig:
    services:
      lambda:
        tolerations:
          - key: gpu
            operator: Exists
        topologySpreadConstraint:
          maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: ScheduleAnyway
```

After:

```yaml
spec:
  podSchedulingConfig:
    profiles:
      lambda-gpu:
        tolerations:
          - key: gpu
            operator: Exists
        topologySpreadConstraints:
          - maxSkew: 1
            topologyKey: topology.kubernetes.io/zone
            whenUnsatisfiable: ScheduleAnyway
    services:
      lambda:
        profile: lambda-gpu
```

Apply the updated resource with `kubectl apply`. If any old field is still present, `kubectl` rejects it with an "unknown field" error that names the field.

If you only used `profiles` and never used `services` or `topologySpreadConstraint`, you do not need to change your resource.


## CRD definition

The operator includes a `LocalStack` CRD which defines your LocalStack instance. See the [api docs](https://github.com/localstack/localstack-operator/tree/main/api-docs.md) for a description of the available fields.
