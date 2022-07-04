[![CircleCI](https://circleci.com/gh/giantswarm/cluster-api-monitoring.svg?style=shield)](https://circleci.com/gh/giantswarm/cluster-api-monitoring)

# cluster-api-monitoring chart

Giant Swarm offers a cluster-api-monitoring `App` which can be installed in management clusters.
Here we define the cluster-api-monitoring chart with its templates and default configuration.

**What is this app?**

`cluster-api-monitoring` is a dedicated [`kube-state-metrics` (`KSM`)](https://github.com/kubernetes/kube-state-metrics) installation with the alpha feature of `CustomResourceStateMetrics` enabled.

**Why did we add it?**

As the current alpha feature has a wide range of limitations and the discussion about new features is still ongoing with the KSM community we had to build this app from a recently created fork of KSM. The goal of this fork is a contribution back to the upstream community but was initialy used to verify if it's worth the effort to maintain a custom metrics exporter, based on KSM `golang` packages.

To not harm the existing `KSM` installation in `kube-system` and make fast progress towards monitoring of ClusterAPI related CRs + the fact that `KSM` is running from a forked version we decided to start creating a new app.

**Who should use it?**

Everyone which needs information from `CustomResource` objects exposed as metric.

## Installing

There are several ways to install this app onto a workload cluster.

- [Using our web interface](https://docs.giantswarm.io/ui-api/web/app-platform/#installing-an-app).
- By creating an [App resource](https://docs.giantswarm.io/ui-api/management-api/crd/apps.application.giantswarm.io/) in the management cluster as explained in [Getting started with App Platform](https://docs.giantswarm.io/app-platform/getting-started/).

## Configuring

If you for example want the conditions of all CRs of type `GitRepository` exposed as metric `flux_gitrepositories_status_conditions` there are two things to do:

First of all, `cluster-api-monitoring` needs a configuration to know how the status condition should be generated as metric.

Therefore, create a file called `flux_gitrepository.yaml` under `helm/cluster-api-monitoring/configuration`. For `flux` it's possible to get a gauge metric based on conditions:

```yaml
labelsFromPath:
  name: [metadata, name]
  url: [spec, url]
  namespace: [metadata, namespace]
metrics:
  - name: status_conditions
    each:
      type: Gauge
      gauge:
        path:
          - status
          - conditions
        valueFrom:
          - status
        labelFromKey: reason
        labelsFromPath:
          type: [type]
```

As we now have a configuration for `GitRepositories` we have to enable this configuration in the `values.yaml` by creating a new object in the `monitoredResource` map:

```yaml
monitoredResources:
  flux:
    gitrepository:
      group: source.toolkit.fluxcd.io
      kind: GitRepository
      version: v1beta2
      plural: gitrepositories
```

### no op (no operation) mode

> As soon as [Allow monitoring of CRs only #1778](https://github.com/kubernetes/kube-state-metrics/issues/1778) is open we have to acknowledge the current no op behavior.

Without any defined `monitoredResources`, `cluster-api-monitoring` is able to run in a `no op` mode. This means the `--resources` argument will be an empty string and therefore `KSM` tries to to scrape all known resources (e.g. `v1.Namespaces`, `v1.Pods`, ...). As `cluster-api-monitoring` is primary designed to monitor `CRs` only and all required permissions are defined in the `ClusterRole`, in the `noop` mode, the `ClusteRole` is empty. Therefore `KSM` will print a bunch of permission errors, e.g. 

```
W0703 18:55:58.809274       1 reflector.go:324] pkg/mod/k8s.io/client-go@v0.24.1/tools/cache/reflector.go:167: failed to list *v1.Namespace: namespaces is forbidden: User "system:serviceaccount:giantswarm:cluster-api-monitoring" cannot list resource "namespaces" in API group "" at the cluster scope
E0703 18:55:58.809332       1 reflector.go:138] pkg/mod/k8s.io/client-go@v0.24.1/tools/cache/reflector.go:167: Failed to watch *v1.Namespace: failed to list *v1.Namespace: namespaces is forbidden: User "system:serviceaccount:giantswarm:cluster-api-monitoring" cannot list resource "namespaces" in API group "" at the cluster scope
W0703 18:55:58.809415       1 reflector.go:324] pkg/mod/k8s.io/client-go@v0.24.1/tools/cache/reflector.go:167: failed to list *v1.ConfigMap: configmaps is forbidden: User "system:serviceaccount:giantswarm:cluster-api-monitoring" cannot list resource "configmaps" in API group "" at the cluster scope                                      
```