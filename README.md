# k8-jira-nexus

Overview This guide is only showing the high level steps to provision a basic Jira setup This is NOT production ready. Do not run Jira like this in production. These are just notes on the basics. What makes this work 1 Deployment for the Jira server Persistent disk for jira-home directory Usage Create a Volume for Persistence gcloud compute disks create jira-home Jira Deployment kubectl create -f jira-deployment.yaml This may take a while!


# nexus-deployment.yml
Run : kubectl create -f nexus-deployment.yml


This will create a 'deployment' called 'nexus-deployment' under namespace 'nexus'. It sets the replica to 1, attaches the label 'app: nexus' to deployment. And does the following:


Dowloads the container image


Attaches the volume to the container


Sets env inside the container * This step is explained and found in the Docker Hub under Nexus image


Sets the resources request for the container


Exposes port 8081 of the container (Nexus uses port 8081)


Mounts the volume to a path inside the container
