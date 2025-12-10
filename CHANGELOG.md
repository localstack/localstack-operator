# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.4.0] - 2025-12-09

### Added

* Expand RBAC permissions to support creating EC2 instances (pods)
* Added functionality to support running in non-root environments
* Support setting `PodSecurityContext` and `ContainerSecurityContext` for the LocalStack pod
* Support mounting the [LocalStack volume](https://docs.localstack.cloud/aws/capabilities/config/filesystem/#localstack-volume) with a PVC
* Support overriding the default image pull policy. This defaults to `Always` if the image tag is `latest`, otherwise `IfNotPresent`

### Fixed

* Present better feedback if the auth token can be read from a secret, but the secret value is blank
* Prevent endless AAAA DNS request loops

### Changed

* Bumped version of Go used to compile the operator to 1.25 resolving numerous CVEs


## [0.3.3] - 2025-08-23

### Added

### Fixed

* Using `ClusterFirst` as the dns policy rather than `Default` which is not a valid setting
* Filter kubectl annotations before forwarding them to child pods to remove any annotations starting with `kubectl.kubernetes.io`
* Set the default lambda runtime timeout to 60 seconds
* Add RBAC policies to support running RDS clusters
    * Added pods/exec and pods/log for the operator

### Changed

* Do not change the ulimit at pod startup

### Removed

[0.4.0]: https://github.com/localstack/localstack-operator/releases/tag/v0.4.0
[0.3.3]: https://github.com/localstack/localstack-operator/releases/tag/v0.3.3
