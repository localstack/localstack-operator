# LocalStack Kubernetes Operator

## Requirements

The LocalStack operator requires a LocalStack [auth token](https://docs.localstack.cloud/aws/getting-started/auth-token/) to authorize the use of the operator.

## Installation

You can use `kubectl` to install the LocalStack Operator into your cluster:

```bash
# latest version
kubectl apply -f https://github.com/localstack/localstack-operator/releases/latest/download/controller.yaml

# or specific version, e.g. v0.4.0
kubectl apply -f https://github.com/localstack/localstack-operator/releases/v0.4.0/download/controller.yaml
```

## CRD definition

The operator includes a `LocalStack` CRD which defines your LocalStack instance. See the [api docs](https://github.com/localstack/localstack-operator/tree/main/api-docs.md) for a description of the available fields.
