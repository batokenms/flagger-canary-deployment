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

# Traffic Increase Logic
stepWeight: 10: This means that 10% of the traffic will be shifted from the stable version (Apache) to the canary version (Nginx) in each step.

interval: 1m: The traffic will shift every 1 minute. This means that Flagger will evaluate the health of the canary version every minute and increase the traffic by 10% if all the defined metrics (such as success rate and latency) are within acceptable thresholds.

# Example of Traffic Shifting Over Time:

Start: Initially, 0% of the traffic is sent to the canary (Nginx), and 100% goes to the stable version (Apache).
After 1 minute: If the canary passes the health checks (e.g., success rate > 99%, latency < 500ms), Flagger will shift 10% of the traffic to the canary.
After 2 minutes: If the canary continues to perform well, Flagger will increase the traffic to 20%.
After 3 minutes: If the canary is still healthy, traffic increases to 30%, and so on.
