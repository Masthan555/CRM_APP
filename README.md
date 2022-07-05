Node JS API's for Customer Relationship Management application, Using which Customer can raise a Ticket if he face any issue with the company product, Which is then automatically assigned to available technician. Which also embeds Notification service for letting the user know tracking of the ticket.

# CRM_APP - Customer Relationship Management Application Backend [ Session 1]
## _Learning the development of RESTful APIs for backend development_ 

This code base contains logic/structure  for creating the Restful APIs for the CRM_APP app
## Features
* Setting up project structure and database
* Setting up data models for Ticket item
* API for CRUD operation on Ticket resource-
* Ability to create, read, update and Ticket based on authorization provided.



## How is the code organized in this repo ?
Every code base is tested, So created new repo and merged everything to master branch for.

## Prerequisite
- Understanding of Node.js
- Understanding of Async Await
- Mongo DB locally installed and running
- Understanding Node CRON and Node Mailer API's

## Tech
- Node.js
- Mongodb


## Installation

this app requires [Node.js](https://nodejs.org/) v14+ to run.

Install the dependencies and devDependencies and start the server.

```sh
npm install
npm run devStart
```


## Rest endpoints
#### 1. Create a Ticket 

```sh
POST /crm/api/v1/tickets
Sample request body :
{
        "title": "Reduced Cooling from Fridge",
        "ticketPriority": "4",
        "description": "Cooling from the fridge is reduced, comparing to previously",
}

Sample response body :
{
    "id": "6245ef3fbddfa2ae0d2bba4e",
    "title": "Reduced Cooling from Fridge",
    "description": "Cooling from the fridge is reduced, comparing to previously",
    "ticketPriority": "4",
    "status": "OPEN",
    "reporter": "REP_01",
    "assignee": "ENGINEER_01",
    "createdAt": "2022-03-31T18:13:22.598Z",
    "updatedAt": "2022-03-31T18:13:22.598Z"
}
```


---
#### 2. Get all the tickets

```sh
GET /crm/api/v1/tickets/

Sample response body :
[
    {
        "id": "6245ef3fbddfa2ae0d2bba4e",
        "title": "Reduced Cooling from Fridge",
        "description": "Cooling from the fridge is reduced, comparing to previously",
        "ticketPriority": "4",
        "status": "OPEN",
        "reporter": "REP_01",
        "assignee": "ENGINEER_01",
        "createdAt": "2022-03-31T18:13:22.598Z",
        "updatedAt": "2022-03-31T18:13:22.598Z"
    },
    {
        "id": "6245ef3fbddfa2ae0d2bba4f",
        "title": "Reduced Cooling from AC",
        "description": "Cooling from the AC is reduced, comparing to previously",
        "ticketPriority": "3",
        "status": "CLOSED",
        "reporter": "REP_01",
        "assignee": "ENGINEER_01",
        "createdAt": "2022-03-31T18:13:22.598Z",
        "updatedAt": "2022-03-31T18:13:22.598Z"
    }
]

```
---
#### 3. Get  the tickets based on status
```sh
GET /crm/api/v1/tickets?status=OPEN

Sample response body :
[
    {
        "id": "6245ef3fbddfa2ae0d2bba4e",
        "title": "Reduced Cooling from Fridge",
        "description": "Cooling from the fridge is reduced, comparing to previously",
        "ticketPriority": "4",
        "status": "OPEN",
        "reporter": "REP_01",
        "assignee": "ENGINEER_01",
        "createdAt": "2022-03-31T18:13:22.598Z",
        "updatedAt": "2022-03-31T18:13:22.598Z"
    }
]
```
---
#### 4. Get  the tickets based on ticket id
```sh
GET /crm/api/v1/tickets/6245ef3fbddfa2ae0d2bba4e

Sample response body :
[
    {
        "id": "6245ef3fbddfa2ae0d2bba4e",
        "title": "Reduced Cooling from Fridge",
        "description": "Cooling from the fridge is reduced, comparing to previously",
        "ticketPriority": "4",
        "status": "OPEN",
        "reporter": "REP_01",
        "assignee": "ENGINEER_01",
        "createdAt": "2022-03-31T18:13:22.598Z",
        "updatedAt": "2022-03-31T18:13:22.598Z"
    }
]
```

---
#### 5. Update the tickets based on ticket id
```sh
PUT /crm/api/v1/tickets/6245ef3fbddfa2ae0d2bba50

Sample request body :
{
        "title": "Reduced Cooling from Fridge",
        "status": "CLOSED",
        "ticketPriority": "4",
        "description": "Cooling from the fridge is reduced, comparing to previously",
}
Sample response body :
{
        "id": "6245ef3fbddfa2ae0d2bba4e",
        "title": "Reduced Cooling from Fridge",
        "description": "Cooling from the fridge is reduced, comparing to previously",
        "ticketPriority": "4",
        "status": "CLOSED",
        "reporter": "REP_01",
        "assignee": "ENGINEER_01",
        "createdAt": "2022-03-31T18:13:22.598Z",
        "updatedAt": "2022-03-31T19:13:22.598Z"
    }
```

