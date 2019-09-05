# graphql-with-spring-boot
A sample application with GraphQL and Spring Boot

# Testing the Application
The application is now ready for testing. Run the Spring Boot application, and open this link — http://localhost:8080/graphiql — in the browser. We will see a nice user interface as below.

![User interface](https://i1.wp.com/techshard.com/wp-content/uploads/2019/08/Annotation-2019-08-21-224723.png?resize=768%2C391&ssl=1 "User interface")

On the right side of user interface, we can also explore documentation.

![Documentation explorer](https://i1.wp.com/techshard.com/wp-content/uploads/2019/08/Annotation-2019-08-21-224841.png?w=562&ssl=1 "Documentation explorer")

Now, run the following query.

```
mutation {
  createVehicle(type: "car", modelCode: "XYZ0192", brandName: "XYZ", launchDate: "2016-08-16") 
  {
    id
  }
}
```

This will create a row in the Vehicle table. The result should be:
```
{
  "data": {
    "createVehicle": {
      "id": "1"
    }
  }
}
```
Let's now run a query to get the data.
```
query {
  vehicles(count: 1) 
  {
    id, 
    type, 
    modelCode
  }
}
```
The output will be:
```
{
  "data": {
    "vehicles": [
      {
        "id": "1",
        "type": "bus",
        "modelCode": "XYZ123"
      }
    ]
  }
}
```
Note that we are requesting for only a limited number of fields, we can change our query by adding or removing fields and see the new results.