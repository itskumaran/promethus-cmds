# promethus-cmds
In Prometheus, you can use the range vector queries to examine metrics over specific intervals. If you want to check metrics at regular intervals over the last hour, you can use the rate() or avg_over_time() functions along with a [1h] range vector to achieve this.

Here’s how you can use these commands with intervals:

1. Rate of a Metric Over the Last Hour
To see the rate of a specific metric (e.g., HTTP requests) at intervals over the last hour:

promql
Copy code
rate(http_requests_total[1h])
This query calculates the per-second rate of increase of http_requests_total over the past hour.

2. Average Value Over the Last Hour
To get the average value of a metric over the last hour:

promql
Copy code
avg_over_time(http_requests_total[1h])
This query calculates the average value of http_requests_total over the past hour.

3. Sum of a Metric Over the Last Hour
To get the total sum of a metric over the last hour:

promql
Copy code
sum_over_time(http_requests_total[1h])
This query sums up the values of http_requests_total over the last hour.

4. Histogram Quantile Over the Last Hour
To get a specific quantile of a histogram over the last hour:

promql
Copy code
histogram_quantile(0.95, sum(rate(http_request_duration_seconds_bucket[1h])) by (le))
This calculates the 95th percentile of HTTP request duration over the past hour.

5. Custom Interval for Aggregation
To customize the interval for aggregation:

promql
Copy code
avg_over_time(http_requests_total[5m])
This calculates the average over 5-minute intervals within the past hour. Adjust [5m] as needed.

Steps to Use These Queries:
Open Prometheus Web UI: Go to http://localhost:9090/graph.

Enter Query: Paste one of the above queries into the "Expression" field.

Set the Time Range: Choose "Last 1 hour" or set a custom time range that includes the last hour.

Run the Query: Click "Execute" to view the results.

These queries will help you analyze the metrics at different intervals over the past hour, giving you insights into trends and performance.
