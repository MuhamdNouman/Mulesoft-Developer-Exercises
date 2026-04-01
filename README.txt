# MuleSoft Developer Exercises

This repository contains a collection of MuleSoft exercises designed to practice core Mule 4 concepts, integration patterns, and API development.

---

# Exercise 01

## Title

MuleSoft Fundamentals: HTTP Listener, Set Variables, Loggers, Flows, and Subflows

## Overview

Build a mini Mule project demonstrating fundamental MuleSoft concepts.

### Objectives

* Use an **HTTP Listener** to call a flow through Postman or a browser.
* Store and retrieve values using **Set Variable**.
* Print values using **Logger**.
* Create reusable **Subflows** using **Flow Reference**.
* Share variables between flows and subflows.

---

# Exercise 02

## Title

MuleSoft Components: Query and Create/Insert Connector of Salesforce and Database
*(Condition: Without Using Set Variables)*

## Overview

Create a MuleSoft project that calls Salesforce and Database connectors while storing responses directly using **Target Variable** (without using Set Variable components).

### Tasks

* Salesforce **Query Connector**
* Salesforce **Create Connector**
* Database **Select Connector**
* Database **Insert Connector**

All responses must be stored using **Target Variable**.

---

# Exercise 03

## Title

Mule Project: Salesforce Create, Update, Upsert, Query, and Delete Connectors
*(Requests received from Postman)*

## Overview

Build a Mule project demonstrating CRUD operations using Salesforce connectors.

### Implement

* Create record using **Salesforce Create Connector**
* Update record using **Salesforce Update Connector**
* Upsert record using **Salesforce Upsert Connector**
* Delete record using **Salesforce Delete Connector**
* Query records using **Salesforce Query Connector**

---

# Exercise 04

## Title

Mule Project: Database Insert, Update, Query, Delete Connectors
*(Requests received from Postman)*

## Overview

Build a Mule project demonstrating database CRUD operations.

### Implement

* Insert record using **Database Insert Connector**
* Update record using **Database Update Connector**
* Delete record using **Database Delete Connector**
* Query records using **Database Query Connector**

---

# Exercise 05

## Title

Understanding Error Handling in MuleSoft
(On Error Propagate vs On Error Continue vs Raise Error)

## Overview

Create a Mule project demonstrating different error-handling strategies.

### Concepts

**On Error Propagate**

* Stops flow execution.
* Sends the error back to the caller.

**On Error Continue**

* Handles the error internally.
* Allows the flow to continue processing.

**Raise Error**

* Used to intentionally generate an error.
* Helps test error-handling mechanisms.

---

# Exercise 06

## Title

Building Two Connected MuleSoft APIs and Understanding Payload & Attributes Changes

## Objective

Understand how APIs communicate and how payload, attributes, and variables change during execution.

## Overview

### API-1

* Receives request from **Postman**
* Calls **API-2 internally**
* Sends final response back to the client

### API-2

* Processes or retrieves data
* Returns response to API-1

### Key Requirement

Log and analyze:

* Payload changes
* Attribute changes
* Variable updates

after API-1 receives the response from API-2.

---

# Exercise 07

## Title

Building a MuleSoft API that Uses Object Store

## Objective

Understand how to use **MuleSoft Object Store**.

## Overview

Design a MuleSoft API with endpoints to store, retrieve, and remove data.

### Endpoints

POST /store
Save a key-value pair into Object Store.

GET /retrieve/{key}
Retrieve a stored value using a key.

DELETE /remove/{key}
Remove a key-value pair from Object Store.

### Testing

Use **Postman** to test the endpoints.

### Use Cases

Object Store can be used for:

* Caching
* Temporary data storage
* Session management

---

# Exercise 08

## Title

Build a MuleSoft API with OAuth 2.0 to Connect to an External System

## Objective

Create a MuleSoft API that securely accesses external systems using OAuth 2.0.

## Overview

The API will:

* Obtain an **Access Token**
* Use the token to access a protected resource

### Configuration

* Client ID
* Client Secret
* Authorization URL
* Token URL

### Implementation

* Use **HTTP Request Connector**
* Authenticate using **OAuth 2.0**
* Expose an endpoint that returns the external system response.

---

# Exercise 09

# Developing a MuleSoft API-Led Architecture for Account Management

## Objective

Design and implement MuleSoft APIs using the **API-Led Connectivity model**.

Layers include:

* Experience API
* Process API
* System APIs

---

## 1. Experience API

### Role

Acts as the front-facing API for external clients.

### Endpoints

GET /query
Query account data.

POST /update
Insert or update account data.

### Responsibility

Forward client requests to the Process API.

---

## 2. Process API

### Endpoint

POST /account-management

### Logic Flow

1. Receive request from Experience API.
2. Call Salesforce System API to check if account exists.

If account exists:

* Upsert the record.

If account does not exist:

* Insert a new record.

Optionally synchronize data with the Database System API.

---

## 3. System APIs

### A. Salesforce System API

Endpoints:

POST /query
Execute dynamic SOQL queries.

POST /upsert
Insert or update Salesforce objects dynamically.

Role: Communicate directly with Salesforce.

---

### B. Database System API

Endpoints:

POST /query
Execute SQL queries dynamically.

POST /update
Insert or update database records.

Role: Communicate directly with the database.

---

# Exercise 10

## Title

OAuth 2.0 Deep Dive – Authorization Code Flow with Token Reuse

## Overview

Implement a complete OAuth 2.0 Authorization Code Flow.

### Concepts

* Authorization Code Flow
* Access Token vs Refresh Token
* Token expiration handling
* Token reuse

### Systems

OAuth Providers:

* Google
* Salesforce

Token Storage:

* Mule Object Store

Testing:

* Postman

### Steps

1. Configure OAuth credentials:

   * Client ID
   * Client Secret
   * Authorization URL
   * Token URL

2. Create login endpoint:

/login → Redirect user to authorization server

3. Capture authorization code:

/callback → Receive authorization code

4. Exchange code for token using HTTP Request.

5. Store token in Object Store.

6. Before every API call:

   * Check if token exists
   * If expired → refresh token
   * Else → reuse token

Example header:

Authorization: Bearer #[vars.accessToken]

---

# Exercise 11

## Title

MuleSoft Batch Processing (Handling Large Data)

## Overview

Learn how to process large datasets using MuleSoft Batch Jobs.

### Concepts

* Batch processing
* Record processing
* Parallel execution

### Input

* Large JSON files
* Large CSV files

### Batch Phases

1. Load
2. Process
3. On Complete

### Tasks

* Transform records using DataWeave
* Insert processed records into:

  * MySQL
  * Salesforce

---

# Exercise 12

## Title

DataWeave Advanced Transformations

## Overview

Practice complex DataWeave transformations used in real-world integrations.

### Concepts

* map
* filter
* reduce
* flatten
* groupBy
* conditional transformations

### Steps

1. Input complex JSON data.
2. Perform nested mapping.
3. Filter records.
4. Group data.
5. Output clean structured JSON.

---

# Exercise 13

## Title

File Processing (CSV, XML, JSON)

## Overview

Work with file-based integrations in MuleSoft.

### Concepts

* File Connector
* File parsing
* Batch file processing

### File Sources

* Local file system
* SFTP server

### Steps

1. Read file from local storage or SFTP.
2. Parse file formats:

   * CSV → JSON
   * XML → JSON
3. Transform data using DataWeave.
4. Store the processed data in a database.

---
