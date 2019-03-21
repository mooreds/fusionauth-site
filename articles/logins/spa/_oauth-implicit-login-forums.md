1. The browser requests the forum single-page application from the application backend. This is a standard SSO login that is fully supported by FusionAuth
1. The application backend responds with the HTML, CSS & JavaScript of the application
1. The browser loads the application and as part of the initialization process, it makes a request to the application backend to see if the user is logged in 
1. The application backend responds with a 404 indicating the user is not logged in
1. The user clicks the login link and the browser navigates away from the single-page application to FusionAuth's OAuth 2 interface. The browser requests the OAuth 2 login page from FusionAuth with a `response_type` of `token` indicating that it is using the implicit grant
1. FusionAuth realizes that the user already has a session and is already logged in. Therefore, it returns a redirect to the application backend's OAuth 2 `redirect_uri`. This redirect includes the access token (in this case a JWT) from FusionAuth
1. The browser requests the application backend's OAuth `redirect_uri`. This request does not include the JWT because it is after the `#` in the URL, which means the browser will not send it in the HTTP request to the application backend 
1. The application backend responds with the HTML, CSS & JavaScript of the application. During this step, the browser will initialize the single-page application. As part of the initialization of the application, the JWT  will be pulled from the current URL of the browser 