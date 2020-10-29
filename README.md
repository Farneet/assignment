# assignment
This repository is created for DevOps assignment

# Performing all the modules Step by Step
Note: Each module has its own README.md file . Follow readme for each module seperately.

# Step by Step deployment for each module

1. Provision EKS cluster 
    follow module terraform-eks-cluster
    (https://learn.hashicorp.com/terraform/kubernetes/provision-eks-cluster)

2. Deploy JAVA App in created Kubernetes cluster
    follow module java-app-deployment

3. Deploy Prometheus 
    follow module kubernetes-prometheus

4. Deploy Alert Manager
    follow module kubernetes-alert-manager

5. Automating secrets
    follow module stretch-goal-secrets


All these steps 1-4 can be automated by Jenkinsfile or shell script 



