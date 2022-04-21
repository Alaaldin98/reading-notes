## Navigation Properties and Routing Submission Requirements

## ASP.NET MVC Routing Overview (C#)
> In this tutorial, Stephen Walther shows how the ASP.NET MVC framework maps browser requests to controller actions.

In this tutorial, you are introduced to an important feature of every ASP.NET MVC application called ASP.NET Routing. The ASP.NET Routing module is responsible for mapping incoming browser requests to particular MVC controller actions. By the end of this tutorial, you will understand how the standard route table maps requests to controller actions.

## Using the Default Route Table
When you create a new ASP.NET MVC application, the application is already configured to use ASP.NET Routing. ASP.NET Routing is setup in two places.

First, ASP.NET Routing is enabled in your application's Web configuration file (Web.config file). There are four sections in the configuration file that are relevant to routing: the system.web.httpModules section, the system.web.httpHandlers section, the system.webserver.modules section, and the system.webserver.handlers section. Be careful not to delete these sections because without these sections routing will no longer work.

Second, and more importantly, a route table is created in the application's Global.asax file. The Global.asax file is a special file that contains event handlers for ASP.NET application lifecycle events. The route table is created during the Application Start event.

 

When an MVC application first starts, the Application_Start() method is called. This method, in turn, calls the RegisterRoutes() method. The RegisterRoutes() method creates the route table.

The default route table contains a single route (named Default). The Default route maps the first segment of a URL to a controller name, the second segment of a URL to a controller action, and the third segment to a parameter named id.

## Summary
The goal of this tutorial was to provide you with a brief introduction to ASP.NET Routing. We examined the default route table that you get with a new ASP.NET MVC application. You learned how the default route maps URLs to controller actions.

## Routing in ASP.NET Core
Routing is responsible for matching incoming HTTP requests and dispatching those requests to the app's executable endpoints. Endpoints (Links to an external site.) are the app's units of executable request-handling code. Endpoints are defined in the app and configured when the app starts. The endpoint matching process can extract values from the request's URL and provide those values for request processing. Using endpoint information from the app, routing is also able to generate URLs that map to endpoints.

## Routing basics
All ASP.NET Core templates include routing in the generated code. Routing is registered in the middleware (Links to an external site.) pipeline in Startup.Configure.

### Endpoint

The MapGet method is used to define an endpoint. An endpoint is something that can be:

- Selected, by matching the URL and HTTP method.
- Executed, by running the delegate.
Endpoints that can be matched and executed by the app are configured in UseEndpoints. For example, MapGet (Links to an external site.), MapPost (Links to an external site.), and similar methods (Links to an external site.) connect request delegates to the routing system. Additional methods can be used to connect ASP.NET Core framework features to the routing system:

- MapRazorPages for Razor Pages
- MapControllers for controllers 
- MapHub<THub> for SignalR 
- MapGrpcService<TService> for gRPC 

### Endpoint metadata
In the preceding example, there are two endpoints, but only the health check endpoint has an authorization policy attached. If the request matches the health check endpoint, /healthz, an authorization check is performed. This demonstrates that endpoints can have extra data attached to them. This extra data is called endpoint metadata:

- The metadata can be processed by routing-aware middleware.
- The metadata can be of any .NET type.
## Routing concepts
The routing system builds on top of the middleware pipeline by adding the powerful endpoint concept. Endpoints represent units of the app's functionality that are distinct from each other in terms of routing, authorization, and any number of ASP.NET Core's systems.

 ## ASP.NET Core endpoint definition
An ASP.NET Core endpoint is:

- Executable: Has a RequestDelegate (Links to an external site.).
- Extensible: Has a Metadata (Links to an external site.) collection.
- Selectable: Optionally, has routing information (Links to an external site.).
- Enumerable: The collection of endpoints can be listed by retrieving the EndpointDataSource (Links to an external site.) from DI (Links to an external site.).
### URL matching
- Is the process by which routing matches an incoming request to an endpoint (Links to an external site.).
- Is based on data in the URL path and headers.
- Can be extended to consider any data in the request.
## URL generation concepts
URL generation:

- Is the process by which routing can create a URL path based on a set of route values.
- Allows for a logical separation between endpoints and the URLs that access them.
Endpoint routing includes the LinkGenerator (Links to an external site.) API. LinkGenerator is a singleton service available from DI (Links to an external site.). The LinkGenerator API can be used outside of the context of an executing request. Mvc.IUrlHelper (Links to an external site.) and scenarios that rely on IUrlHelper (Links to an external site.), such as Tag Helpers (Links to an external site.), HTML Helpers, and Action Results (Links to an external site.), use the LinkGenerator API internally to provide link generating capabilities.
