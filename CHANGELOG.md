# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [0.4.8] - 2026-06-16

### Fixed

* CoreDNS Corefile corruption with multiple LocalStack instances
* Security updates to fix
    * CVE-2026-42504

## [0.4.7] - 2026-05-28

### Added

* Supports `PodSchedulingConfig` to control where pods are executed

### Fixed

* Fixed license version matching

## [0.4.6] - 2026-05-19

### Fixed

* Security updates to fix
    * CVE-2026-33811 
    * CVE-2026-33814 
    * CVE-2026-39820 
    * CVE-2026-39836 
    * CVE-2026-42499 

## [0.4.5] - 2026-04-28

### Fixed

* Security updates to fix CVE-2026-39883

## [0.4.4] - 2026-04-08

### Fixed

* Security Updates to fix CVE-2026-33186 and CVE-2026-24051

## [0.4.3] - 2026-03-16

### Added

* Option to disable ssl enforcement during license check (set `LOCALSTACK_LICENSE_SSL_NO_VERIFY=1` for the operator pod)

### Changed

* Removed the rbac-proxy image and updated the kubebuilder authentication method for the metrics endpoint

## [0.4.2] - 2026-01-28

### Fixed

* Fixed not setting the `searches` field of the `dnsConfig` for the LocalStack pod when running as a non-root user

## [0.4.1] - 2025-12-16

### Added

* Support for specifying a custom CA certificate when fetching the license. See the `caCertificate` field of the `LocalStack` CRD object in the api docs for more information

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

[0.4.7]: https://github.com/localstack/localstack-operator/compare/v0.4.6..v0.4.7
[0.4.6]: https://github.com/localstack/localstack-operator/compare/v0.4.5..v0.4.6
[0.4.5]: https://github.com/localstack/localstack-operator/compare/v0.4.4..v0.4.5
[0.4.4]: https://github.com/localstack/localstack-operator/compare/v0.4.3..v0.4.4
[0.4.3]: https://github.com/localstack/localstack-operator/compare/v0.4.2..v0.4.3
[0.4.2]: https://github.com/localstack/localstack-operator/compare/v0.4.1..v0.4.2
[0.4.1]: https://github.com/localstack/localstack-operator/compare/v0.4.0..v0.4.1
[0.4.0]: https://github.com/localstack/localstack-operator/compare/v0.3.3..v0.4.0
[0.3.3]: https://github.com/localstack/localstack-operator/releases/tag/v0.3.3
