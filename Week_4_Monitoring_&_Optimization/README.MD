# Monitoring & Optimization

## 1. Monitoring on AWS


Monitoring is like having a security camera for your application. Just as a camera helps you see what's happening in a store, monitoring tools help you keep an eye on how your application is performing. For example, if users are experiencing slow page loads, you want to know about it before they do. This way, you can fix the problem quickly and keep your users happy. Monitoring collects important information, like how much memory your application is using or how many people are connected to your database, so you can spot issues before they become big problems.

Imagine you're a chef in a busy restaurant. You want to know if the oven is too hot or if the ingredients are running low before the customers complain. Monitoring your application works the same way; it helps you check the "temperature" of your system and make adjustments as needed.

<p align="center">
    <img src="images/metrics.png" width="700px">
</p>


**Monitoring Definition:**
The process of collecting, analyzing, and using data to assess the operational health and usage of IT resources.

**Importance of Monitoring:**
* Provides real-time insights into system performance.
* Helps identify operational issues before they affect users.
* Improves resource performance and reliability.
* Recognizes security threats by establishing a baseline of normal activity.
* Supports data-driven business decisions.
* Enables cost optimization by identifying underutilized resources.


**Metrics:** Data points collected from resources (e.g., CPU utilization, network performance) that help evaluate system health.

**Types of Metrics:** Different AWS resources generate different metrics (e.g., EC2 instances vs. S3 buckets).

**Amazon CloudWatch:** A service that centralizes monitoring data, allowing users to visualize metrics, set alarms, and automate responses to performance changes.



## Amazon CloudWatch

**Overview:** CloudWatch is a managed service that allows you to monitor AWS resources without managing infrastructure. It centralizes metrics from various AWS services.

**Metrics:** Different AWS resources send metrics to CloudWatch automatically, providing basic monitoring for free. Detailed monitoring is available for a fee, allowing metrics to be posted every minute.

**Custom Metrics:** You can create custom metrics for application-specific data, such as page views or error rates, using the PutMetricData API.

**Dashboards:** CloudWatch dashboards allow you to visualize metrics through customizable widgets. You can aggregate data from different regions and control access through IAM policies.

**Logs:** CloudWatch Logs stores and analyzes log files from various sources. You can query logs and set up metric filters to convert log data into metrics.

**Alarms:** You can create alarms to trigger actions based on metric thresholds. Alarms can notify you or initiate automated responses to issues.