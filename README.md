# Hybrid Flow(Steps)
1.A user tries to access the application (the client).
2.The client redirects the user to the authorize endpoint.
3.Cloudentity authenticates the user and displays a consent screen if there is an authorization scope to be granted.
4.The user gives their consent.
5.Cloudentity issues an authorization code and one or more additional parameters depending on the value for the response_type parameter provided in the second step.
6.The client performs a request to the token endpoint using authorization code provided in the previous step.
7.Cloudentity validates the request.
8.Cloudentity returns the token.
9.The client requests protected resources from the resource server and submits the token it received in the previous step.
10.The resource server validates the token and responds the requested resources.
Notes 1:
The client must inform Cloudentity of its desired grant type by using the response_type parameter. For the hybrid grant flow, the response_type can have the following values:
code id_token - a successful response contains both an authorization code and an ID token.
code token - a successful response contains an authorization code, an access token and an access token type.
code id_token token - a successful response contains an authorization code, an ID token, an access token, and an access token type.
Notes 2:
Cloudentity does not display the consent screen when there is no authorization scope to be granted.
Notes 3:
After Cloudentity generates the authorization code, it is redirected to the redirection endpoint configured for the registered client. The client must have at least one registered redirection URI. If there are multiple registered redirection URIs, the request to the authorize endpoint must always include the redirect_uri parameter. If there is only one registered redirection URI for the client, it does not have to include the redirect_uri parameter in the request to the authorize endpoint.
