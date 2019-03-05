# k8-jira-nexus

Overview This guide is only showing the high level steps to provision a basic Jira setup This is NOT production ready. Do not run Jira like this in production. These are just notes on the basics. What makes this work 1 Deployment for the Jira server Persistent disk for jira-home directory Usage Create a Volume for Persistence gcloud compute disks create jira-home Jira Deployment kubectl create -f jira-deployment.yaml This may take a while!

