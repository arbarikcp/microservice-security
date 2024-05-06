## Chapter 2: First steps in securing microservices (sample01)

[https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample01](https://github.com/microservices-security-in-action/samples/tree/master/chapter02/sample01)
 
### Unsecure Order service 

- **mvn clean install**
- **mvn spring-boot:run**
this will start the service on port 8080, defined in application.properties.
- the below request will create an order with the items.
- ```dockerfile
  curl --location 'http://localhost:8080/orders' \
  --header 'Content-Type: application/json' \
  --data '{
  "items":[
  {
  "itemCode":"IT0001",
  "quantity":3
  },
  {
  "itemCode":"IT0004",
  "quantity":1
  }
  ],
  "shippingAddress":"No 4, Castro Street, Mountain View, CA, USA"
  }'
    ```
- We can fetch order detail by below call.
- ```
    curl --location --request GET 'http://localhost:8080/orders/026ab900-d76e-43c2-aa31-d4d41c89438e'
    ```
  