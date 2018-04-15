# Noticeable API Samples

The Noticeable API implements [GraphQL](https://graphql.org/learn/). 
This repository provides samples for common operations.

## How to call the GraphQL endpoint?

The Noticeable GraphQL API has a single HTTP endpoint:

https://api.noticeable.io/graphql

The endpoint remains constant no matter what operation you perform (query or mutation).

### Sending requests

The GraphQL API accepts both GET and POST requests.

You can make HTTP requests with any clients. However, for testing purposes, we recommend using our explorer that 
provides automatic completion, real-time error highlighting, intelligent type ahead and syntax highlighting:

https://api.noticeable.io/graphiql?accessToken=YOUR_ACCESS_TOKEN

#### GET requests

A GET request must pass _query_, optional _variables_ and _operationName_ in the URL.

Here is a well-formatted GET request to our API using cURL:

```bash
curl --header "Authorization: Apikey YOUR_ACCESS_TOKEN" \
     --get https://api.noticeable.io/graphql \
     --data-urlencode "query=YOUR_GRAPHQL_PAYLOAD"
```

In the above command `YOUR_ACCESS_TOKEN` and `YOUR_GRAPHQL_PAYLOAD` must be replaced by your own values:

- `YOUR_ACCESS_TOKEN`: As a project owner, you can create or retrieve an Access Token [from your dashboard](https://noticeable.io/api/tokens).
- `YOUR_GRAPHQL_PAYLOAD`: For instance, the content from one of the `.graphql` files provided in this repository (you need to escape double quotes inside double quotes).

**Note**: GET requests have the benefit of hitting a powerful global Content Delivery Network (CDN) to make your requests 
as fast as possible. However, updates to any data accessed by the API may take up to 5 minutes to propagate. 
Besides, GET requests do not affect your quota when they hit the CDN. 
For this reason, this is the recommended manner to consume the API with read operations aka queries (not mutations).

#### POST requests

A POST request accepts a JSON body. It must contain either a _query_ or an _operationName_ 
(or both, in case of a named query), and may include _variables_.

Here's an example of a valid POST request using cURL:

```bash
curl --header "Authorization: Apikey YOUR_ACCESS_TOKEN" \
     --header "Content-Type: application/json" \
     --request POST https://api.noticeable.io/graphql \
     --data '{"query": "YOUR_GRAPHQL_PAYLOAD"}'
```

In the above command `YOUR_ACCESS_TOKEN` and `YOUR_GRAPHQL_PAYLOAD` must be replaced by your own values:

- `YOUR_ACCESS_TOKEN`: As a project owner, you can create or retrieve an Access Token [from your dashboard](https://noticeable.io/api/tokens).
- `YOUR_GRAPHQL_PAYLOAD`: For instance, the content from one of the `.graphql` files provided in this repository (you need to escape double quotes inside double quotes).

**Warning:** POST requests are never cached. As a consequence, every request counts against your API Calls quota.

## Schema documentation

https://graphdoc.noticeable.io
