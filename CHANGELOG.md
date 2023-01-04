# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

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

[Unreleased]: https://github.com/giantswarm/cluster-api-monitoring-app/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/giantswarm/cluster-api-monitoring-app/releases/tag/v1.0.0
