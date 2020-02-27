Cors Issue in angular:

Exception: Access to XMLHttpRequest at 'http://localhost/api/...php' from origin 'http://localhost:4200' has been blocked by CORS policy: Request header field content-type is not allowed by Access-Control-Allow-Headers in preflight response.

Solution:

Reference :: https://angular.io/guide/build#using-corporate-proxy

Proxying to a backend server

You can use the proxying support in the webpack dev server to divert certain URLs to a backend server, by passing a file to the --proxy-config build option. For example, to divert all calls for http://localhost:4200/api to a server running on http://localhost:3000/api, take the following steps.

1. Create a file proxy.conf.json in your project's src/ folder.
2. Add the following content to the new proxy file:
{
  "/api": {
    "target": "http://localhost:3000",
    "secure": false
  }
}

3. In the CLI configuration file, angular.json, add the proxyConfig option to the serve target:
...
"architect": {
  "serve": {
    "builder": "@angular-devkit/build-angular:dev-server",
    "options": {
      "browserTarget": "your-application-name:build",
      "proxyConfig": "src/proxy.conf.json"
    },
...

4. To run the dev server with this proxy configuration, call ng serve.

You can edit the proxy configuration file to add configuration options; some examples are given below. For a description of all options, see webpack DevServer documentation.
Note that if you edit the proxy configuration file, you must relaunch the ng serve process to make your changes effective.
