# OAuth 

We use [OAuth](http://oauth.net/) to publish and allow
you to interact with our data in a safe and secure manner.

## Send secure authorized requests to the WWstay API

####Features 

1. Secure - 
Users are not required to share their passwords with 3rd party applications, increasing account security.
2. Standard - 
A wealth of client libraries and example code are compatible with OAuth implementation.

WWstay APIs use the **[OAuth 2.0](http://tools.ietf.org/html/rfc6749)** protocol for authentication and authorization. 
WWstay supports common OAuth 2.0 scenarios such as those for web server, installed, and client-side applications.

###Authentication Model

There are two forms of authentication.

**1. Application-user authentication :**

This is the most common form of resource authentication. 
Your signed request both identifies your application’s identity 
in addition to the identity accompanying granted permissions of 
the end-user you’re making API calls on behalf of, 
represented by the user’s access token.


**2. Application-only authentication :**

Application-only authentication is a form of authentication where 
your application makes API requests on its own behalf, without a user context.

# Register An Application


You can create new applications on WWstay Developer Site. 
You must be logged-in to your WWstay account in order to do so.
To begin, obtain OAuth 2.0 client credentials by
<h4><a href="https://stage.wwstay.com/app/o/applications/" target="_blank" class="btn btn-primary" style="text-align:center;">Register An Application</a></h4>

Upon registering you will get <CLIENT_ID> and <CLIENT_SECRET> for the registered application.
These credentials can be used to obtain access token in the next step.
#POST oauth2/token

Allows a registered application to obtain an OAuth 2 Bearer Token, 
which can be used to make API requests on an application’s own behalf, without a user context. 
This is called Application-only authentication.

As with all API methods, HTTPS is always required.

Successful responses include a JSON-structure describing the awarded Bearer Token.

**Resource URL**

```
https://stage.wwstay.com/app/o/token/
```

**Parameters**

|Parameter       | Significance                                                                                                        |
|----------------|---------------------------------------------------------------------------------------------------------------------|
| grant_type     | **Required.** Specifies the type of grant being requested by the application.Example Values: client_credentials |                
| client_id      | **Required.** The client ID you received upon registering your application.                                         |
| client_secret  | **Required.** The client Secret you received upon registering your application.                                     |

&nbsp;

**Sample Curl Request:**

```
curl -X POST -d "client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>&grant_type=client_credentials" https://stage.wwstay.com/app/o/token/
```

**Response For Sample Request:**

```
HTTP/1.1 200 OK
Status: 200 OK
Content-Type: application/json; charset=utf-8
...
Content-Encoding: gzip
Content-Length: 140

{"token_type":"bearer","access_token":"<ACCESS_TOKEN>"}

```

