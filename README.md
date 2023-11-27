# Splunk-1
Notes on Splunk


Splunk is basically a **data  visualization and analyzation tool!**

Why we need it in an organization there are lot of data’s been collected like metrics logs etc, these are need to be analyzed so that we can know where we can improve  and it helps us to make important decisions, so slunk helps to analyze and visualize the data from the data sources!

What means visualization in terms of this context is like creating dashboards!

Major uses of Splunk

To monitor the system performance

Monitor system health(CPU, Disk etc)

To improve the quality

How does Splunk work?

So firstly we have to understand how splunk architecture and components work, because Splunk is not just a single tool it’s set of component’s!

Splunk architecture- Splunk has two types of environments single server environment and Distributed environment

-In organizations mostly we use distributed server environment

Single server environment

It is mainly used for Testing purpose, which means for the data indexing

In this context data indexing means storing the data, simply  testing the a **big architecture** we use single server environment.

Distributed server environment 

It is basically used to do a specific tasks in multiple servers

How does distributed server environment works?

In the distributed environments there are different servers for specific Splunk components.

Scaling can be performed in different ways based on need.

What is splunk components in this context?

So basically splunk components has two major components one is **Processing components** the other is **Management components**

What does Processing component would do is basically it will **handle the data,**

It has **Forwarders** to collect the data (Forwarders attach themselves to the data)

It has **Indexers** - Indexers stores the data

and it has **Search heads**- we can search the dashboards data or Visualization or report etc

 So search heads used by users, search heads collects the data which is stored in Indexers and gets data from Forwarders, this is how it works!

Management component basically manages multiple components (If we have a big cluster we need more forwarders we need more Indexers and search heads), it has Deployment server

Deployment server  is responsible for **handling multiple forwarders** 

It has **Indexer cluster master node** which manages multiple indexers

It has **Search head cluster developer** which manages multiple Search heads

It has **License master**- we need licensed master to manage the threshold limit of the components 

It has **Monitoring Console**, which is used to to monitor processing component and Management component 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d9415a84-09a3-4d14-8c00-0e59c218f6f0/Untitled.png)

Splunk Data Flow

How does the Data flow to each of these components?

So it has **Splunk Data Pipeline** 

Splunk Data Pipeline has a Input which consists of

Monitor Input
FIFO Input
UDP Input

TCP Input

Then the does goes to the **Parsing pipeline**- Parsing pipeline defines the fields and all, then it will goes to the next part which is **Indexing pipeline** where every data will be stored!

Data flow in the Splunk

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d172496c-fa4b-4a47-b015-6281d2a8dad7/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69317a0f-d0e8-4f94-afbc-ee1d0c3eaab6/Untitled.png)

Splunk flow explanation:

The data from the servers will flow through the multiple forwarders; forwarders collects the data from the servers and then ship it to one forwarder, next Indexer will store the data which is collected and helps to monitor and visualize the data or we have **Search heads** which is used to **visualize the data and analyze the data**, so the information will be shown in the dashboards!

If anything goes wrong we get notified to the Slack.

Splunk Licensing-

Every components have a License; Based upon the license we have limit to use the Indexers;

There are different types of licenses, to manage all the licenses we need Master License!

 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df8dc8a1-6760-499c-802b-5bf6fa92fcbc/Untitled.png)

• **Splunk Search Processing Language.**

SPL

SPL is for finding all the indexes in the splunk

**SPL to find all the index's in the Splunk:**

Splunk has two types of indexers

One is internet indexer which start with underscore_

Other one is external indexer which are defined by the users

index=app status>399 | top limit=3 status showperc=f

showperc=f or showcount=f is for hiding a column

Response

top response_time

limit=0 shows all the data

**limit=0** will give all the data in the **particular index**.

For suppose if you wanted only top 3 values

the just limit=3 response_time

Let’s say client is asking to find the least sold product id

then we have to use rare command

index=app | rare productId

Lets say you wanted to give this proud a meaningful name use command called replace 

replace prouctId

How to work on fields if there is no data

table command

index=app |table method, action

chart function will helps to display the events

SO chart is to display the events

Transaction function

SMTP server

REGIX QUERY'S

Splunk with Regex

Regex is nothing but a regular expressions

With the help os Regex we can extract the error codes, Urls’s, and the ip addresses

(Advanced queries we use this regex)

Regex regularly used for pattern matching or string matching

Splunk integration with the Spring boot

-For the integration for these two different servers we need a file called log4j-spring.xml

- In the file we make the customizations
- We are using log4j for the logging which is a 3rd party logging device for the spring boot application
- So first of all we need a splunk-url
- then Host (jump server), where the splunk server is running
- Token to make the connection between these two servers
- Index to push the application logs
- And finally the source
