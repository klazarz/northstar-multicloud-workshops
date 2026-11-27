# See the service in Azure Monitor

## Introduction

Maya wants an early view of how the service is behaving. Alex suggests recording what Azure Monitor actually reports before drawing conclusions.

Estimated lab time: 20 minutes.

### Objectives

* Select the database as the metric scope and inspect a useful metric.
* Record the observation, time range, aggregation and any gaps.

### Prerequisites

* The assigned database is available and your Azure account can view its metrics.

## Task 1: Open the database metrics

1. In the Azure portal, open **Oracle AI Database@Azure**, select **Oracle Autonomous AI Database**, and open the assigned database.
2. Under **Monitoring**, select **Metrics**. Confirm the scope names the intended database.
3. Select **CPU Utilization** from the metric list and choose **Average** aggregation. Choose a recent time range such as the last hour and a suitable available time granularity. Record the displayed time range, time zone, aggregation, units and any visible value or trend.
4. Add or inspect **Database Availability** if available. Record its definition and any displayed values. Oracle describes 1 as available for connections in the given minute and 0 as unavailable; a missing data point is not the same as 0.

CPU utilization is a percentage relative to the CPUs the database is allowed to use; it is not a count of ECPUs. The [metric reference](https://learn.microsoft.com/en-us/azure/azure-monitor/reference/supported-metrics/oracle-database-autonomousdatabases-metrics) describes metric units and aggregation.

## Task 2: Evaluate what you can conclude

1. Note whether you see data, delayed data, or no data for each metric. If the chart is empty, check the correct resource, time range and permissions with your facilitator. Record the gap rather than treating it as zero or as an outage.
2. Explain one useful observation and one limitation. For example: “The selected period shows CPU utilization values, but this chart alone does not explain a specific user's response time.” Avoid copying private resource identifiers into shared screenshots.

**Checkpoint:** Your notes identify the metric, resource, time range and observation or explicitly document that no data was visible.

You may now **proceed to the next lab**.

## Acknowledgements

* **Author and contributors** - To be confirmed before publication
* **Last reviewed** - November 2026
