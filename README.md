# flyway-k8-helm-migrations
Helm generating configmaps for k8 init containers running flyway migrations

Requirements

  Database url with user/pass in values.yaml in
  the config map
  Application that connects to your database after flyway init container runs.

  Run 
    cd helm
    kubectl create ns uptime
    HELM_ARGS:        "-f values.${CI_JOB_NAME}.yaml --set image.tag=${CI_PIPELINE_ID}"
    helm template --output-dir 'deploy' '.' -f values.yaml --set image.tag=${YOUR_APP_WITH_DB_IMAGE}
   kubectl apply -f deploy/uptime/templates

 Cleanup
   kubectl delete ns uptime
   kubectl delete deploy/uptime/templates
     
