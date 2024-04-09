# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.11.0] - 2024-04-09

### Changed

- Add a new label `cluster_id` to comply with vintage metrics.
- Ensure `cluster_type` label is set based on the metrics' source CR.

## [1.10.0] - 2024-03-15

### Changed

- Pull image from Azure CR.

## [1.9.0] - 2024-01-25

### Changed

- Enable CiliumNetworkPolicy by default and add metrics port.

## [1.8.1] - 2024-01-18

### Added

- PSS compliance

## [1.8.0] - 2023-08-07

### Added

- Add cilium network policies support (enabled with `ciliumNetworkPolicy.enabled=true`).

### Removed

- Cleanup comments from `README.md` as all mentioned changes/PRs got merged and released in upstream `KSM`. 

## [1.7.1] - 2023-06-15

### Add

- push to `capz-app-collection`

## [1.7.0] - 2023-06-15

### Add

- New metrics:
  - `capi_cluster_status_condition_last_transition_time`
  - `capi_kubeadmcontrolplane_status_condition_last_transition_time`
  - `capi_machinedeployment_status_condition_last_transition_time`
  - `capi_machinehealthcheck_status_condition_last_transition_time`
  - `capi_machinehealthcheck_info`
  - `capi_machinepool_status_condition_last_transition_time`
  - `capi_machineset_status_condition_last_transition_time`
  - `capi_machine_status_condition_last_transition_time`
- New labels for `capi_machineset_info` metric
  - `bootstrap_reference_kind`
  - `bootstrap_reference_name`
  - `infrastructure_reference_kind`
  - `infrastructure_reference_name`
- New labels for `capi_machine_info` metric
  - `bootstrap_reference_kind`
  - `bootstrap_reference_name`
  - `infrastructure_reference_kind`
  - `infrastructure_reference_name`
  - `control_plane_name` if the machine is a control-plane machine
  
## [1.6.0] - 2023-05-31

### Add

- initial support for Cluster API Provider Cloud Director CRs:
  - `capi_vcdcluster_annotation_paused`
  - `capi_vcdcluster_created`
  - `capi_vcdcluster_info`
  - `capi_vcdcluster_status_conditions`
  - `capi_vcdcluster_status_ready`
  - `capi_vcdmachine_addresses`
  - `capi_vcdmachine_annotation_paused`
  - `capi_vcdmachine_created`
  - `capi_vcdmachine_info`
  - `capi_vcdmachine_owner`
  - `capi_vcdmachine_status_conditions`
  - `capi_vcdmachine_status_ready`

## [1.5.0] - 2023-05-30

### Add

- initial support for Cluster API Provider VSphere CRs:
  - `capi_vspherecluster_annotation_paused`
  - `capi_vspherecluster_created`
  - `capi_vspherecluster_info`
  - `capi_vspherecluster_status_conditions`
  - `capi_vspherecluster_status_ready`
  - `capi_vspheremachine_addresses`
  - `capi_vspheremachine_annotation_paused`
  - `capi_vspheremachine_created`
  - `capi_vspheremachine_info`
  - `capi_vspheremachine_network_info`
  - `capi_vspheremachine_owner`
  - `capi_vspheremachine_status_conditions`
  - `capi_vspheremachine_status_ready`
  - `capi_vspherevm_created`
  - `capi_vspherevm_owner`
  - `capi_vspherevm_status_conditions`
  - `capi_vspherevm_status_ready`

### Removed

- Stop pushing to `openstack-app-collection`.

## [1.4.0] - 2023-03-01

### Change

- Bump `kube-state-metrics` to stable version `2.8.1`
- Rename `capi_azuremachine_status_addresses` to `capi_azuremachine_addresses` to align with `capi_machine_addresses`
- Rename `capi_azuremachinepool_status_addresses` to `capi_azuremachinepool_addresses` to align with `capi_machine_addresses`
- Align label generation for `capi_azuremachine_addresses` and `capi_azuremachinepool_addresses` with `capi_machine_addresses`

## [1.3.1] - 2023-01-17

## [1.3.0] - 2023-01-10

### Change

- Drop `uid` label to reduce cardinality

### Add

- initial support for Cluster API Provider Azure CRs:
  - `capi_azurecluster_annotation_paused`
  - `capi_azurecluster_created`
  - `capi_azurecluster_info`
  - `capi_azurecluster_owner`
  - `capi_azurecluster_status_conditions`
  - `capi_azurecluster_status_ready`
  - `capi_azuremachine_annotation_paused`
  - `capi_azuremachine_created`
  - `capi_azuremachine_info`
  - `capi_azuremachine_owner`
  - `capi_azuremachine_status_addresses`
  - `capi_azuremachine_status_conditions`
  - `capi_azuremachine_status_ready`
  - `capi_azuremachinepool_annotation_paused`
  - `capi_azuremachinepool_created`
  - `capi_azuremachinepool_info`
  - `capi_azuremachinepool_owner`
  - `capi_azuremachinepool_status_addresses`
  - `capi_azuremachinepool_status_conditions`
  - `capi_azuremachinepool_status_image_info`
  - `capi_azuremachinepool_status_ready`
  - `capi_azuremachinepool_status_replicas`
  - `capi_azuremachinepoolmachine_annotation_paused`
  - `capi_azuremachinepoolmachine_created`
  - `capi_azuremachinepoolmachine_owner`
  - `capi_azuremachinepoolmachine_status_conditions`
  - `capi_azuremachinepoolmachine_status_image_info`
  - `capi_azuremachinepoolmachine_status_latest_model_applied`
  - `capi_azuremachinepoolmachine_status_ready`
  - `capi_azuremachinepoolmachine_status_version`

### Fixed

- Fix PSP seccomp profile for CAPA and CAPG.

## [1.2.0] - 2023-01-09

### Add

- Add Pod Security Policy for CAPA and CAPG.

## [1.1.0] - 2023-01-09

### Add

- initial support for Cluster API `MachinePools` add the following metrics:
  - `capi_machinepool_annotation_paused`
  - `capi_machinepool_created`
  - `capi_machinepool_info`
  - `capi_machinepool_owner`
  - `capi_machinepool_spec_replicas`
  - `capi_machinepool_status_condition`
  - `capi_machinepool_status_phase`
  - `capi_machinepool_status_replicas`
  - `capi_machinepool_status_replicas_available`
  - `capi_machinepool_status_replicas_ready`
  - `capi_machinepool_status_replicas_unavailable`

### Change


- `cluster_name` label from `capi_cluster` metrics got removed as the value is a duplicate of the `name` label
- Align all `capi` metrics with upstream
  - `capi_machinedeployment_status_unavailable_replicas` changed to `capi_machinedeployment_status_replicas_unavailable`
  - `*_status_conditions` changed to `*_status_condition` (plural to singular)
- Moved from `ServiceMonitor` to `PodMonitor` as there the service itself isn't used
- Remove `plural` from configuration as not needed anymore for `kube-state-metrics` to run
- Update to `kube-state-metrics` version `v2.7.0`
- Change back to upstream `kube-state-metrics` image

## [1.0.0] - 2022-07-12

### Add

- initial support for Cluster API `kubeadmcontrolplanes`:
  - `capi_kubeadmcontrolplane_created`
  - `capi_kubeadmcontrolplane_info`
  - `capi_kubeadmcontrolplane_owner`
  - `capi_kubeadmcontrolplane_spec_replicas`
  - `capi_kubeadmcontrolplane_spec_strategy_rollingupdate_max_surge`
  - `capi_kubeadmcontrolplane_status_conditions`
  - `capi_kubeadmcontrolplane_status_replicas_ready`
  - `capi_kubeadmcontrolplane_status_replicas_unavailable`
  - `capi_kubeadmcontrolplane_status_replicas_updated`
- initial support for Cluster API `machinehealthchecks`:
  - `capi_machinehealthcheck_created`
  - `capi_machinehealthcheck_status_current_healthy`
  - `capi_machinehealthcheck_status_expected_machines`
  - `capi_machinehealthcheck_status_remediations_allowed`
- initial support for Cluster API `machinedeployments`:
  - `capi_machinedeployment_info`
  - `capi_machinedeployment_created`
  - `capi_machinedeployment_status_conditions`
  - `capi_machinedeployment_spec_replicas`
  - `capi_machinedeployment_spec_paused`
  - `capi_machinedeployment_status_replicas`
  - `capi_machinedeployment_status_replicas_ready`
  - `capi_machinedeployment_status_replicas_available`
  - `capi_machinedeployment_status_replicas_unavailable`
  - `capi_machinedeployment_status_phase`
- initial support for Cluster API `openstackclusters`:
  - `capi_openstackcluster_info`
  - `capi_openstackcluster_created`
  - `capi_openstackcluster_status_failure`
  - `capi_openstackcluster_status_loadbalancer`
  - `capi_openstackcluster_status_bastion`
- initial support for Cluster API `openstackmachines`:
  - `capi_openstackmachine_info`
  - `capi_openstackmachine_created`
  - `capi_openstackmachine_volume_disk_size`
  - `capi_openstackmachine_status_instance_state`
  - `capi_openstackmachine_status_failure`
- initial support for Cluster API `machines`:
  - `capi_machine_info`
  - `capi_machine_created`
  - `capi_machine_status_conditions`
  - `capi_machine_status_phase`
- initial support for Cluster API `clusters`:
  - `capi_cluster_info`
  - `capi_cluster_created`
  - `capi_cluster_spec_paused`
  - `capi_cluster_status_conditions`
  - `capi_cluster_status_phase`

[Unreleased]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.11.0...HEAD
[1.11.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.10.0...v1.11.0
[1.10.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.9.0...v1.10.0
[1.9.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.8.1...v1.9.0
[1.8.1]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.8.0...v1.8.1
[1.8.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.7.1...v1.8.0
[1.7.1]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.7.0...v1.7.1
[1.7.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.6.0...v1.7.0
[1.6.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.5.0...v1.6.0
[1.5.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.4.0...v1.5.0
[1.4.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.3.1...v1.4.0
[1.3.1]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.3.0...v1.3.1
[1.3.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.2.0...v1.3.0
[1.2.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/giantswarm/cluster-api-monitoring-app/releases/tag/v1.0.0
