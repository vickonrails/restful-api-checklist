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

### Authentication and Authorization

- [ ] **OAuth**: Implement authentication with third-party OAuth services like Facebook, Twitter, etc.
- [ ] **Auth Endpoints**: Ensure endpoints for basic authentication activies like `sign-in`, `sign-up`, `forgot-password`, `recover-password` are available.
- [ ] **JWT or API Keys**: You would want to implement one of JWT or API Keys auth depending on the use case for the API.
- [ ] **Roles Based Authorization**: Implement roles to authorize users' operations.
- [ ] **Encrypt Sensitive Information**: Store encrypted versions of users' passwords and other sensitive information.

### Security

- [ ] **2FA**: Implement Two Factor Authentication for sensitive operations like reset password, activities after a long time of inactivity.
- [ ] **Always Use HTTPs**: Install an SSL certificate and ensure all no request is served via HTTP.
- [ ] **Hash credentials**: Implement encryption for sensitive information like passwordds and other tokens.
- [ ] **Hoard Sensitive Information**: Respond to requests with only relevant fields. Don't just spit out every field from the database.
- [ ] **Don't expose your Id**: If you use integers as Ids, don't always expose them so people can't just guess things. Maybe use GUIDs alongside.

### Performance

- Coming soon

### URL and Routing

- Coming soon

### API Versioning

- Coming soon

### Testing

- Coming soon

### CI & CD

- Coming soon

### Error Handling

- Coming soon

### Response Payload

- [ ] **Consistent Response Payload**: Keep the response structure constant so people can know where to find things let error messages and payload data.
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

### Rate Limiting & Trottling

- Coming soon

### API Documentation

- Coming soon

### Caching

- Coming soon

## Contributing

Please contribute with tips/best practices

- Fork the repository
- Create your own branch
- Make your changes (Once per pull request)
- Send your pull request
