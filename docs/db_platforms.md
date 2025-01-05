Here is a list of popular paid and open-source online relational databases. I will provide summaries of the APIs they expose, focusing on APIs that can allow LLMs using helper functions to configure, read, and write to these platforms with minimal user interaction.

### Paid Online Relational Databases

#### 1. **Amazon RDS**
**API Reference:** [Amazon RDS API](https://docs.aws.amazon.com/AmazonRDS/latest/APIReference/Welcome.html)

**Summary:**
- **Exposed APIs:**
  - `CreateDBInstance`: Creates a new DB instance.
  - `DescribeDBInstances`: Lists existing DB instances.
  - `ModifyDBInstance`: Modifies an existing DB instance.
  - `DeleteDBInstance`: Deletes a DB instance.

#### 2. **Google Cloud SQL**
**API Reference:** [Google Cloud SQL API](https://cloud.google.com/sql/docs/mysql/admin-api)

**Summary:**
- **Exposed APIs:**
  - `POST /projects/{project}/instances`: Creates a new SQL instance.
  - `GET /projects/{project}/instances`: Lists SQL instances.
  - `PATCH /projects/{project}/instances/{instance}`: Updates an existing SQL instance.
  - `DELETE /projects/{project}/instances/{instance}`: Deletes a SQL instance.

#### 3. **Microsoft Azure SQL Database**
**API Reference:** [Azure SQL Database REST API](https://docs.microsoft.com/en-us/rest/api/sql/)

**Summary:**
- **Exposed APIs:**
  - `PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}`: Creates or updates a database.
  - `GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases`: Lists databases.
  - `PATCH /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}`: Updates an existing database.
  - `DELETE /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Sql/servers/{serverName}/databases/{databaseName}`: Deletes a database.

#### 4. **Snowflake**
**API Reference:** [Snowflake Documentation](https://docs.snowflake.com/en/developer-guide/udf/python/udf-python-introduction.html)

**Summary:**
- **Exposed APIs:**
  - `POST /v1/data/warehouse/{account}/queries`: Execute SQL queries.
  - `GET /v1/data/warehouse/{account}/databases`: List databases.
  - `POST /v1/data/warehouse/{account}/databases`: Create a new database.
  - `DELETE /v1/data/warehouse/{account}/databases/{databaseName}`: Delete a database.

### Open-Source Online Relational Databases

#### 1. **PostgreSQL (via various managed services)**
**API Reference:** [PostgreSQL Documentation](https://www.postgresql.org/docs/)

**Summary:**
- **Exposed APIs:** PostgreSQL itself does not expose APIs, but managed services like Amazon RDS for PostgreSQL, Google Cloud SQL for PostgreSQL, and Azure Database for PostgreSQL provide API interfaces.

#### 2. **MySQL (via various managed services)**
**API Reference:** [MySQL Documentation](https://dev.mysql.com/doc/)

**Summary:**
- **Exposed APIs:** Similar to PostgreSQL, MySQL itself does not expose APIs, but managed services like Amazon RDS for MySQL, Google Cloud SQL for MySQL, and Azure Database for MySQL provide API interfaces.

#### 3. **MariaDB (via various managed services)**
**API Reference:** [MariaDB Documentation](https://mariadb.com/kb/en/mariadb-documentation/)

**Summary:**
- **Exposed APIs:** Managed services for MariaDB provide API interfaces similar to those for MySQL.

#### 4. **SQLite**
**API Reference:** [SQLite Documentation](https://www.sqlite.org/docs.html)

**Summary:**
- **Exposed APIs:** SQLite is a serverless database and does not provide APIs for remote management. It is designed for local use within applications.

#### 5. **CockroachDB**
**API Reference:** [CockroachDB API](https://www.cockroachlabs.com/docs/v20.2/admin-ui-api.html)

**Summary:**
- **Exposed APIs:**
  - `POST /v2/sql`: Execute SQL queries.
  - `GET /v2/databases`: List databases.
  - `POST /v2/databases`: Create a new database.
  - `DELETE /v2/databases/{databaseName}`: Delete a database.

### Example of Helper Functions for LLMs

Let's illustrate how helper functions might look for configuring, reading, and writing to these platforms with minimal user interaction. We'll use Amazon RDS as an example.

#### Example: Amazon RDS Helper Functions

```javascript
const AWS = require('aws-sdk');
const rds = new AWS.RDS();

// Helper function to create a new DB instance
function createDBInstance(params) {
    return rds.createDBInstance(params).promise();
}

// Helper function to list DB instances
function listDBInstances() {
    return rds.describeDBInstances().promise();
}

// Helper function to modify a DB instance
function modifyDBInstance(params) {
    return rds.modifyDBInstance(params).promise();
}

// Helper function to delete a DB instance
function deleteDBInstance(params) {
    return rds.deleteDBInstance(params).promise();
}

// Example usage of helper functions
const params = {
    DBInstanceIdentifier: 'mydbinstance',
    AllocatedStorage: 20,
    DBInstanceClass: 'db.t2.micro',
    Engine: 'mysql',
    MasterUsername: 'admin',
    MasterUserPassword: 'password'
};

createDBInstance(params)
    .then(data => console.log(data))
    .catch(err => console.error(err));

listDBInstances()
    .then(data => console.log(data))
    .catch(err => console.error(err));
```

This example shows how an LLM could use helper functions to configure, read, and write to Amazon RDS with minimal user interaction. Similar helper functions can be created for other platforms and frameworks to achieve the same level of automation.
