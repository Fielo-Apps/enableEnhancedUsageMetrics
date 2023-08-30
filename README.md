# Enable Enhanced Usage Metrics

Click on the following button to deploy the repository to any org. Salesforce Login is required

<a href="https://githubsfdeploy.herokuapp.com?owner=Fielo-Apps&repo=enableEnhancedUsageMetrics&ref=master">
  <img alt="Deploy to Salesforce"
       src="https://raw.githubusercontent.com/afawcett/githubsfdeploy/master/deploy.png">
</a>

# Using Enhanced Usage Metric Salesforce

> **IMPORTANT**: The schema changes can take some time to activated. <br>
> **IMPORTANT 2**: As of now (2023-08-25) Salesforce Inspector does not support the new Fields of the `PlatformEventUsageMetric` object. The query must be executed in the Salesforce Developer Console.

In the developer console, run the query:
```SQL
SELECT EventName, Client, Value, StartDate, EndDate
FROM PlatformEventUsageMetric
WHERE TimeSegment='Daily' AND UsageType='PUBLISH' AND StartDate >= LAST_N_DAYS:1 AND EndDate <= TODAY
```

Check the results:
![EventsUsage](https://raw.githubusercontent.com/tibeal/images/master/image-4.png)