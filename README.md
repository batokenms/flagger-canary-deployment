# flagger-canary-deployment

# Apply the Canary Resource

kubectl get canaries --all-namespaces

# Monitor Canary Deployment
# To check the status of the canary deployment, you can use:

kubectl get canaries --all-namespaces

# Flagger will now start shifting traffic from Apache (stable) to Nginx (canary), gradually increasing the percentage of traffic based on your specified metrics.

Flagger uses several key metrics to control the canary deployment and determine whether it should proceed with traffic shifting, halt, or roll back the canary deployment. 

These metrics are usually collected from monitoring tools like Prometheus, and you can define them in the Canary resource.

By default, Flagger tracks these three primary metrics:

# 1. Request Success Rate
   
Metric: request-success-rate

What it measures: The percentage of successful requests handled by the application (canary or stable).

Use: Flagger uses this to determine if the canary is failing or working correctly. A drop below a defined success rate threshold (for example, 99%) triggers a rollback.


