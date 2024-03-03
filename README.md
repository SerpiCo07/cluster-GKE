In this documentaion we I explained step by step how to create a simple web-app usign FLASK and a cluster using GKE, then depoly the application on GKE 

# Web-app using FLASK 
This flask app is supposed to the following tasks :
    
- Receive the name of an object from a pub/sub subscriber
- Ask the bucket within the Google Cloud Storage to send the file directly having giving its name withing the bucket 
- Sort all data within the file
- Send its output to a topic on pub/sub
 
 
 Here's a high-level overview of steps you'd follow, along with adjustments to ensure smooth interaction between GCS and your Flask application running in GKE:
- Containerize Your Flask Application
- Build and Push the Docker Image
- Prepare GKE for Deployment
- Deploy to GKE >> deployment.yaml
- Expose Your Application >> service.yaml

Moreover, don't forget to adjust GCS and GKE for interaction :
- Authentication :
        Since our application interacts with GCS, we should ensure our GKE pods have the correct permissions. With Workload Identity, we can bind Kubernetes service accounts to Google Cloud service accounts with the necessary GCS permissions.
- Configuration :
        Manage sensitive configurations and credentials using Kubernetes Secrets or ConfigMaps, and reference these in your deployment configuration.
## Containerize Your Flask Application

Enable the following APIs:
-Artifact Registry
-Cloud Build
-Google Kubernetes Engine APIs



## Build and Push the Docker Image

The general approach we store our container on Artifact Registry then we deploy it on Cluster from that registry 