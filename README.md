# flyway-k8-helm-migrations


Helm generating configmaps for k8 init containers running flyway migrations pattern.

This chart uses a config map templating feature to convert migrations/*.sql files into a configmap vol into an init container before your app runs.

## Requirements:

 - Database url with user/pass in values.yaml for the config map.
  
 - Application that connects to your database after flyway init container runs.
 
 - Migrations directory with *.sql files to the root of the helm chart.
 


## Run: 
  
    cd helm
    
    kubectl create ns uptime
    
    helm template --output-dir 'deploy' '.' -f values.yaml --set image.tag=${YOUR_APP_WITH_DB_IMAGE}
    
    kubectl apply -f deploy/uptime/templates

## Cleanup:
    
    kubectl delete ns uptime
    
    kubectl delete -f deploy/uptime/templates
     
