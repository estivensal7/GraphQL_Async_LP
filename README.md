# GraphQL_Async_LP

### Overview

Throughout the Full Stack Web Development course we learned how to build, and work with REST APIs. In the following activities, and presentations you will learn about GraphQL! By the end of this short course you will understand the differences between the REST APIs that we have built, and the features that GraphQL has to offer. Since the best way to learn is to build, we will build a small application using React, Apollo, MongoDB, Express, and GraphQL.

[GraphQL Homepage](https://graphql.org/)

##### What is GraphQL?

GraphQL, introduced by Facebook is a query language for APIs that provides a complete and understandable description of the data in your API. It gives you the power to ask for exactly what you need from your API and nothing more. It is usually described as a frontend-directed API technology as it allows front-end developers to request data in a much simpler way than ever before. The best part is the language isn't dependent on any specific database management system.

##### GraphQL vs REST

One of the basic problems with conventional REST is the failure of the client to demand a personalized data set. In addition to that, running and controlling multiple endpoints is another difficulty as clients are mostly needed to request data from diversified endpoints. Instead of working with rigid server-defined endpoints, you can send queries to get exactly the data you’re looking for in one request using GraphQL. Therefore, a user can request a dataset from a server by transferring a query string, mentioning what they need.

GraphQL & Rest are not so different, but GraphQL has some small changes that make a big difference to the developer experience of building and consuming an API.

The core idea of REST is the resource, each resource is identified by a URL, and you receive that resource by sending a GET request to that URL. One thing to note in REST is that the type, shape, of the resource and the way you fetch that resource are coupled. See the code below for example:

```
GET /books/1

{
        "title": "The Long Earth",
        "author": {
                "firstName": "Terry",
                "lastName": "Pratchett"
        }
        // ...more fields here
}
```

_Note that in the example above, some REST APIs would return "author" as a separate resource._

In REST documentation you might refer to the example above as the "book endpoint". GraphQL is quite different in this respect, because in GraphQL these two concepts are completely separate. In your GraphQL schema you might have the _Book_ and _Author_ types.

```
type Book {
  id: ID
  title: String
  published: Date
  price: String
  author: Author
}
type Author {
  id: ID
  firstName: String
  lastName: String
  books: [Book]
}
```

Notice that we have described the kinds of data available, but this description doesn't tell you anything at all about how those objects might be fetched from a client. Ultimately, the difference here is with GraphQL the description of a particular resource is not coupled to way you retrieve it.

To be able to actually access a particular book or author, we need to create a Query type in our schema:

```
type Query {
  book(id: ID!): Book
  author(id: ID!): Author
}
```

Now, we can send a request similar to the REST request above, but with GraphQL this time:

```
GET /graphql?query={ book(id: "1") { title, author { firstName } } }

{
  "title": "Black Hole Blues",
  "author": {
    "firstName": "Janna",
  }
}
```

Awesome! Now we can see a few differences between GraphQL & REST, eventhough both can be requested via URL, and both can return the same shape of JSON response.

Let's get started with a few activities together! As we progress through the lessons, please make sure to read the `README.md` files. These files will outline the objective, and explanation of the concepts learned in each lesson.

![alt text](https://media1.tenor.com/images/6ae1c49e69cfc8d6eb2d105aa9a5b8ed/tenor.gif?itemid=4184916 "Spongebob GIF")
