Node JS API's for Customer Relationship Management application

# CRM_APP - Customer relationship management application backend
## _Learning the development of RESTful APIs for backend development_ 

This code base contains logic/structure for creating the Restful APIs for the CRM_APP app, Using which Customer can raise a Ticket if he face any issue with the company product, Which is then automatically assigned to available technician. Which also embeds Notification service for letting the user know tracking of the ticket.
## Features
* Setting up project structure and database
* Setting up data models for Ticket item
* API for CRUD operation on Ticket resource-
* Ability to create, read, update and Ticket based on authorization provided.

* Setting up data models for User item
* API for CRUD operation on User resource-
* Ability to create, read, update and User based on authorization provided.



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

---
#### 1. USER/ENGINEER/ADMIN SignUp

```sh
POST /crm/api/v1/auth/signup
Sample request body :
{
    "name" : "Akshay",
    "userId" : "AKSH_007",
    "email" : "aksh.007@gmail.com",
    "userType" : "CUSTOMER",
    "password" : "aksh82521",
}

Sample response body :
{
    "name" : "Akshay",
    "userId" : "AKSH_007",
    "email" : "aksh.007@gmail.com",
    "userType" : "CUSTOMER",
    "userStatus" : "APPROVED",
    "password" : "aksh82521",
    "createdAt": "2022-03-31T18:13:22.598Z",
    "updatedAt": "2022-03-31T18:13:22.598Z"
}
```

---
#### 2. USER/ENGINEER/ADMIN Login

```sh
POST /crm/api/v1/auth/signin
Sample request body :
{
    "userId" : "AKSH_007",
    "password" : "aksh82521",
}

Sample response body :
{
    "name" : "Akshay",
    "userId" : "AKSH_007",
    "email" : "aksh.007@gmail.com",
    "userType" : "CUSTOMER",
    "userStatus" : "APPROVED",
    "accessToken" : "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6Im1hc3RoYW4iLCJpYXQiOjE2NTQ3MTI1MjUsImV4cCI6MTY1NDcxNjEyNX0.9nFfFTp82ZEf91l1mjn3rULou8_i4LCeULZr_qulNKM",
}
```

##### Incase of having any issues/doubts in running the API's or understanding the code.
##### Please feel free to contact me : masthan55591@gmail.com