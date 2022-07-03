# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Add

- initial support for Cluster API machinehealthcheck
  - `capi_machinehealthcheck_status_current_healthy`
  - `capi_machinehealthcheck_status_expected_machines`
  - `capi_machinehealthcheck_status_remediations_allowed`
- initial support for Cluster API machinedeployments
  - `capi_machinedeployment_info`
  - `capi_machinedeployment_status_conditions`
  - `capi_machinedeployment_spec_replicas`
  - `capi_machinedeployment_status_replicas`
  - `capi_machinedeployment_status_ready_replicas`
  - `capi_machinedeployment_status_available_replicas`
  - `capi_machinedeployment_status_unavailable_replicas`
  - `capi_machinedeployment_status_phase`
- initial support for Cluster API openstack
  - `capi_openstackcluster_info`
  - `capi_openstackcluster_status_failure`
  - `capi_openstackcluster_status_loadbalancer`
  - `capi_openstackcluster_status_bastion`
  - `capi_openstackmachine_info`
  - `capi_openstackmachine_volume_disk_size`
  - `capi_openstackmachine_status_instance_state`
  - `capi_openstackmachine_status_failure`
- initial support for Cluster API machines
  - `capi_machine_info`
  - `capi_machine_status_conditions`
  - `capi_machine_status_phase`
- initialize the "empty" app with serviceaccount only

[Unreleased]: https://github.com/giantswarm/{APP-NAME}/tree/main
