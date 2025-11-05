# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

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

[0.3.3]: https://github.com/localstack/localstack-operator-public/releases/tag/v0.3.3
