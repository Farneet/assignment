# kubernetes-prometheus
Setting up prometheus monitoring on Kubernetes cluster.

# Create a new namespace in existing cluster 

``` kubectl create namespace monitoring ```

Create a new namespace to keep resources segregated.

# Create Resources for Prometheus

``` kubectl create -f kubernetes-prometheus/ -n monitoring```

    Deploy single file

``` kubectl create -f kubernetes-prometheus/{file_name} -n monitoring```    

Creates all the resources in folder kubernetes-prometheus 
 * `prometheus-clusterRole.yaml`  - To fetch the metrics from Kubernetes API cluster reader permissions should be given to the namspace. Know more about cluster roles (https://kubernetes.io/docs/reference/access-authn-authz/rbac/)
 * `prometheus-configmap.yaml` - To get metrics dynamically from kubernetes resources configurations are done in this config map
    * Prometheus scrape configuration has these scrape jobs.
        * `kubernetes-pods` - Add annotations in pod metadata to get all the pod metrics  automatically ```        prometheus.io/scrape prometheus.io/port ``` 
        * `kubernetes-service-endpoints` - Add annotations in pod metadata to scrape all the service endpoints ```        prometheus.io/scrape prometheus.io/port ``` 
        * `kubernetes-apiservers` `kubernetes-nodes` `kubernetes-cadvisor` - These scrape jobs are also added to get metrics from api-servers, nodes, cadvisor respectively.
    * `prometheus.rules` - Rules to send alerts to the alert manager can be configured as rule
        *    Added rule to send an alert when 10% of the pod memory is consumed.
*    `prometheus-deployment.yaml` - Creates deployment for prometheus
            Check the resources created
            `kubectl get deployment -n monitoring`
            `kubectl get pods -n monitoring`
* `prometheus-service.yaml` - Creates Service for Prometheus
        `kubectl get service -n monitoring`
        Note : Using AWS(or any other cloud provider) for kuberentes hence use `type: Loadbalancer` 