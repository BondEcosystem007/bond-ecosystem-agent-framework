TODO list:

- tableau trial (TT) setup
- create a viz on tab server
- test tableau API through postman


- mule: set up vs code
- mule: create mule trial (MT) for anypoint mule cloud 
- mule: figure out how to deploy a hello world API on mule through vscode and into mule cloud
- mule: test mule API through postman


- snf (snowflake): set up snowflake trial (ST) account
- snf: create local DB to ensure things are good
- snf: test API to create table, read table, write table through postman


interop:

- mule: attempt to pull data from TT
- mule: attempt to push data to ST



Multi-agent-framework:

- openai: get a gpt4 token
- agentlite: set up agentlite locally and hook it up with gpt4
- agentlite: do a helloworld test interacting with gpt4
- agentlite: do a helper function test POC, if it works proceed:
- agentlite: write access_mule_api
- agentlite: write access_snf_api : {create table}
- agentlite: write access_tableau_api 
- agentlite: prompts: test access to the various APIs
- agentlite: prompts: create the right schema
- agentlite: prompts: write code which can pull data from tableau
- agentlite: prompts: serving_API: write RAML(1) code (mule) which creates an API to pull data from tableau and display in a certain way
- agentlite: prompts: serving_API: write RAML(2) to fetch data from snowflake and return information
- agentlite: prompts: processing_API: write RAML(3) to pull from tableau , connect with other sources, and drops it into snowflake (for cron)
- agentlite: prompts: write flask API (prior to mule) which can pull from tableau, 



Cron (backend data collection)

airflow will be used to fire the data pipeline jobs (pull data from tableau, ETL, drop in snowflake)

- agentlite: write access_airflow_API.
- agentlite: write python code in airflow which calls mule's processing_API on a 15 min(?) basis: this will fetch 



Enrichment:

- connect employee data with what tableau API is returning to show who exactly is logged in at what time in which dashboard
- may require extract from data on username/title/business unit from data warehouse
