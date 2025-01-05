## API Specification:

This is a generic API specification of a green field application designed by a custom model in chatGPT (likely finetuned on top of GPT4)

Here are all the endpoints specified in this API spec based on MoSCoW prioritization

- Must Have
- Should Have
- Could Have
- Would Like to Have

### Must Have

**1. List All Tableau Dashboards**
- **URI**: `/dashboard_list/`
- **Description**: Retrieves a list of all Tableau dashboards along with their unique IDs.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/dashboard_list/" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboards": [
      {"name": "SalesDashboard", "id": "101"},
      {"name": "MarketingDashboard", "id": "102"}
    ]
  }
  ```

**2. Get Dashboard by Name**
- **URI**: `/dashboard_list/{dashboard_name}`
- **Description**: Fetches the unique ID associated with a specified dashboard name.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/dashboard_list/SalesDashboard" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboard": {"name": "SalesDashboard", "id": "101"}
  }
  ```

**3. Get User Details by Username**
- **URI**: `/user_details/{user_name}`
- **Description**: Returns the workday user ID associated with a specified username.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/user_details/jdoe" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "user": {"username": "jdoe", "workdayId": "WD123"}
  }
  ```

**4. Get Current User Count on a Dashboard**
- **URI**: `/realtime_usage_summary/user_count/{tableau_dashboard_unique_id}`
- **Description**: Provides the current number of unique users accessing a specific Tableau dashboard.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/realtime_usage_summary/user_count/12345" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "12345",
    "currentUserCount": 15
  }
  ```

**5. List Active Users on a Dashboard (Version 1)**
- **URI**: `/realtime_usage_details/v1/{tableau_dashboard_unique_id}`
- **Description**: Lists each user currently active on a specified dashboard along with available metadata.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/realtime_usage_details/v1/12345" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "12345",
    "users": [
      {"username": "jdoe", "sessionStart": "2024-05-10T12:00:00Z"},
      {"username": "asmith", "sessionStart": "2024-05-10T12:05:00Z"}
    ]
  }
  ```



**6. List Active Users on a Dashboard (Version 2)**
- **URI**: `/realtime_usage_details/v2/{tableau_dashboard_unique_id}`
- **Description**: Provides the same data as Version 1 but also includes the title of each user and their L5 manager name.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/realtime_usage_details/v2/12345" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "12345",
    "users": [
      {"username": "jdoe", "title": "Sales Manager", "L5Manager": "Jane Doe", "sessionStart": "2024-05-10T12:00:00Z"},
      {"username": "asmith", "title": "Marketing Director", "L5Manager": "John Smith", "sessionStart": "2024-05-10T12:05:00Z"}
    ]
  }
  ```



### Should Have

**7. Engagement Metadata Over a Time Duration**
- **URI**: `/time_duration_usage_summary`
- **Description**: Provides engagement metadata for Tableau dashboards over a specified time duration.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/time_duration_usage_summary?start_time=2024-05-10T00:00:00Z&end_time=2024-05-12T23:59:59Z" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "summary": [
      {"dashboardId": "101", "totalSessions": 50, "totalDurationHours": 120},
      {"dashboardId": "102", "totalSessions": 30, "totalDurationHours": 80}
    ]
  }
  ```

**8. List Active Users on a Dashboard with Additional Metadata (Version 2)**
- **URI**: `/realtime_usage_details/v2/{tableau_dashboard_unique_id}`
- **Description**: Provides the same data as Version 1 but also includes additional metadata such as user's title and their L5 manager name. Utilizes persistent storage to maintain user details for efficient retrieval.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/realtime_usage_details/v2/12345" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "12345",
    "users": [
      {"username": "jdoe", "title": "Sales Manager", "L5Manager": "Jane Doe", "sessionStart": "2024-05-10T12:00:00Z"},
      {"username": "asmith", "title": "Marketing Director", "L5Manager": "John Smith", "sessionStart": "2024-05-10T12:05:00Z"}
    ]
  }
  ```
- **Persistent Storage**: User titles and L5 manager names are stored in Snowflake. This data is joined with real-time session data pulled from Tableau to provide enriched user profiles in the response.


### Could Have


**9. Change Impact Assessment**
- **URI**: `/change_impact_assessment/{dashboard_id}`
- **Description**: Analyzes potential impact on user engagement from upcoming changes to a specified dashboard.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/change_impact_assessment/101" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "101",
    "estimatedImpact": "High",
    "affectedUserCount": 150,
    "criticalMetricsAffected": ["Response Time", "User Load"]
  }
  ```

**10. Dashboard Criticality Assessment**
- **URI**: `/dashboard_criticality/`
- **Description**: Returns a list of dashboards ordered by their criticality based on usage metrics and impact assessments.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/dashboard_criticality/" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboards": [
      {"id": "101", "name": "SalesDashboard", "criticalityLevel": "High"},
      {"id": "102", "name": "MarketingDashboard", "criticalityLevel": "Medium"}
    ]
  }
  ```

**11. Outage Impact Analysis**
- **URI**: `/outage_impact_analysis/{dashboard_id}`
- **Description**: Provides insights into user activity before, during, and after an outage to assess the impact on a specific dashboard.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/outage_impact_analysis/102" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "102",
    "preOutageUserCount": 40,
    "duringOutageUserCount": 5,
    "postOutageRecoveryTime": "2 hours"
  }
  ```


### Would Like to Have

**12. Data Lineage**
- **URI**: `/data_lineage/{dashboard_id}`
- **Description**: Traces the data sources and transformations used within a specific dashboard.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/data_lineage/101" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "101",
    "dataSources": [
      {"sourceId": "db1", "sourceName": "SalesDB", "usageFrequency": "High"},
      {"sourceId": "db2", "sourceName": "MarketingDB", "usageFrequency": "Medium"}
    ],
    "transformations": [
      {"transformationId": "t1", "description": "Aggregate sales by region"}
    ]
  }
  ```

**13. Most Active Users**
- **URI**: `/most_active_users/{dashboard_id}`
- **Description**: Lists the top active users for a specific dashboard, including usage frequency and duration.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/most_active_users/102" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "102",
    "users": [
      {"username": "asmith", "sessionCount": 40, "averageDuration": "30 minutes"},
      {"username": "jdoe", "sessionCount": 35, "averageDuration": "45 minutes"}
    ]
  }
  ```

**14. Session Duration Statistics**
- **URI**: `/session_duration_statistics/{dashboard_id}`
- **Description**: Aggregates session duration statistics such as average, median, and mode session times to understand user engagement depth.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/session_duration_statistics/103" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "103",
    "averageDuration": "25 minutes",
    "medianDuration": "20 minutes",
    "modeDuration": "15 minutes"
  }
  ```


**15. Dashboard Usage Trends**
- **URI**: `/dashboard_usage_trends/{time_period}`
- **Description**: Provides trends in dashboard usage over specified time periods (daily, weekly, monthly).
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/dashboard_usage_trends/monthly" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "trends": [
      {"dashboardId": "101", "usageCount": 120, "timePeriod": "April"},
      {"dashboardId": "102", "usageCount": 90, "timePeriod": "April"}
    ]
  }
  ```

**16. User Segmentation**
- **URI**: `/user_segmentation/{dashboard_id}`
- **Description**: Segments users based on usage patterns and interactions with a dashboard.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/user_segmentation/104" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "dashboardId": "104",
    "segments": [
      {"segmentName": "Heavy Users", "users": ["jdoe", "asmith"]},
      {"segmentName": "Occasional Users", "users": ["mjones", "cperry"]}
    ]
  }
  ```

**17. Detailed Time Duration Usage**
- **URI**: `/time_duration_usage_details`
- **Description**: Lists detailed user sessions and interactions within a specified time frame.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/time_duration_usage_details?start_time=2024-05-10T00:00:00Z&end_time=2024-05-12T23:59:59Z" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "details": [
      {"dashboardId": "101", "username": "jdoe", "sessionStart": "2024-05-10T12:00:00Z", "duration": "30 minutes"},
      {"dashboardId": "102", "username": "asmith", "sessionStart": "2024-05-10T12:30:00Z", "duration": "45 minutes"}
    ]
  }
  ```

**18. User Usage Details for Specific Time Duration**
- **URI**: `/user_usage_details_for_time_duration`
- **Description**: Retrieves detailed usage information for a given user over a specified period.
- **Example Call**:
  ```bash
  curl -X GET "http://api.example.com/user_usage_details_for_time_duration?user=WD123&start_time=2024-05-10T00:00:00Z&end_time=2024-05-12T23:59:59Z" -H "Authorization: Bearer {access_token}"
  ```
- **Example Response**:
  ```json
  {
    "usageDetails": [
      {"dashboardId": "101", "dashboardName": "SalesDashboard", "sessionStart": "2024-05-10T12:00:00Z", "duration": "30 minutes", "title": "Sales Manager", "L5Leader": "Jane Doe"}
    ]
  }
  ```




## Authentication Methodology
- For authentication, we will use OAuth 2.0 with access tokens. This method ensures secure access to the API by requiring each request to include a valid access token obtained through the authentication provider.

- **Authentication Example**:
  ```bash
  curl -X POST "http://auth.example.com/oauth/token" -d "grant_type=client_credentials&client_id={client_id}&client_secret={client_secret}"
  ```
  This POST request returns an access token which is then used in the Authorization header for subsequent API requests.