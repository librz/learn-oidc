# OAuth

OAuth is a authorization framework that allows 3rd party app to obtain limited access to an HTTP service.

RFC: https://datatracker.ietf.org/doc/html/rfc6749

### Use Cases

- delegate 

### Roles

1. Resource Owner(typically end-user)
2. Resource Server(holds resource, typically your owner backend server)
3. Client(an app on behalf of resource owner, typically browser)
4. Authorization Server(server responsible for issuing auth token)

### Endpoints

1. authorization endpoint(resource owner are redirected here for authentication, the outcome of this step is often a code representing user grant)
2. token endpoint(user-agent makes an api call to authorization server using code generated in last step in exchange for access token)
3. redirection endpoint(this is usually your app url that the authorization server redirects to after user grant)

After user grant, why not redirectly directly with access token? In short, this has to do with security concerns:

- when redirect, all the info is in the url which can be obtained by attackers
- the code is designed to be used one time, it can only be used once. If it was used by u, attacker can not use it anymore
- the code is designed to be short-lived
- access tokens can be used repeatly as long as it's not expired

### Tokens

1. access token (a string representaion of credentials used to access protected resources, usually in the form of JWT since it's signed and can guarantee the credentails is not tampered with)
2. refresh token (a token used to obtain access token, usually a JWT as well)
