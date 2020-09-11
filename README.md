# GCP_Practice_Project

Google Cloud Fundamentals: Getting Started with GKE:

```sh
gcloud config set project qwiklabs-gcp-00-d9731b439b2b

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
