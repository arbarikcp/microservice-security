## Chapter 2: First steps in securing microservices (sample02)

[https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample02](https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample02)
- We must enable Spring websecurity by `@EnableWebSecurity`
- This one creates a OAuth Authorization server, `@EnableAuthorizationServer`
- Also registers few inmemory client in `OAuthServerConfig.java`
- ``` 
  curl -u orderprocessingapp:orderprocessingappsecret \
  'http://localhost:8085/oauth/token' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Basic b3JkZXJwcm9jZXNzaW5nYXBwOm9yZGVycHJvY2Vzc2luZ2FwcHNlY3JldA==' \
    --data '{
    "grant_type": "client_credentials",
    "scope": "read write"
    }
  ```
- ```
    curl --location 'http://localhost:8085/oauth/token' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Basic b3JkZXJwcm9jZXNzaW5nYXBwOm9yZGVycHJvY2Vzc2luZ2FwcHNlY3JldA==' \
    --data '{
    "grant_type": "client_credentials",
    "scope": "read write"
    }'
    ```
- response
  - ```
    {
    "access_token": "fef007bd-f2c6-4ed3-8cd7-3d1c9168d96b",
    "token_type": "bearer",
    "expires_in": 3599,
    "scope": "read write"
}
    ```

- it also has an endpoint to check the token, as it produces an opaque token, So Resource server should get more detail about the token to validate and Authorize.
  - ```
    curl --location --request POST 'http://localhost:8085/oauth/check_token?token=fef007bd-f2c6-4ed3-8cd7-3d1c9168d96b' \
    --header 'Authorization: Basic b3JkZXJwcm9jZXNzaW5nYXBwOm9yZGVycHJvY2Vzc2luZ2FwcHNlY3JldA=='
    ```
- Response:    
- ```
      {
        "aud": [
            "sample-oauth"
        ],
        "scope": [
            "read",
            "write"
        ],
        "active": true,
        "exp": 1714997624,
        "client_id": "orderprocessingapp"
      }
 ```  