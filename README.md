Pre-requistes:
1. Amazon EKS Cluster is setup and running. 
Switch to Jenkins user
sudo su - jenkins

Create EKS Cluster with two worker nodes using eksctl
eksctl create cluster --name demo-eks --region us-east-2 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2

the above command should create a EKS cluster in AWS, it might take 15 to 20 mins. The eksctl tool uses CloudFormation under the hood, creating one stack for the EKS master control plane and another stack for the worker nodes. 

2. Create ECR repo in AWS
4. Jenkins Master is up and running
5. Docker installed on Jenkins instance 
6. Docker, Docker pipeline and Kubernetes CLI plug-ins are installed in Jenkins






6. Install kubectl on your instance

Step # 1 - Create Maven3 variable under Global tool configuration in Jenkins
Make sure you create Maven3 variable under Global tool configuration. 


Step #2 - Create Credentials for connecting to Kubernetes Cluster using kubeconfig
Click on Add Credentials, use Kubernetes configuration from drop down.


use secret file from drop down.



execute the below command to login as jenkins user.
sudo su - jenkins

you should see the nodes running in EKS cluster.

kubectl get nodes



Execute the below command to get kubeconfig info, copy the entire content of the file:
cat /var/lib/jenkins/.kube/config



Open your text editor or notepad, copy and paste the entire content and save in a file.
We will upload this file.


Enter ID as K8S and choose File and upload the file and save.



Enter ID as K8S and choose enter directly and paste the above file content and save.

Step # 3 - Create a pipeline in Jenkins
Create a new pipeline job.


Step # 4 - 
Your docker user id should be updated.
your registry credentials ID from Jenkins from step # 1 should be copied
