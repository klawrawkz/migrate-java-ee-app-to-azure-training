# Setting up Azure Kubernetes Service

## What are we going to do in this step

In this step we are going to setup access to your Azure Kubernetes Service (AKS)
cluster.

## Start in the correct directory

Please execute the command below:

```shell
cd /mnt/02-setting-up-aks
```

> :bulb: If you are interested to know what steps the provisioning script took to
> provision your Azure Kubernetes Service cluster, see
> [Manual Provisioning steps](MANUAL.md)

## Get the Kubernetes config file

In order to access the Kubernetes cluster using `kubectl` you will need a Kube
config file.

> :pushpin: Note as the purpose of this training is migrating the JavaEE
> application to AKS and not Kubernetes administration we are using admin access
> to the AKS cluster. For production environments we recommend
> [configuring RBAC](https://docs.microsoft.com/en-us/azure/aks/azure-ad-rbac)
> to limit access to your Kubernetes cluster based on roles.

Execute the following command line:

```shell
az aks get-credentials --resource-group sharearound \
  --name sharearound-aks-$UNIQUE_ID --admin --file kubeconfig
```

This will create the Kube config file in `kubeconfig`

## Set the KUBECONFIG environment variable

Execute the command line below:

```shell
export KUBECONFIG=$PWD/kubeconfig
```

This set the KUBECONFIG environment variable to point to the `kubeconfig` file
so `kubectl` will be able to interact with your AKS cluster.

## List the nodes in your AKS cluster

To verify you can work with your cluster we are going to ask the cluster for the
information on the Kubernetes nodes in your cluster.

Execute the following command line:

```shell
kubectl get nodes
```

This should show you the list of nodes in your Kubernetes cluster.

> :stop_sign: If you are getting errors on this command, please go to the
> Azure Portal to verify the deployment of the Azure Kubernetes Cluster
> has completed. If it has not completed wait until it has completed
> and then try to command above again.

## What you accomplished

1. You have created a Kubeconfig file for use by `kubectl`.
1. You have verified you can see the nodes of your AKS cluster.

## More information

For more information about AKS, see:

1. [Azure Kubernetes Service product page](https://azure.microsoft.com/en-us/services/kubernetes-service/)
1. [Azure Kubernetes Service documentation](https://docs.microsoft.com/en-us/azure/aks/)
1. [Azure CLI commands for AKS](https://docs.microsoft.com/en-us/cli/azure/aks?view=azure-cli-latest)
1. [Kubectl Reference Documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)

[Previous](../02-setting-up-acr/README.md) &nbsp; [Next](../04-migrating-web-pages/README.md)
