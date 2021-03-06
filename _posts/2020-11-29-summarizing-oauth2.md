---
layout: post
title:  "Summarizing OAuth 2.0"
date:   2020-11-29
categories: OAuth2 Summary Security Autherization
---
# What OAuth 2.0 Solves 
The OAuth 2.0 authorization framework enables a third-party
   application to obtain limited access to an HTTP service. [1]

# The Four Main Flows

Definition of the terms used here   
- User-agent - Domain restricted web page in a browser, mobile app or similar component the user interact directly with 
- Client-server - Server that holds the business logic and resources of the application 
- Auth-server - Authorization server that holds on to the user ids, credentials, details about permissions, and gives access tokens  
- Resource-server - The third party server that the current application wants to access a resource from. When the frontend has a seperate server that serves the web pages, this resource-server can be the backend-server that exposes an API.  

I. Autherization Code Flow

1. User triggers an action that requires access to a resource   
2. User-agent redirects the user to the auth-server   
3. User proves themselves (give username, password)  
4. Auth-server redirects the user to the client-server via the user-agent, with the auth code attached to the url   
5. Client-server exchange this auth code into an access token from the auth-server   
6. Client-server uses the access-token to access the resources in a certain scope in the resource-server, and delivers the service via the user-agent   

- The user-agent (client side code) does not get to see the access token. Only sees the short lived auth code.
- Username and password not shared with the resource server and the client server
- Auth-server may also provide a refresh token

II. Implicit Flow

1. User triggers an action that requires access to a resource
2. User-agent redirects the user to the auth-server
3. User proves themselves (give username, password)
4. Auth-server redirects the user to the client-server via the user-agent, with the access token
5. Client-server or the user-agent can use the access token to access the resource

- Username and password not shared with the resource server and the client server

III. Resource Owner Password Credentials Flow

1. User triggers an action that requires access to a resource
2. User-agent gets the username and password from the user, and sends them to the auth-server
3. Client-server or the user-agent can use the received access token to access the resource

- Do not have to use the username and password everytime a resource is accessed

IV. Client Credentials Flow

1. User triggers an action that requires access to a resource
2. User-agent (Client app) gets itself autherized with the auth-server, using a client ID and client secret (all other flows above would also perform this, if other methods to verify the client are not used)
3. User-agent gets an access token. It can then access the resource.

- User-agent represents the user 

Best Practices  
[https://tools.ietf.org/html/draft-ietf-oauth-security-topics-16](https://tools.ietf.org/html/draft-ietf-oauth-security-topics-16)



# References

1. [The OAuth 2.0 Authorization Framework](https://tools.ietf.org)
2. [A youtube video on OAuth 2.0](https://www.youtube.com/watch?v=996OiexHze0)

