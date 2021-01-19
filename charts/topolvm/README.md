# TopoLVM Helm Chart
----------------------------------------

## Pre Requisites
* Kubernetes 1.16+
* `lvmd` installed on the underlying nodes, ref: https://github.com/topolvm/topolvm/blob/master/docs/lvmd.md
* Configure `kube-scheduler` on the underlying nodes, ref: https://github.com/topolvm/topolvm/tree/master/deploy#configure-kube-scheduler
* `cert-manager` version `v1.0.0+` installed. ref: https://cert-manager.io/
* Requires at least `v3.2.3` version of helm to support
* Namespace named `topolvm-system` with the relevant labels:

    ```
    kubectl apply -f charts/topolvm/namespace.yaml
    ```

### Installing the Chart
To install the chart with the release name `topolvm` using a dedicated namespace(recommended):

```sh
helm upgrade -i topolvm charts/topolvm --namespace=topolvm-system
```

The chart can be customized using the following configurable parameters:

| Parameter                       | Description                                                                                         | Default                      |
| ------------------------------- | ----------------------------------------------------------------------------------------------------| -----------------------------|
| `image.repository`              | TopoLVM Container image name                                                                        | `quay.io/topolvm/topolvm`    |
| `image.tag`                     | TopoLVM Container image tag                                                                         | `0.6.0`                      |
| `image.pullPolicy`              | TopoLVM Container pull policy                                                                       | `IfNotPresent`               |
| `controller.replicaCount`       | Number of TopoLVM controllers pods to deploy                                                        | `2`                          |
| `podSecurityPolicy.create`      | Specify if a pod security policy must be created                                                    | `true`                       |

Specify parameters using `--set key=value[,key=value]` argument to `helm install`

Alternatively a YAML file that specifies the values for the parameters can be provided like this:

```sh
helm upgrade -i topolvm -f values.yaml charts/topolvm
```

---

Dont forget to:
kubectl label namespace kube-system topolvm.cybozu.com/webhook=ignore
install the kube-scheduler plugin as described in the "Configure kube-scheduler" section of /deploy/README.md
Config is automatically copied to the masters at /etc/topolvm/scheduler when deployed as a daemonset and kubeScheduler.managed=true
