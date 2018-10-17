This repo is to help me - and anyone else who may derive value from it - better understand GraphQL and Apollo.

# GraphQL

GraphQL allows users to fullfill queries of *existing* data.

  * It is a syntax that describes how to ask for data.
  * It is generally used to load data from a server to a client.

The GraphQL layer exists between the client (React) and one - or more - data sources (database).

Characteristics of GraphQL:

  * It allows the client to specify exactly what data it needs
  * It makes it easier to aggregate data from multiple resources 
  * It uses a type system to describe data

Building blocks of GraphQL:

  * schemas
  * queries
  * resolvers

## **Queries**
  * The request you make to GraphQL is a query.
    ```js
      // overview of query syntax
      operation_type operation_name (variable_definitions) { 
        selection_sets 
      }

      // basic example
      // declare a new query with the `query` keyword
      // look for the field name `stuff`
      query {
        stuff
      }

      // we can also look for nested fields
      query {
        stuff {
          name
          age
          height
        }
      }

      // query fields can also point to arrays
      query {
        posts { // this is an array of posts
          title
          content
          author {
            name
            profileURL
          }
        }
      }

      // query fields also support arguments 
      // if we want to retrieve a specific post...
      query {
        post (id: "abc123") {
          title
          content
          author {
            name
            profileURL
          }
        }
      }

      // we can also make the arguments dynamic
      query getMyPost($id: String) {
        post (id: $id) {
          title
          content
          author {
            name
            profileURL
          }
        }
      }
    ```



1. Install dependencies.

    * `apollo-server` --- allows you to define the shape of your data and how to fetch it
    * `graphql` --- used to build schemas and execute queries on those schemas