Collect REST API Authentication
==========================
Sign up
-------
The Collect REST API use authentication from auth0.com. Before you can use the REST API you must register with email and password [here](https://itcauth0prod.eu.auth0.com/login?client=ST9a66rvqw3CA7hWFGJgEuqMARB8Kjfx&redirect_uri=https%3A%2F%2Fwww.intelecom.no). When done, please contact Puzzel Service Desk to get access to the correct customer data.

Get access token
----------------
To access the API you must provide an authorization token in your requests. To get hold of this token you must use a service at auth0.com supplying your email and password along with some data:

URL: https://itcauth0prod.eu.auth0.com/oauth/ro

Method: POST

Content-Type: application/json

Content body:
```json
{
  "username":    "<your username>",
  "client_id":   "ST9a66rvqw3CA7hWFGJgEuqMARB8Kjfx",
  "password":    "<your password>",
  "id_token":    "",
  "connection":  "collect-api-database",
  "grant_type":  "password",
  "scope":       "openid",
  "device":      ""
}
```

Response sample:
```json
{
    "id_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwczovL2l0Y2F1dGgwZGV2LmV1LmF1dGgwLmNvbS8iLCJzdWIiOiJhdXRoMHw1NmZkMDUzZDdjMWZiM2RkMjY3YmM3ZTYiLCJhdWQiOiJFb3J0RVVDMXNDa3RtbFpMdEFJQ0p2UGRmZjJjTmdYbCIsImV4cCI6MTQ1OTQ1OTMwNiwiaWF0IjoxNDU5NDIzMzA2fQ.7CcrbAgBpXmnvEccZdgscVxgevzbFPMryG5z7gkpBrw",
    "access_token": "24nTW53UeoAaZFm0",
    "token_type": "bearer"
}
```

Use access token
----------------
To authenticate to the Collect API add the following header to your requests:
```
Authorization: Bearer <id_token from response above>
```

This access token is only valid for a limited time, and must be renewed when you receive a HTTP status code 401 (not authorized) from the Collect API. To renew the access token you must follow the procedure described above for "Get access token".
