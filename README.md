# GCP_Practice_Project

## Google Cloud Fundamentals: Getting Started with GKE:  
![image 1](Mails%20Snapshots/1.PNG)  

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


## Google Cloud Fundamentals: Getting Started with Compute Engine

```sh
#Create a virtual machine using the GCP Console
gcloud beta compute --project=qwiklabs-gcp-02-d18343694552 instances create my-vm-1 --zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE --service-account=324311420145-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --tags=http-server --image=debian-9-stretch-v20200910 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=my-vm-1 --reservation-affinity=any

gcloud compute --project=qwiklabs-gcp-02-d18343694552 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server


# Create a virtual machine using the gcloud command line
gcloud compute zones list | grep us-central1
gcloud config set compute/zone us-central1-b
gcloud compute instances create "my-vm-2" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \
--subnet "default"
exit


#Connect between VM instances
gcloud beta compute ssh --zone "us-central1-b" "my-vm-2" --project "qwiklabs-gcp-02-d18343694552"
ping my-vm-1
ssh my-vm-1
sudo apt-get install nginx-light -y
sudo nano /var/www/html/index.nginx-debian.html
```  
Write "Hi from Hazem" then save & quit.  
```sh
curl http://localhost/
exit
curl http://my-vm-1/
```


