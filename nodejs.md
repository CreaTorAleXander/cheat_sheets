### nodejs
really helpful http://qnimate.com/express-js-middleware-tutorial/#prettyPhoto

#### route Handler
Route is used to handle a HTTP request. Route is a combination of a path and callback, which is executed when a request's path is mathches, The callback is called as the route handler.

Every root handler get a reference to the request and response object of the HTTP request that is currently beeing served.

#### next() usage
there can be multiple route handlers exectured for a single http request

```
var app = require("express")();

app.get("/", function(httpRequest, httpResponse, next){
    httpResponse.write("Hello");
    next();
});

app.get("/", function(httpRequest, httpResponse, next){
    httpResponse.write(" World !!!");
    httpResponse.end();
});

app.listen(8080);

``` 

In the example above first handle writes some response and then calls *next()*. The *next()* method is used to call the next route handler math the route path.


#### important
A route handler must end the request or call the next route handler

It is also possible to pass multiple route handlers to a single call to ... methods. Here is an example


```
var app = require("express")();

app.get("/", function(httpRequest, httpResponse, next){
    httpResponse.write("Hello");
    next();
}, function(httpRequest, httpResponse, next){
    httpResponse.write(" World !!!");
    httpResponse.end();
});

app.listen(8080);

```

#### Middleware

Middleware is those methods/functions/opeartions that are called between processing the request and sending the response in your application method.

##### <code>express.json()</code> & <code>express.urlencoded</code>

When talking about these we specificially think about POST requests or PUT Request

##### Why do we need them?

When you receive POST and PUT requests on your backend in both you receive data from a form for example. Now the server is asked to accept or store that data (object), which is enclosed in the body of that Request. 

<code>express.json()</code> is a method inbuilt in express to recognize the incoming Request Object as a JSON Object.
<code>express.urlencoded()</code> is a method inbuilt in express to recognize the incoming Request Object as strings or arrays

With these you can now limit what kind of request you can parse.

For example:

express.json({limit: '1mb}) only allows payload up to 1mb.

Middleware name meaning is good to explain with the example below.
The first two defined route handler are called as middleware because they are not handling the request rather for pre-processing of the request.


```
app.get("/*", function(httpRequest, httpResponse, next){
    logRequest();
    next();
})

app.get("/*", function(httpRequest, httpResponse, next){

    if(checkLogin())
    {
        next();
    }
    else
    {
        httpResponse.send("You are not logged in!!!");
    }
})
```