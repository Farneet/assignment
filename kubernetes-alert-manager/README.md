# kubernetes-alert-manager
Setting up alert-manager on Kubernetes cluster.

# Get namespace in existing cluster 

``` kubectl get namespace ```

`monitoring` Namespace already exists . 

Create a new namespace to keep resources segregated.

# Create Resources for alert-manager

``` kubectl create -f kubernetes-alert-manager/ -n monitoring```

# Deploy single file
    
``` kubectl create -f kubernetes-alert-manager/{file_name} -n monitoring```    

Creates all the resources in folder kubernetes-alert-manager 

 * `alertManager-configmap.yaml` - configmap for configuration of alert template path, email and other alert receiving configurations. In this setup, we are using email reciever. check all other supported recievers here (https://prometheus.io/docs/alerting/latest/configuration/#%3Creceiver%3E)
    * Recievers
        * `email_config` - configure alerts to email
        * `webhook_config` - configuration for alerts to webhook url

 * `alertTemplate-configmap.yaml`  - configMap to dynamically substitute the values and delivers alerts to the reciever based on template.

*   `alertmanager-deployment.yaml` - Creates deployment for alert manager
            Check the resources created
            `kubectl get deployment -n monitoring`
            `kubectl get pods -n monitoring`
*   `alertmanager-deployment-service.yaml` - Creates service for alert manager
        `kubectl get service -n monitoring`
        Note : Using AWS(or any other cloud provider) for kuberentes hence use `type: Loadbalancer` 
        

                
                  







