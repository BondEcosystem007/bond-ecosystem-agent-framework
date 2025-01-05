This document identifies some of the most popular paid and open-source dashboards available in the market. It then proceeds to summarize their APIs, focusing on endpoints that return metadata usage.

Here is a list of some of the most popular dashboards:

### Paid Dashboards
1. **Tableau**
2. **Power BI**
3. **Looker**
4. **Qlik Sense**
5. **Domo**

### Open-Source Dashboards
1. **Grafana**
2. **Metabase**
3. **Redash**
4. **Apache Superset**
5. **Kibana**

Next, I will research and summarize the APIs for these dashboards, focusing specifically on endpoints related to metadata usage. This will include an overview of each dashboard’s API capabilities and details on how to retrieve metadata.

### Paid Dashboards

#### 1. Tableau
**API Reference:** [Tableau REST API](https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api.htm)

**Summary:**
- **Metadata API:** The Tableau Metadata API allows users to discover and understand Tableau content and its relationships within and across Tableau Server and Tableau Online.
  - **Endpoints:**
    - `GET /api/metadata/{siteId}/tables`: Retrieves metadata information about tables.
    - `GET /api/metadata/{siteId}/databases`: Retrieves metadata about databases.
    - `GET /api/metadata/{siteId}/workbooks`: Retrieves metadata about workbooks and their relationships.

#### 2. Power BI
**API Reference:** [Power BI REST API](https://docs.microsoft.com/en-us/rest/api/power-bi/)

**Summary:**
- **Metadata API:** The Power BI REST API provides programmatic access to Power BI resources such as dashboards, reports, datasets, and more.
  - **Endpoints:**
    - `GET /v1.0/myorg/reports`: Retrieves metadata about reports in the Power BI service.
    - `GET /v1.0/myorg/datasets`: Retrieves metadata about datasets.
    - `GET /v1.0/myorg/dashboards`: Retrieves metadata about dashboards.

#### 3. Looker
**API Reference:** [Looker API](https://docs.looker.com/reference/api-and-integration)

**Summary:**
- **Metadata API:** The Looker API provides access to Looker data, managing instances, and interacting with Looker content.
  - **Endpoints:**
    - `GET /api/3.1/looks`: Retrieves metadata about looks (pre-built queries).
    - `GET /api/3.1/dashboards`: Retrieves metadata about dashboards.
    - `GET /api/3.1/queries`: Retrieves metadata about queries.

#### 4. Qlik Sense
**API Reference:** [Qlik Sense API](https://qlik.dev/apis/rest)

**Summary:**
- **Engine API:** The Qlik Sense API allows access to app objects, data models, and more.
  - **Endpoints:**
    - `GET /qrs/app/{id}`: Retrieves metadata about a specific app.
    - `GET /qrs/dataconnection`: Retrieves metadata about data connections.
    - `GET /qrs/stream`: Retrieves metadata about streams.

#### 5. Domo
**API Reference:** [Domo API](https://developer.domo.com/docs/domo-apis/data-api-reference)

**Summary:**
- **Metadata API:** The Domo API allows for management and retrieval of Domo resources.
  - **Endpoints:**
    - `GET /v1/datasets`: Retrieves metadata about datasets.
    - `GET /v1/dashboards`: Retrieves metadata about dashboards.
    - `GET /v1/cards`: Retrieves metadata about cards (visualizations).

### Open-Source Dashboards

#### 1. Grafana
**API Reference:** [Grafana HTTP API](https://grafana.com/docs/grafana/latest/http_api/)

**Summary:**
- **Metadata API:** Grafana's HTTP API allows for managing Grafana resources such as dashboards, data sources, and more.
  - **Endpoints:**
    - `GET /api/dashboards/db/:slug`: Retrieves metadata about a specific dashboard.
    - `GET /api/datasources`: Retrieves metadata about data sources.
    - `GET /api/search`: Searches and retrieves metadata about various Grafana objects.

#### 2. Metabase
**API Reference:** [Metabase API](https://www.metabase.com/docs/latest/api-documentation.html)

**Summary:**
- **Metadata API:** Metabase API provides access to manage Metabase resources such as questions, dashboards, and collections.
  - **Endpoints:**
    - `GET /api/dashboard`: Retrieves metadata about dashboards.
    - `GET /api/card`: Retrieves metadata about questions (cards).
    - `GET /api/collection`: Retrieves metadata about collections.

#### 3. Redash
**API Reference:** [Redash API](https://redash.io/help/user-guide/integrations-and-api/api)

**Summary:**
- **Metadata API:** The Redash API allows access to manage queries, dashboards, and other Redash resources.
  - **Endpoints:**
    - `GET /api/dashboards`: Retrieves metadata about dashboards.
    - `GET /api/queries`: Retrieves metadata about queries.
    - `GET /api/destinations`: Retrieves metadata about alert destinations.

#### 4. Apache Superset
**API Reference:** [Apache Superset API](https://superset.apache.org/docs/rest-api)

**Summary:**
- **Metadata API:** Superset's REST API allows for the management and retrieval of various Superset resources.
  - **Endpoints:**
    - `GET /api/v1/dashboard`: Retrieves metadata about dashboards.
    - `GET /api/v1/chart`: Retrieves metadata about charts.
    - `GET /api/v1/dataset`: Retrieves metadata about datasets.

#### 5. Kibana
**API Reference:** [Kibana API](https://www.elastic.co/guide/en/kibana/current/api.html)

**Summary:**
- **Metadata API:** Kibana API provides access to manage Kibana resources and retrieve metadata.
  - **Endpoints:**
    - `GET /api/saved_objects/_find`: Retrieves metadata about saved objects such as dashboards, visualizations, and index patterns.
    - `GET /api/saved_objects/dashboard/{id}`: Retrieves metadata about a specific dashboard.
    - `GET /api/saved_objects/visualization/{id}`: Retrieves metadata about a specific visualization.

With this list and initial summary, we can now proceed to provide detailed summaries for each dashboard's metadata API endpoints. Please let me know if you would like to start with a specific dashboard or need more information on a particular one.
