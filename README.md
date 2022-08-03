# Thales-infinite-Challenge
## Assumption is we are using public cloud kubernetes cluster (EKS)

## Solution for the Task 1 ##


`-` Creation of deployment, by running the below command it will create 2 pods(replica set) of php application.

`-` It also create Node port service.

 kubectl apply -f php-deployment.yml

`-` Once this is created next step is to create HPA (Horizontal Pod Autoscaler).

`-` In order to verify the load, verify if the metric server is available or not .

`-` if not available please install by using the below command.

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

`-` Once the metric serve is in place to create the load please execute the below command which will increase the load - once HPA verification is completed kill it by using ctrl+c.

kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"

`-` Next to this we will create PDB and service account.

`-` Once PDB is created it will allow max one pod to be unavailable as per our instructions.

`-` Log in to pod to check if the API token is visible as environment variable or not by executing 

kubectl exec --stdin --tty <php-apache-5df567968c-4z4cl> -- /bin/bash 

  To verify value of secret   echo $API_TOKEN
  
apt install curl (to verify nodeport)
  
`-` now verify your nodeport service by executing curl command.
  
  curl nodeip:port (port from kubectl get pods -o wide )
  
  eg: curl 10.57.**.211:32048
## Please find the useful commands used 
  
* kubectl apply -f php-deployment.yml
* kubectl get all
* kubectl apply -f hpa3.yml
* kubectl get all
* kubectl apply -f pdb.yml
* kubectl apply -f sa.yaml
* kubectl get sa
* kubectl get secrets
* kubectl apply -f secret-password1.yml
* kubectl get pods
* kubectl exec --stdin --tty php-apache-5df567968c-4z4cl -- /bin/bash
