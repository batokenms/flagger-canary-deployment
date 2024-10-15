# flagger-canary-deployment

# Apply the Canary Resource

kubectl get canaries --all-namespaces

# Monitor Canary Deployment
# To check the status of the canary deployment, you can use:

kubectl get canaries --all-namespaces

# Flagger will now start shifting traffic from Apache (stable) to Nginx (canary), gradually increasing the percentage of traffic based on your specified metrics.


