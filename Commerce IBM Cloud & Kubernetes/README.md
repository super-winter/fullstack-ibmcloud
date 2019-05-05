# ibmcloud-commerce-kubernetes
Step by Step to deploy the IBM WebSphere Commerce Container into Kubernetes, IBM Cloud

#### Summary
- [X] [IBM Docker Registry Console](https://cloud.ibm.com/kubernetes/registry/main/images)
- [X] [IBM Cloud Kubernetes](https://cloud.ibm.com/kubernetes/clusters)
- [X] Design and Implement your Commerce App on IBM Cloud.
- [X] Scale your App on IBM Cloud.

### Welcome to IBM Registry Container
Let's get started by installing the needed CLIs, setting up your first private registry namespace, and pushing your first image.

1. [Install the IBM Cloud CLI](https://cloud.ibm.com/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli)

2. [Install the Docker CLI.](https://docs.docker.com/engine/installation/)

3. Install the Container Registry plug-in.

:large_blue_circle:`ibmcloud plugin install container-registry -r Bluemix`

4. Log in to your IBM Cloud account.

:large_blue_circle:`ibmcloud login -a https://cloud.ibm.com --sso`

5. Choose a name for your first namespace, and create that namespace. Use this namespace for the rest of the Quick Start.

:large_blue_circle:`ibmcloud cr namespace-add gars`

### Push the image to your private registry
1. Log your local Docker daemon into the IBM Cloud Container Registry.

:large_blue_circle:`ibmcloud cr login`

2. Pull the test image from IBM Cloud Container Registry.

:large_blue_circle:`docker pull us.icr.io/gars/commerce:lbcluster`

3. Choose a repository and tag by which you can identify the image. Use the same repository and tag for the rest of this Quick Start.

:large_blue_circle:`docker tag us.icr.io/gars/commerce:lbcluster us.icr.io/<namespace>/commerce:lbcluster`

4. Push the image.

:large_blue_circle:`docker push us.icr.io/<namespace>/commerce:lbcluster`

5. Verify that your image is in your private registry.

:large_blue_circle:`ibmcloud cr image-list`

### Welcome to IBM Cloud Kubernetes

### Gain access to your cluster

Download and install a few CLI tools and the Kubernetes Service plug-in.

:large_blue_circle:`curl -sL https://ibm.biz/idt-installer | bash`

1. Log in to your IBM Cloud account.

:large_blue_circle:`ibmcloud login -a https://cloud.ibm.com --sso`

2. Target the Kubernetes Service region in which you want to work.

:large_blue_circle:`ibmcloud ks region-set us-south`

3. Get the command to set the environment variable and download the Kubernetes configuration files.

:large_blue_circle:`ibmcloud ks cluster-config gars_disaster_recovery`

4. Set the KUBECONFIG environment variable. Copy the output from the previous command and paste it in your terminal. The command output should look similar to the following.

:large_blue_circle:`export KUBECONFIG=/Users/igor/.bluemix/plugins/container-service/clusters/gars_disaster_recovery/kube-config-hou02-gars_disaster_recovery.yml`

Alternatively, you can directly download your kubeconfig files to manually configure the cluster context.

5. Verify that you can connect to your cluster by listing your worker nodes.

:large_blue_circle:`kubectl get nodes`

6. Deploy to a Kubernetes services 

:large_blue_circle:`kubectl run commerce-web --image=us.icr.io/<namespace>/commerce:lbcluster`

![](https://github.com/imvieira/fullstack-ibmcloud/blob/master/Commerce%20IBM%20Cloud%20&%20Kubernetes/Kube_port_forward_Commerce.gif?raw=true)
