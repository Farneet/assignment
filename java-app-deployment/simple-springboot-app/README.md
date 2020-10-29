# Deploy Java application in Kubernetes cluster


# Ready for Deployment

Build the Docker Image 

```docker build -t simple-springboot --build-arg VERSION=0.0.1-SNAPSHOT . ```

# Tag & Push the Image to Docker Registry

```
docker tag simple-springboot-app farneet/simple-springboot-app
docker push farneet/simple-springboot-app

```
# Create deployment template

Install helm (https://helm.sh/docs/intro/install/)

``` helm create simple-springboot-app ```

Make changes in templates/deployment.yaml to add env variables relevent to application & Add the details in values.yaml
Annotations in values.yaml to enable prometheus pod metrics for pod metadata in templates/deployment.yaml

``` podAnnotations: 
        prometheus.io/port: '8080'
        prometheus.io/scrape: 'true' 
        
``` 
App related environment variables set in deployment.yaml

``` env:
            - name: JAVA_OPTS
              value: {{ .Values.javaOpts }}
            - name: LOG_LEVEL
              value: {{ .Values.logLevel }}
```

Add annotations for Prometheus in templates/service.yaml for prometheus

```annotations:
    prometheus.io/port: 8080
    prometheus.io/scrape: "true"
```
    


# Deployment

Deploy to production using Jenkinsfile 

Manual Deployment

``` helm template simple-springboot-app -f simple-springboot-app/values.yaml > production_deploy.yaml ```

``` kubectl apply -f production_deploy.yaml -n backend```









