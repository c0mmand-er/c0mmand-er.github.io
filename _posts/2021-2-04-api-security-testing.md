---
layout: post
title: API SECURITY TESTING
description: "APPLICATION PENTESTING"
modified: 2021-2-04
tags: [API security, pentesting]
image:
  feature:
---

![](/images/api-testing.png)

In this article, we are going to discuss a methodology that one could apply to test any kind of API. This included Analyzing the API, learning about the API, methodology to test API, and exploiting API. It also included techniques to list endpoints and exploit bugs on real production API.

## 1: Analyzing the API

First, we need to analyze the target API to know its structure and authentication mechanism. For example, we can find API endpoints like the following:

- /api/v1/magazines.json
- /api/v1/magazines/1234/articles.json

By analyzing this, we will have an idea about the structure of the API. In this example; we can list magazines by requesting **/api/v1/magazines.json**. Also, we can get articles that belongs to a specific magazine by the following request **/api/v1/magazines/1234/articles.json**.

By doing so, we will have an idea about the structure of the API and how we can formulate our requests to get a specific resource.
Also, we need to know the Authentication mechanism of the API. Authentication types are the following:

#### A: Basic HTTP authentication

While making API requests, a header is added to the HTTP request called **‘Authorization’**. This header has a value of the username and password separated by a colon (:) in base64 format. For Example;

- Username >> C0mmander

- Password >> testing

- Base64 format of C0mmander:testing >> QzBtbWFuZGVyOnRlc3Rpbmc=

Now, the header will be as shown below:

<center>Authorization: Basic QzBtbWFuZGVyOnRlc3Rpbmc=</center>

#### B: Access token

An access token is sent with the request which is verified by the API server, and thus, depending on its authenticity, the request is accepted or rejected.
First, you need to obtain an access token by authorizing an application, and then use the access token to make API requests and act on behalf of you.
That is the most common authentication method these days.

#### C: Cookies

A session cookie is used to verify the user and is created when a successful login is registered. This cookie should be replayed with every API request and based on this a cookie request is accepted or rejected.

## 2: Learning the API

### A: Developer documentation

The documentation gives a great insight into any API. You can learn about API endpoints. By reading the documentation we can understand structure, data-types, permissions, and request methods that are accepted by the endpoint.

### B: Understanding requests/responses

We need to make multiple requests with different HTTP methods to an endpoint and understand how it responds. For example: 
A GET request made to retrieve details about resource works fine. What about trying the DELETE method!! And so on. That can give us an error. We should make note of every single error. This will help understand the API and advanced exploitation at later stages.

### C: Learning scopes

It is essential to learn the scopes offered by the API. Scopes are just permissions that are enforced on the application so that the application can access only authorized resources or information about an entity using the API.

### D: Learning roles

Roles offered for specific functionality.
For example, Facebook offers different types of roles for Pages managers as the following.

![](/images/face-roles.png)
<center> https://www.facebook.com/help/289207354498410 </center>>

Sometimes many roles only work on the website while nothing has been implemented on the API to handle such roles. So, we can simply get an access_token with proper scopes and escalate privileges via the API.

## 3: Methodology to test API

### A: Listing endpoints

We need to list the endpoints to be examined. For example, if you are targeting the user endpoint, we need to list all users' relevant endpoints such as listing user information, updating user info, or deleting a user. Take notes for every request you do as the following:

- GET /v1/{user-id}
- POST /v1/{user-id}
- DELETE /v1/{user-id}

Now we understanding the API and are ready to test these mentioned endpoints.

### B: Trying different request methods

To test the endpoints, you need to fire different request methods (GET, POST, DELETE) and then observe how the API behaves. Note that, in developer documentation, accepted methods and requests may not be documented. 
Take notes on every request you do and the behavior of the server as the following:

![](/images/api-notes.png)

## 4: Exploiting API

Now we know how to examine these APIs and list endpoints, we are in a perfect position to find some bugs by following these types of testing strategies.

### A: Scope-based testing

This type of testing requires knowledge about scope (permissions) related to API.

**EXAMPLE:**

While examining the user endpoint, we came across that we need view_users and manage_users scopes (permissions) to view/add/edit/delete users. In this bug, we were able to discover that the DELETE method was missing a permission check of manage_users scope, so any user with just the view_users scope (permission) was able to delete users from the application.


### B: Roles-based testing
Assuming that we have already studied page roles applied to our targeted API. We will find bugs using the information about roles implemented on a specific resource.

**EXAMPLE:**

While testing an Android app, we found a chat endpoint. Using this endpoint, an application was able to access the chat of a user. We have three roles:

- Admin
- Editor
- Analyst

Via the website, the admin and the editor are allowed to access chat while the analyst didn't have chat access. In this bug, analysts were able to escalate privileges to delete chat using their access tokens generated from the android app. 

### C: Insecure Direct Object Reference testing

Insecure direct object references (IDOR) are a type of access control vulnerability that arises when an application uses user-supplied input to access objects directly (portswigger.net).

**EXAMPLE:**

We came across an endpoint that we can use to view other companies' files. Let's assume that the endpoint is the following:

- GET /v1/files/{file-id}

By changing the file-id to another file-id that belongs to another company, we were able to access files of other companies. While testing for IDORs, you have to forget all the scopes and roles for the given API and try to test endpoints freely.

# Final Note

Those are just a few strategies that you can apply during any API security testing. Also, we have discussed scenarios in access token-based API, but you can use the same concepts and same ideas to find bugs in other APIs designs or any other custom designed API.
