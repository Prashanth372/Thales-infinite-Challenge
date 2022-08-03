# Thales-infinite-Challenge
## Assumption is we are using public cloud kubernetes cluster (EKS)

Below is the solution for the task1.

"kubectl apply -f php-deployment.yml"
`kubectl get all`
`kubectl apply -f hpa3.yml`
`kubectl get all`
`kubectl apply -f pdb.yml`
`kubectl apply -f sa.yaml`
`kubectl get sa`
`kubectl get secrets`
`kubectl apply -f secret-password1.yml`
`kubectl get pods`
`kubectl exec --stdin --tty php-apache-5df567968c-4z4cl -- /bin/bash`

Creation of deployment, by running the below command it will create 2 pods(replica set) of php application.
It also create Node port service.
kubectl apply -f php-deployment.yml

Once this is created next step is to create HPA (horizontal pod autoscaler).
In order to verify the load, verify if the metric server is available or not .
if not available pelase install by using the below commnand.
< to fill cmd>
Once the metric serve is in place to create the load please execute the below command which will increase the load - once HPA verification is completed kill it by using ctrl+c.

< to fill cmd>
Next to this we will create PDB and service account.

Once PDB is created it will allow max one pod to be unavailable as per our instructions.

Log in to pod to check if the API token is visible as environment variable or not by 
kubectl exec --stdin --tty <php-apache-5df567968c-4z4cl> -- /bin/bash 
  echo $API_TOKEN
apt install curl 
  now verify your nodeport service by executing curl command.
  curl nodeip:port (port from kubectl get pods -o wide )
  eg: curl 10.57.**.211:32048

