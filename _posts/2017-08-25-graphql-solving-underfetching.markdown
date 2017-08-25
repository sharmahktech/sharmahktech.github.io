---
layout:     post
title:      "GraphQL - Solving Underfetching"
subtitle:   "Let's see if we can"
date:       2017-08-25 12:00:00
author:     "HK"
header-img: ""
---


<p>In the  <a href="https://sharmahktech.github.io/2017/08/24/graphql-why-do-you-need-to-know/"> earlier post</a> we briefly discussed that GraphQL can be used to solve under fetching problem. Now let's try to see with an example if we can really do it.

</p>

<p>
Before Going ahead, let's discuss as to what is under fetching. Let’s assume that we have two services. First Service is to fetch employ details like first name, last name and second service is fetching employ address like city, street etc..

</p>
<p>
Consider that we have to display employ list with three fields - first name, last name and city. To display this information we will need to call two services. First service will fetch first name and last name whereas second service will fetch city information.

</p>

> So we can define under fetching as a problem where we don't get enough information in one service but to fetch additional data or information about the subject, we will need to invoke second/multiple service.

<p>
Let's see how we solve this problem using GraphQL.

</p>

<p>
Let me try to explain the problem that we want to solve.

</p>
<p>
We have a requirement to display list of employs. In the list we want to display first name last name and city.

</p>
<p>
We have service available which returns as the first name and last name. We have another service available which returns street and city. So to display employ information in the list we will need to invoke these two services.

</p>
<p>
And that is what we don't want and we want to call only one service which will return us the required date.

</p>

<p>
I am using nodejs to develop GraphQL server. You will need "express", "express-graphql" and "graphql" for writing the code.
</p>

<p>
To mimic the behavior of invoking a service and getting the data from the database, we are declaring some constants. Below is the data to mimic the first service we discussed -
</p>

    const emp = [
      {
        id: "1",
        firstName: "John",
        lastName: "Wire"
      }, {
        id: "2",
        firstName: "Jem",
        lastName: "Will"
      }, {
        id: "3",
        firstName: "Jill",
        lastName: "Smith"
      }, {
        id: "4",
        firstName: "Jul",
        lastName: "Tan"
      }
    ]


<p>
And below is the data to mimic the second service we discussed -
</p>

        const addr = [
          {
            id: "1",
            street: "Lake street",
            city: "Dream City"
          }, {
            id: "2",
            street: "River street",
            city: "Dream City"
          }, {
            id: "3",
            street: "Sea street",
            city: "Dream City"
          }, {
            id: "4",
            street: "No street",
            city: "Dream City"
          }
        ]

<p>
Here is the schema using the GraphQL schema language -
</p>

            var schema = buildSchema(`
              type Employ {
                firstName: String!
                lastName: String!
                street: String!
                city: String!
              }
              type Query {
                getEmploy(id: String!): Employ
              }
            `);
<P>
You can see that we are declaring a new type "Employ" which consists of four field. So the type "Employ" is combining the fields available in two different services.
</P>

<p>
Now let's see resolvers. We have "getEmploy" which invokes two  services and then create an object of Employ type.
</p>

    var root = {
      getEmploy: function({id}) {
        var emp1 = findEmp("id", id);
        var addr1 = findAddr("id", id)
        return new Employ(emp1[0].firstName, emp1[0].lastName, addr1[0].street, addr1[0].city );
      }
    }

<p>
We will also need to declare Employ class with all the required fields and functions, to be used in GraphQL query.
</p>

        class Employ{
          constructor(firstName, lastName, street, city) {
            this.firstName = firstName;
            this.lastName = lastName;
            this.street = street;
            this.city = city;
          }
          firstName(){
            return this.firstName;
          }
          lastName(){
            return this.lastName;
          }
          street(){
            return this.street;
          }
          city(){
            return this.city;
          }
        }
<p>
With this we should be ready to see if we can really solve the under fetching problem. You can download the <a href="https://github.com/sharmahktech/graphqlexp/"> source code</a> from my GitHub account.
<p>

<p>
Now lets switch to GraphiQL (after starting the server) and test what we have developed so far -
</p>

<a href="#">
    <img src="{{ site.baseurl }}/img/graphiql-1.jpg" alt="fig-1">
</a>

<p>
As you can see that we are able to fetch all required data, in only one GraphQL service call only. Still we will need to discuss that how it is better than the REST services.
I hope you enjoyed reading this post.
</p>
