# TopoLVM Helm Chart
# Work IN progress
----------------------------------------

## Pre Requisites
* Kubernetes 1.15+
* `lvmd` installed on the underlying nodes, ref: https://github.com/topolvm/topolvm/blob/master/docs/lvmd.md
* `cert-manager` installed. ref: https://cert-manager.io/
* Requires at least `v3.2.3` version of helm to support
* Namespace named `topolvm-system`:

    ```sh
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
| `image.tag`                     | TopoLVM Container image tag                                                                         | `0.5.3`                      |
| `image.pullPolicy`              | TopoLVM Container pull policy                                                                       | `IfNotPresent`               |
| `controller.replicaCount`       | Number of TopoLVM controllers pods to deploy                                                        | `2`                          |
| `podSecurityPolicy.create`      | Specify if a pod security policy must be created                                                    | `true`                       |

Specify parameters using `--set key=value[,key=value]` argument to `helm install`

Alternatively a YAML file that specifies the values for the parameters can be provided like this:

```sh
helm upgrade -i topolvm -f values.yaml charts/topolvm
```

