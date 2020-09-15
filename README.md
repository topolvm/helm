# TopoLVM Helm Charts for Kubernetes

Provided by [TopoLVM](https://github.com/topolvm/topolvm), ready to launch on Kubernetes using [Kubernetes Helm](https://github.com/helm/helm).

## Before you begin

### Setup a Kubernetes Cluster

For setting up Kubernetes on cloud platforms or bare-metal servers refer to the Kubernetes [getting started guide](http://kubernetes.io/docs/getting-started-guides/).

### Install Helm

Helm is a tool for managing Kubernetes charts. Charts are packages of pre-configured Kubernetes resources.

To install Helm, refer to the [Helm install guide](https://github.com/helm/helm#install) and ensure that the `helm` binary is in the `PATH` of your shell.

### Using Helm

Once you have installed the Helm client, you can deploy a TopoLVM Helm Charts into a Kubernetes cluster.

Please refer to the [Quick Start guide](https://helm.sh/docs/intro/quickstart/) if you wish to get running in just a few commands, otherwise the [Using Helm Guide](https://helm.sh/docs/intro/using_helm/) provides detailed instructions on how to use the Helm client to manage packages on your Kubernetes cluster.

Useful Helm Client Commands:
* View available charts: `helm search repo`
* Install a chart: `helm install my-release topolvm/<package-name>`
* Upgrade your application: `helm upgrade`


