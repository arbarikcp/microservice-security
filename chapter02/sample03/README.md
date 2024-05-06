## Chapter 2: First steps in securing microservices (sample03)

[https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample03](https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample03)
- This implements a secure Order service, its REST API are secured by the OAuth Authorization service.
- We must enable Spring websecurity by `@EnableWebSecurity`
- So in this case Order service will act as a Resource `@EnableResourceServer` in `ResourceServerConfig`
- Get the token From Authorization server and then pass that token to crete an Order.
- This project contains a bean `ResourceServerTokenServices` . this object does the token validation from Authorization server.
- As in Authorization server we have a endpoint `/check_token` which gets more detail about the token.
- In `ResourceServerConfig` we have defined the scope needed for each endpoint.
- 