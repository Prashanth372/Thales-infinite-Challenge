# Thales-infinite-Challenge
## Assumption is we are using public cloud kubernetes cluster (EKS)

Below is the solution for the task1.


Creation of deployment, by running the below command it will create 2 pods(replica set) of php application.
It also create Node port service.
kubectl apply -f 
Once this is created next step is to create HPA (horizontal pod autoscaler).

Next to this we will create PDB and service account.

Once PDB is created it will allow max one pod to be unavailable as per our instructions.

