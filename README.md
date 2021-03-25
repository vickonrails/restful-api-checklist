<h1>
    Restful API Checklist
</h1>

<p>You know how you would normally cross your t's and dot your i's after writing an exam?</p>

<p>Restful API checklist is a group of tips and best practices to ensure your API complies with the Restful API Standards, is easy to use and maintain.</p>

> I'm no expert in building APIs. Heck, I haven't built any production one yet, but I've been doing some research while building [WhereAPI](http://whereapi.xyz/), and this is the guide I've followed. I hope it helps you too.

## Checklist Sections

1. **[Authentication & Authorization](#authentication-and-authorization)**
2. **[Security](#security)**
3. **[Performance](#performance)**
4. **[URL and Routing](#url-and-routing)**
5. **[API Versioning](#api-versioning)**
6. **[Testing](#testing)**
7. **[Continious Integration and Delivery](#ci-and-cd)**
8. **[Error Handling](#error-handling)**
9. **[Response Payload/Body](#response-payload)**
10. **[Rate Limiting & Throttling](#rate-limiting-and-throttling)**
11. **[API Documentation](#api-documentation)**
12. **[Caching](#caching)**
13. **[References](#references)**

### Authentication and Authorization

- [ ] **OAuth**: Implement authentication with third-party OAuth services like Facebook, Twitter, etc.
- [ ] **Auth 2.0 Endpoints**: Ensure endpoints for basic authentication activies like `sign-in`, `sign-up`, `forgot-password`, `recover-password` are available.
- [ ] **JWT or API Keys**: You would want to implement one of JWT or API Keys auth depending on the use case for the API.
- [ ] **Roles Based Authorization**: Implement roles to authorize users' operations.
- [ ] **Encrypt Sensitive Information**: Store encrypted versions of users' passwords and other sensitive information.

### Security

- [ ] **2FA**: Implement Two Factor Authentication for sensitive operations like reset password, activities after a long time of inactivity.
- [ ] **Always Use HTTPs**: Install an SSL certificate and ensure all no request is served via HTTP.
- [ ] **Hash credentials**: Implement encryption for sensitive information like passwordds and other tokens.
- [ ] **Hoard Sensitive Information**: Respond to requests with only relevant fields. Don't just spit out every field from the database.
- [ ] **Don't expose your Id**: If you use integers as Ids, don't always expose them so people can't just guess things. Maybe use GUIDs alongside.
- [ ] **Implement CORS**: Your API would most likely be used by a single page application (SPA). Ensure the right sites have access to the API.
- [ ] **Don't store secure information in JWT**: Most times, you'll want to store select information in a JWT. Don't store sensitive information in JWT.

### Performance

- Coming soon

### URL and Routing

- [ ] **Nouns not Verbs**: Name all endpoints as nouns and not verbs. The method of requests already act as verbs.
- [ ] **Plural Names**: All resources that are collections are in plural form. Single items are in singular form.
- [ ] **Resources are nested**: Relationships between entities are represented in the url. Take for example, [https://blogs.com/articles/2024/comments/2](https://blogs.com/articles/2024/comments/2), comments revolve around articles. So it makes sense to be nested url-wise.
- [ ] **Addressible through a URI**: All resources on the server are addressible via a URI and can be exposed by a single request.
- [ ] **Request Idempotency**: A `DELETE` request is idempotent in that hitting the same request multiple times does not do anything (Because the resource has already been removed. Just returns an error). `GET`, `PUT` `PATCH` & `DELETE` must be idempotent. Subsequent invocations of the same request will have no adverse consequences.

### API Versioning

- [ ] **Version APIs**: Assign major versions (v1, v2, v3) to APIs for backward compactibility and easy debugging. You might not need a version if the default API is the most up-to-date one.

### Testing

- [ ] **Use automated testing**: You can't manually test every endpoint before deploying to production. You can run automated tests to ensure compliance after making changes to the code.
- [ ] **Load test**: There's only one way to know if your API can perform well in rugged conditions - test it. Certain metrics are requests per second, requests per minute, etc.

### CI & CD

- Coming soon

### Error Handling

- [ ] **Extend the error object**: You might need to extend the error object of your language to provide more details about your error.
- [ ] **Readable error message**: Alongside your error code, should be a human-readable explanation of your error. Developers can show this to their users too.

### Response Payload

- [ ] **Consistent Response Payload**: Keep the response structure constant so people can know where to find things let error messages and payload data.
- [ ] **Standard HTTP Methods**: Always respond with standard HTTP methods.

  | HTTP Method | Meaning                                       |
  | ----------- | --------------------------------------------- |
  | GET         | Fetch or read a resource                      |
  | POST        | Create a new resource                         |
  | PUT         | Edit a resource or create new if not existing |
  | PATCH       | Incrementally edit a resource                 |
  | DELETE      | Remove a resource or item                     |

- [ ] **Appropriate Status Codes**: Respond with appropriate status codes.

  | Status Code | Description                                                                                                                                   |
  | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
  | 200         | The request was successful.                                                                                                                   |
  | 201         | A resource was successfully created.                                                                                                          |
  | 202         | Request has been received. This is only used for asynchronous processing.                                                                     |
  | 304         | The GET request was conditional and contained an 'If-None-Match' header that was used to determine the current representation has not changed |
  | 400         | Bad request. This should be used if there are syntax errors and validation errors.                                                            |
  | 401         | Authentication has failed, or the authenticated client is not authorized.                                                                     |
  | 404         | The requested resource could not be found.                                                                                                    |
  | 405         | The method is not supported by the resource.                                                                                                  |
  | 406         | Not Acceptable. Return this code when the Accept header identifies an unsupported format.                                                     |
  | 409         | There is a conflict. Return this if the request reflects stale data (that violates an optimistic lock).                                       |
  | 412         | A precondition failed. Used for conditional requests (e.g., when an 'If-Match' header does not match a resource's Etag value).                |
  | 415         | Unsupported Media Type. Return when a client requests content in an unsupported format.                                                       |
  | 417         | Expectation Failed. Return this if appropriate when supporting 'look-before-you-leap' requests.                                               |
  | 422         | Unprocessable entity.                                                                                                                         |
  | 429         | The rate limit is exceeded.                                                                                                                   |
  | 500         | Internal server error                                                                                                                         |

- [ ] **Pagination**: Sending very, unpaginated volumes of data can heavily slow down the server, network or client. Ensure all collections of resources implement pagination by default (Even without any query parameters).
- [ ] **Self discovery**: Respond to an API call with links to related resources. This is the best form of your API documentation and makes discovery of other endpoints faster.
- [ ] **Expose appropriate headers**: Headers can be useful for storing additional information. Store things like pagination info, security and other browser information here.

### Rate Limiting & Trottling

- [ ] **Implement rate limiting**: Avoid DOS attacks and protect your server. Denial of Service (DOS) attacks aim to make your server unavailable by sending thousands of requests in very little time.

### API Documentation

- [ ] **API documentation**: Documentation should be accessible, example-based and easy to use. An API is as good as the documentation.

### Caching

- Coming soon

## Contributing

Please contribute with tips/best practices

- Fork the repository
- Create your own branch
- Make your changes (Once per pull request)
- Send your pull request
