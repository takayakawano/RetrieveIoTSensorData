# Design for IoT scinario with Dynamics 365
This is a sample design for Internet of Things(IoT) scinario with Dynamics 365.
The Internet of things (IoT) is the network of physical devices, vehicles, home appliances and other items embedded with electronics, software, sensors, actuators, and network connectivity which enables these objects to connect and exchange data. This sample is focus onto how to retreive the sensor data.

# what is the benefit of using this sample to you?

- Understand what the best solution for located huge sensor data.
- Understand how to connect to Azure Cosomos DB.
- Evaluate based on this sample design.

# Relational Database(RDB) vs NoSQL

NoSQL is the best solition of huge data as sensor data. 
Azure has NoSQL that name is Azure Cosomos DB.

# Azure Cosomos DB has SLA

Azure Cosomos DB is one of NoSQL. Azure Cosomos DB has huge benefit that is Service Level Agreenent(SLA) for customer.
https://azure.microsoft.com/en-us/support/legal/sla/cosmos-db/v1_1/

# Overview this sample

![capture](https://user-images.githubusercontent.com/19568228/34718842-9f7101ca-f57b-11e7-818f-6072e9dd9359.JPG)

# how to implement this sample

## Azure Cosmos DB
### Create an Azure Cosmos DB Account
1. Login to Azure portal
2. Click to Create a resouece > Azure Cosmos DB >  Create button
3. Select the API to "SQL" in the create screen.
4. Open this Azure Cosmos DB account

### Create sample data
1. Click [Data Explore] menu
2. Create a collection (ex. SampleDB)
3. Create Documents under the SampleDB collection. 

A sample document
{
    "id": "sampledata1_id",
    "status": "Error",
    ...
}

## Implement the Connector of Azure Logic App for Azure Cosmos DB
1. Open following site.
https://github.com/jeffhollan/docdb-connector
2. Click [Deploy to Azure] button
3. Setting a key of your Azure Cosmos DB Account to Settings -> Application Settings in Connector

## Create a traial orgnization of Dynamics 365(CRM) Online 
https://www.microsoft.com/en-us/dynamics/free-crm-trial.aspx

## Azure Logic App
### Create an Azure Logic App
1. Login to Azure portal
2. Create a Logic App
3. Open Logic Apps Designer
4. Add a [HTTP + Swagger] item. then Enter Connector URL (ex. https://docdb-connectorb644.azurewebsites.net/swagger)
5. Click Next, then Select [Query Documents]
6. Enter require culomns your Azure Cosmos DB Account name, Database, Collection.
7. Enter query (ex. SELECT * FROM c WHERE c.status = 'Error')



