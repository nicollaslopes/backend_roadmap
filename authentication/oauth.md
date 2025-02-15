# OAuth

OAuth is _not_ an API or a service: it’s an open standard for authorization and anyone can implement it. More specifically, OAuth is a standard that apps can use to provide client applications with “secure delegated access”. OAuth works over HTTPS and authorizes devices, APIs, servers, and applications with access tokens rather than credentials.

### SAML

SAML is basically a session cookie in your browser that gives you access to webapps. It’s limited in the kinds of device profiles and scenarios you might want to do outside of a web browser.

### Pseudo-Authentication with OAuth 2.0

Login with OAuth was made famous by Facebook Connect and Twitter. In this flow, a client accesses a `/me` endpoint with an access token. All it says is that the client has access to the resource with a token. People invented this fake endpoint as a way of getting back a user profile with an access token. It’s a non-standard way to get information about the user. There’s nothing in the standards that say everyone has to implement this endpoint. Access tokens are meant to be opaque. They’re meant for the API, they’re not designed to contain user information.

What you’re really trying to answer with authentication is _who_ the user is, _when_ did the user authenticate, and _how_ did the user authenticate. You can typically answer these questions with SAML assertions, not with access tokens and authorization grants. That’s why we call this pseudo authentication.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d690d49c-5ce7-45f3-860d-a8dd2f8a52f5" alt="abstract_flow">
</p>
