# Security <!-- omit in toc -->
- [1. Introduction](#1-introduction)
  
# 1. Service Accoutns
links: 
- https://cloud.google.com/iam/docs/service-accounts
- https://cloud.google.com/iam/docs/service-accounts#short-lived-credentials

- special types of accounts used by apps and svcs
- **Non-human access** to GC API
- managed within projects like other resources
- **no associated password**, cannot log in via browser or cookies
- authentication is done via **private/public key pairs**

## 1.1. Comparison of OAuth2 and JWT
link: https://anil-pace.medium.com/json-web-tokens-vs-oauth-2-0-85dd0b32057d#:~:text=So%20the%20real%20difference%20is,JWT%20as%20a%20token%20format.

- **OAuth** is not an API or a service: it’s an open standard for authorization and anyone can implement it.
- So the real difference is that **JWT is just a token format**, **OAuth 2.0 is a protocol** (that may use a JWT as a token format or access token which is a bearer token.).
- JWT is a JSON based security token forAPI Authentication
- JWT can contain unlimited amount of data unlike cookies.
- JWT can be seen not but modifiable once it’s sent.
- JWT is just serialised, not encrypted.
- OAuth is not an API or a service: it’s an open standard for authorization .
- OAuth is a standard set of steps for obtaining a token. There are 5 different flow patterns.
- Authorization code grant is the most secure OAuth grant type
- Resource Owner grant type is the least secure

---
---
# 2. Terminology
- **Authentication** is the process of verifying the identity of a user by obtaining some sort of credentials for example his username password combination, and using those credentials to verify the user’s identity.
- **Authorization** is the process of allowing an authenticated user to access his resources by checking whether the user has access rights to the system. You can control access rights by granting or denying specific permissions to an authenticated user. So, If the authentication was successful, the authorization process starts. Authentication process always proceeds to Authorization process.