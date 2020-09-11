# GCP_Practice_Project_Overview

## Lab: Google Cloud Fundamentals: Getting Started with GKE:  


```sh

#Confirm that needed APIs are enabled
gcloud services enable container.googleapis.com
gcloud services enable containerregistry.googleapis.com


#Start a Kubernetes Engine cluster
export MY_ZONE=us-central1-a
gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2
kubectl version


#Run and deploy a container
kubectl create deploy nginx --image=nginx:1.17.10
kubectl get pods
kubectl expose deployment nginx --port 80 --type LoadBalancer
kubectl get services
kubectl scale deployment nginx --replicas 3
kubectl get pods
kubectl get services
```


## Lab: Google Cloud Fundamentals: Getting Started with Compute Engine:

```sh
#Create a virtual machine using the GCP Console
gcloud compute instances create my-vm-1 --zone "us-central1-a" --machine-type "e2-medium" 
--subnet "default" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --tags http

gcloud compute firewall-rules create allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=http:80 --target-tags=http

# Create a virtual machine using the gcloud command line
gcloud compute zones list | grep us-central1

gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" 
--subnet "default"


#Connect between VM instances
gcloud compute ssh "my-vm-2"
ping my-vm-1
ssh my-vm-1
sudo apt-get install nginx-light -y
sudo nano /var/www/html/index.nginx-debian.html
```  
Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this "Hi from Hazem" then save & exit.

```sh
curl http://localhost/
exit
curl http://my-vm-1/
```


