# Control API development

First, we'll just build control APIs manually so we have something to compare against what the coder LLMs will build and then judge the results.



I started with the tableau API
https://help.tableau.com/current/api/rest_api/en-us/REST/rest_api.htm

it walks through tutorials and get access to systems. meh dont have time to read academically, so let's just get the environment first.

built it in mule-tableau-api-testing.ipynb

see images/01*


### Mule control API:


## First, we build an integration


#### First a test API which fronts another API

to learn how to consume a downstream API, I used this tutorial 
https://docs.mulesoft.com/mule-runtime/latest/rest-api-examples#:~:text=To%20consume%20the%20REST%20API,or%20set%20up%20an%20account.

it consumes baconipsum.com:80/api

see images/07-14


## Next, we build an API spec for what our Dashboard Engagement API

For Mule, first we write an API spec on anypoint.mulesoft.com under our account:

https://developer.mulesoft.com/tutorials-and-howtos/getting-started/build-api-specification-api-designer/

i used the above to create an api spec for two URIs (resources) and publish them on exchange

/dashboard-list
/realtime-usage-summary

see images/02.., and 03..



### Next, we pull this API from anypoint.mulesoft.com into our local IDE


this is done to fleshout the API spec (which is just a skeleton)

I used these instructions:

https://developer.mulesoft.com/tutorials-and-howtos/quick-start/developing-your-first-mule-application/

I followed most of the steps until "connect to a database", as I was going to connect to a tableau API first. (we'll come back to the connect to database as we also need to connect to snowflake)

up until now, we have pulled in the api spec into the IDE
see images/04, 05, 06



### Next, we flesh out our two endpoints with actual API calls..




-- other thoughts

having to stop thinking and imputing ourselves on genAI, we can have it work with long context windows (quote Dwarkesh Patel's blog with Stalto, and Trenton) and forget about things versus fine tune it and make it remember everything