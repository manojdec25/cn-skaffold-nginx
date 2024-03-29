# cn-skaffold-nginx
Coud Native Skaffold based Nginx Service Deployment

Here is a simple cloud native nginx deployment using the skaffold tool. Below document show how you can deploy them in a minikube environment.

Pre-req: 
Please make sure you install docker, minikube, skaffold.

**Step-1: Setup minikube environment**

Start the minikube

    minikube start -p my-dep-env

set the skaffold config to minikube environment

    skaffold config set --kube-context my-dep-env local-cluster true

Change your docker environment to refer to minikube docker environment

    source <(minikube docker-env -p my-dep-env)

**Step-2: Build and Run Skaffold**

To build the image use the below command 

    skaffold build

Run the below command to deploy and run the nginx web service on the minikube

    skaffold run

This should deploy the nginx pod, deployment and service. 

**Step-3: Check pod, deployment and service status**

To check if the kubernetes deployment is success and the service created

    kubetcl get pods,svc -A

To expose the nignx service via minikube

    minikube service mynginx -p my-dep-env

This will open the browser and show the nginx service running.

**Step-4: Check the nginx web service or application**


**Step-5: Clean up**
