## What is NodeJS
NodeJs is a JavaScript runtime built on google's open-source V8 JavaScript engine.

NodeJS is just another JavaScript Runtime, It is just like a container, like an environment in which the program written in JavaScript can be executed, but outside of any browser whatsoever.

JavaScript Code will be parsed and run in google's V8 Engine.

#### JavaScript On the server
Now we can use JavaScript on the server-side of web development.
In order to build fast, highly scalable network applications (back-end).

NodeJS ->
* NodeJS is single-threaded, based on event drive, non-blocking I/O model.
* Node is perfect for building **fast** and **scalable** data-intensive apps.
* 

NodeJS Use ->
 * API with database behind it (preferably No SQL).
 * Data streaming (think YouTube).
 * Real-time chat application.
 * Server-side web application.
 * Companies like: netflix, uber, paypal, ebay have started using node in production;
 * **JavaScript across the entire stack**: faster and more efficient development;
 * **NPM**: Huge library of open-source packages available for everyone for free;
 * **Very active** developer community

NodeJS Don't Use -> 
* Applications with heavy server-side processing (CPU-intensive)
* USE -> PHP, PYTHON.

## Synchronous & Asynchronous Code
**Synchronous** -> Synchronous code means that each statement is executed one after another in a sequential manner. Each line of code waits for the previous line to complete before it executes.

In simple terms, the execution is blocked until the current operation finishes. A certain operation can only be executed after the one before it has finished.

**Asynchronous** -> Asynchronous code allows certain tasks to be processed in the background, enabling other code to execute simultaneously without being blocked by heavy or time-consuming tasks.

Once an asynchronous task is complete, it triggers a mechanism (such as a callback function, promise, or async/await) to handle the result/value. This way, we can perform other operations while waiting for the asynchronous task to finish, making the overall process more efficient.

## Creating a server 
To create a server we first have to import the HTTP module, which gives object full of methods and variety of properties.

Then after we imported HTTP module, we use **`.createServer()`** method of that object. That method takes an callback function as an argument.

That callback function has two parameters first one is the request object and the second one is the response object.

**The callback function, which we provided to the `createServer()` method as an argument, will run every time there is a request.** 
In short that callback function runs for every request that is coming from the website

## Sending Responses
Easiest way to send the response back to the user, would be to use the **response** objects method called **`.end()`**. It takes 1 argument and it is what we want to send back. It could be text or html template, id does not matter. 

## Writing Headers
We use headers to provide detailed information about the type of data being sent or received.Headers are essential components of data transmission protocols, such as HTTP, SMTP, and FTP. They accompany each data packet and contain metadata that helps both the sender and the receiver interpret the content accurately.

In the context of web development and HTTP requests, headers play a crucial role in facilitating communication between clients (such as web browsers) and servers. For instance, the "Content-Type" header specifies the media type of the content being sent, allowing the recipient to interpret it correctly. Similarly, headers like "Content-Length" indicate the size of the content, enabling efficient data transfer.

Headers can also convey additional information beyond the content itself. For example, HTTP headers may include "Cache-Control" directives to control caching behavior, "Authorization" headers for authentication purposes, and "User-Agent" headers to identify the client making the request. 

In summary, headers serve as metadata containers that enhance the reliability, security, and efficiency of data transmission by providing contextual information about the data being exchanged.

We have the ability to create our own headers as well. This means we are not limited to just using the predefined ones provided by protocols like HTTP. By defining custom headers, we can imbue our data transmissions with personalized metadata and instructions tailored specifically to our application's needs.

For instance, imagine you're developing a web service for a real-time messaging app. You might create custom headers to include timestamps, message priorities, or even unique identifiers for tracking message delivery. These custom headers can enhance the functionality of your application, allowing you to implement features like message queuing, message routing, or even message encryption.

In essence, creating custom headers grants us the freedom to extend the capabilities of our communication protocols beyond their standard functionalities. It's akin to adding custom labels to packages we send, ensuring they reach their destination exactly as we intend, with all the necessary information included

We write headers using **`.writeHead()`** method of the response and request objects. 

**`writeHead(statusCode, headersObject)`** write head takes two arguments:
* Status Code -> Firs is the status code it could be 200(OK) or 404(Not Found) any status code, depending on the situation.
* Headers Object -> We give and object which contains a collection of information about the data we are sending or receiving.(headers) 

```javascript
const http = require("http")

const server = http.createServer((request,respsone) => {
	res.writeHead(200, {
	"Content-Type": "text/html", // application/json
	"my-own-header": "hello-world", // Our own created header/Custom header
	})
	res.end("This is a response");
})
```


## Listening to responses
In order for us to listen for request/connections, we have to use **`.listen()`** method, which is a method accessible on our created server object. 

**`listen(portNumber, hostName, callBackFunction)`** Listen method takes 3 arguments: 
* Port Number -> The port we want our server to run.
* Host Name -> The host name we want our server to have.
* CallBack Function -> A callback function that will run every time we start a server.

```javascript
const server = http.createServer((req,res) => {})

server.listen(8000,"127.0.0.1", () =>{
	console.log("Listening to requests on port 8000");
})
```

## An Overview of How the Web Works
### What Happens when we access a web page
Request-response model/Clint-server architecture -> Our browser which is also called a client, sends a **request** to the server where the web page is hosted and a server will then send back a **response**, which is going to contain a web page that we just requested.    

### URL
`https://www.google.com/maps` 
Every URL gets a HTTP or HTTP protocol, then we have a domain name, which is google.com in this case. Also after the slash a so called resource that we want to access, In this case /maps.

google.com Is not a real address of the website, we convert the real IP address to the domain name using DNS(Domain Name Server).

DNS -> DNS is a special servers which are basically like the phone books of the internet.

DNS lookup -> When we open up the browser at first it makes a request to a DNS, and this special server will then simply match the web address that we type in to the browser to the servers real IP address. 
This happens through our internet service provider(ISP.

Domain is not a real address and the DNS will convert it to that real IP address.

Real IP Address -> `https://216.58.211.206:443`
 * Protocol (HTTP or HTTPS)
 * IP address
 * Port Number (Default 443 for HTTPS, 80 for HTTP) 

So once we have a real web address a TCP/IP socket connection is established between browser and a server, which are now finally connected, and this connection is typically kept alive for the entire time it takes to transfer all the files of the website.

**TCP** -> TCP Is transmission control protocol. the Job of TCP is to break up requests and responses into a thousands of small chunks called packets before they are set. Then once they get to their destination it will reassemble all the packets into the original request or response.  

**IP** -> IP is internet protocol. The Job of the IP protocol is to actually send and route all of these packets through the internet, so it ensures that all of them arrive at the destination that they should go using IP addresses on each packet. 

**TCP/IP** protocols and together they are communication protocols that define exactly how data travels across the web. They are the ones who set the rules about how data moves on the internet. 

**Communication Protocol** -> A communication protocol is simply a system of rules, that allows two or more parties to communicate.

**HTTP Request** -> Is just a protocol that allows clients and web servers to communicate by sending requests and response messages from client to server and back.

A request message will look something like this:
```HTTP Request  
GET /maps HTTP/1.1 # <- Start line: HTTP Method + Request target + HTTP Version

# Headers -> HTTP Request headers (many different possibilities)
Host: www.google.com  #
User-Agent: Mozilla/5.0
Accept-Language: en-US

<BODY> # <- Request Body (Obly when sending data to server, e.g. POST)
```

* Start line -> HTTP Method + Request target + HTTP Version.
* Headers -> Headers just hold some information that we send about the request itself. Information about the Request itself.
* Request Body (BODY) -> In Case we are sending data to the server there will also be a request body, containing that data. E.g. (HTML FORM). **Contains the data**, that we send to the server.

HTTP methods: 
* **GET** -> To simply request data.
* **POST** -> To send data.
* **PUT** -> To modify data.
* **PATCH** -> To modify data.

**HTTP Response** -> When our request hits(arrives to) the server, which will be working on it until it has our site ready to send back, and it will send it back using HTTP response. 

A response message will look something like this:
```HTTP Response
HTTP/1.1 200 OK # <- Start Line: HTTP version + status code + status message

# Headers # <-  HTTP Response headers (many different possibilities)
Date: Fri, 18 Jan 2021
Content-Type: text/html
Transfer-Encoding: chunked

<BODY> # <- Response Body (most responses)
```

* Start Line -> HTTP version + status code + status message.
* Headers -> Information about the response itself.
* Response Body(BODY) -> **Contains the date**, that we send back to the client.

## Processes Threads and the Thread Pool
When we use node on a computer it means, that there is a node process running on that computer. 

In that process nodejs runs in a so called single thread, a thread is basically just a Sequence of Instructions. 

When the program is initialized, all the "top-level" level code is executed, which means all the code, that is not inside of any callback function. 
Also all the modules, that our app needs are required and all the callback functions are registered. 
Then, After all of this, the event loop finally starts running. 

Sometimes some tasks are actually too heavy, they are too expensive to be executed in the event loop, because they would then block the single thread, and so that is where the **thread pool** comes in, which just like event loop is provided in nodejs by libuv library.  

**Thread Pool** gives us 4 additional threads(or more), that are completely separate from the main single thread. This threads together form a thread pool, and the event loop can then automatically offload heavy("expensive") tasks to the thread pool. 
All of this happens automatically behind the scenes.

* Additional 4 threads (or more).
* Offload work(heavy tasks) from the event loop 
* Handle heavy ("expensive") tasks:
	* File system APIs
	* Cryptography
	* Compression
	* DNS Lookups

NodeJS Process -> Instance of a program in execution on a computer.

**Thread** -> Is a  Sequence of Instructions.

## Event Loop
**Event Loop** -> All the application code that is inside of **callback 
functions** (non-top-top-level code).

**NodeJS** is build around **callback functions**.

Event loop is where all the application code that is inside of callback functions is executed. Basically all code that is not top level code will run in the event loop. Some parts might get offloaded to the thread pool. But it is the event loop that takes care of all this. 

NodeJS is all build around callback functions, so functions that are called as soon as some work is finished, sometime in the future.

Node uses an Event-Driven architecture.

Things like our application receiving and HTTP request on our server, or timer expiring, or a file finished to read, all this will emit events as soon as they are done with their work. 
Event loop will then pick up this events and call the callback functions  that are associated with each event.

The Event Loop receives events each time something important happens and will then call the necessary callbacks such as we define in our code. In summary, Event Loop receives events, calls their callback functions and offloads the more heavy(expensive) tasks to the thread pool.

### The Event Loop In Detail
When we start our node application, the event loop starts running right away. 

**Event Loop** -> The Event Loop is a core concept in JavaScript's runtime (like Node.js) for handling asynchronous operations. It allows JavaScript to perform non-blocking operations by offloading operations to the system kernel whenever possible.

Event Loop has multiple phases, and each phase has a callback queue, which are the callbacks coming from the events that the event loop receives. 

### First phase
So the first phase takes care of callbacks of expired timers.

```javascript
setTimeout(() => {
console.log("Timer Expired!");
});
```

If there are callback functions from timers that just expired this are the first ones to be processed by the event loop. If the timer expires later during the time when one of the other phases are being processed, then the callback of that timer will only be called as soon as event loop comes back to this first phase.

This works like this in all four phases. So, callbacks in each queue are processed one by one until there are no ones left in the queue. Only then, the event loop will enter the next phase.

### Second Phase
Next, we have I/O polling and execution of I/O callbacks.

So, polling basically means looking for new I/O Events, that are ready to be processed, and putting them into the callback queue.

I/O stands for input/output.

```javascript
fs.readFile("file.text", (e,d) => {
console.log("Fole Read!");
});
```

### Third Phase
The next phase is for `setImmediate` callbacks and `setImmediate` is a special kind of timer that we can use if we want to process callbacks immediately, after the I/O Polling and execution phase.

### Forth Phase
The Forth phase is for close callbacks, Basically, in this phase, all close events are processed. E.g. When a web server or a Web Socket shut down.

 
Event Loop phases:
1. Expired timer callbacks.
2. I/O Polling and execution of I/O Callbacks.
3. `setImmediate` callbacks.
4.  Close callbacks

There are actually also two other queues:
* PROCESS.NEXTTIC() QUEUE
* OTHER MICROTASKS QUEUE (Resolved Promises)

**PROCESS.NEXTTIC() QUEUE** -> 

**OTHER MICROTASKS QUEUE (Resolved Promises)** -> Mainly for Resolved Promises

If there are any callbacks in one of these two queues to be processed they will be executed right after the current phase of the event loop finishes instead of waiting for the entire loop to finish.

In other words, after each of these four phases, if there are any callbacks in these two special queues they will be executed right away.  
E.g. Let's imagine that a promise resolves and returns some data from an API call while the callback of an expired timer is running, So In this case, the promise callback will be executed right after the one from the timer finishes.

```javascript
somePromise.then((data) =>{
console.log("Recieved Data!");
});
```

The same logic also applies to the `nextTick()` queue.
So basically, `Process.nextTick()` is a function, that we can use when we really, really need to execute a certain callback right after the current event loop phase.

All right, and with this, we actually finished one tick of the event loop, and a tick is basically just one cycle in this loop. 
So, now it is time to decide whether the loop should continue to the next tick or if the program should exit.

Node simply checks whether there are any timers, or I/O tasks that are still running in the background and if there aren't any then it will exit the application, But if there are any pending timers or I/O tasks well, the it will continue running the event loop and go straight to the next tick(cycle).  

**Tick** -> A tick is one complete cycle through the phases of the Event Loop, during which it processes available events and executes callbacks.

We should not block the event loop, it is our responsibility:
* Don't use **sync** versions of  functions in fs, crypto and zlib modules is your callback functions.
* Don't perform complex calculations (e.g loops inside loops).
* Be careful with JSON in large objects.
* Don't use too complex regular expressions (e.g nested quantifiers).

Event Loop actually waits for stuff to happen in the poll phase, so in that phase where I/O Callbacks are handled. So when this queue of callbacks is empty, so when we don't have any I/O callbacks, then the event loop will wait in this phase until there is an expired timer, but if we scheduled a callback using `setImmediate()` then that callback will actually be executed right away after the polling phase and even before expired timers, if there is one.

### Summary
The event loop is what makes the asynchronous programming possible in nodejs. It takes care of all incoming events and performs orchestration by offloading heavier tasks into the thread pool, and doing the most simple work itself, Also we need the event loop, because in nodejs everything works in one single thread. 


## Events and EventDriven Architecture
### The Event-Driven Architecture
Most of nodes core modules, are built around an event-driven architecture, and we can of course also use this architecture to our advantage in our own code.

So in node there are certain objects called **event emitters**, that emit named events as soon as something important happens in the app, like request hitting server or a timer expiring or a file finishing to read. These events than can be picked up by event listeners that we developers set up which will fire off callback functions that are attached to each listener. 

**Event Emitter(s)** -> Certain object(s), which emit named events as soon as something important happens in the app. Event Emitters can emit named events and we can then subscribe to this events, so basically listen to them, and then react and handle accordingly.

So again, on one hand we have event emitters, and on the other hand event listeners that will react to emitted events by calling callback functions.

```javascript
const server = http.createServer();
server.on("request", (req,res) => {
	console.log("Request Received");
	res.end("Request Received");
});
```

This Event Emitter logic is called the **Observer Pattern** in JavaScript programming in general. 

The idea is that there is an observer in this case an event listener, which keeps waiting, keeps observing the subject that will eventually emit the event that the listener is waiting for, and the opposite of this pattern is simply functions calling other function. 
Observer pattern has been designed to react rather than to call(invoke).

Event Emitters can emit named events and we can then subscribe to this events, so basically listen to them, and then react and handle accordingly. 

## Introduction to Streams
### What are Streams
**Stream** -> Streams are used to process (Read and Write) data piece by piece (Chunks), without completing the whole read or write operation, and therefore without keeping all the data in memory.

* This makes streams Perfect for handling larger volumes of data, for example videos.
* Also Streaming makes data processing more efficient in terms of memory (no need to keep all data in memory) and time (We don't have to wait until all the data is available).

### Node.JS  Streams Fundamentals
So in node there are 4 fundamental types of streams.
* Readable Streams
* Writable Streams
* Duplex Streams 
* Transform Streams

**Streams are actually instances of the `EventEmitter` class**. 
Meaning that all streams can **emit** and **listen** to named Events.
#### Readable Streams
**Readable Streams** -> Readable Streams are the ones from which we can read data, we can consume data.

##### Example:
* HTTP Requests
* fs read streams

##### Important Events
* data -> emitted when there is a new piece of data to consume.
* end -> emitted as soon as there is no more data to consume.

##### Important Functions
* `pipe()`
* `read()`

#### Writable Streams
**Writable Streams** -> Writable Streams are the ones to which we can write data, so basically the opposite of readable streams.

##### Example:
* HTTP Responses
* fs write streams

##### Important Events
* drain 
* finish 

##### Important Functions
* `write()`
* `end()`

#### Duplex Streams
**Duplex Streams** -> Duplex Streams are simply Streams that are both readable and writable at the same time.

##### Example:
* net web socket

#### Transform Streams
**Transform Streams** -> Transform Streams are Duplex streams, which at the same time can modify or transform the data as it is read or written.

##### Example:
* zlib Gzip creation

## What is an API?
**API(Application Programming Interface) -> a piece of software that can be used by another piece of software, in order to allow applications to talk to each other.

But, "Application" can be other things:
* Node.js' fs or HTTP APIs("Node APIs).
* Browser's DOM JavaScript API.
* With object-oriented programming, when exposing methods to the public, we're creating an API. 

### The REST Architecture
**REST** -> which stands for Representational States Transfer is basically a way of building web APIs in a logical way making them easy to consume.

To build Restful APIs, which means APIs following the REST Architecture, we just need to follow a couple of principles.

1. We need to separate our API into logical resources. 
2. these resources should then be exposed, which means to be made available using structured, resource-based URLs, To perform different actions on data, like reading or creating or deleting data.
3. The API should use the right HTTP methods and not the URL.
4. The data that we actually send back to the client or that we received from the client, should usually use the JSON data format. Where some formatting standard applied to it.
5. They must be stateless.

The key abstraction of information in REST is a resource and therefore all the data that we want to share in the API should be divided into logical resources.

**Resource** -> In the context of REST, **Resource** is an object or a representation of something, which has some data associated to it. Any information that can be **named** can be a resource

Now we need to expose, which means to make available the data using some structured URLs, that the client can send a request to. For example, something like this `https://www.natours.com/addNewTour`.
Endpoints should **only contain resources** and not the actions that can be performed on them. 

Endpoints should contain **only resources**(nouns) and use **HTTP Methods** for actions!

The data that the client actually receives or that the server receives from the client, usually, we use the JSON data format.

JSON is a very lightweight data interchange format, which is heavily used by web APIs coded in any programming language. 

JSON looks like a regular JavaScript object, with all these **key-value pairs**.
* All the keys have to be strings. 
```json
{
	"id": 5, // String and Value
	"tourName": "The Park Camper", // key-value pair
	"rating": "4.9", // key-value pair
	"guides": [  // Array
		{ // object
			"name": "Steven Miller",
			"role": "Lead Guide",
		},
		{ // object
			"name": "Lisa Brown",
			"role": "Tour Guide"
		}
	]
}
```

A Restful API should always be **stateless**.
**Stateless** -> in a stateless Restful API, All state is handled on the client. This means that each request must contain **all** the information necessary to process a certain request. The server should **not** have to remember previous request.

**State** -> State simply refers to a piece of data in the application that might change over time. 
For Example, whether a certain user is logged in, or on a page with a list with several pages what the current page is.

State should be handled on the client means that each request must contain all the information that is necessary to process a certain request on the server. The server should never ever have to remember  the previous request in order to process the current request.

## The Essence Of Express Development: The Request-Response Cycle
The request-response cycle or express app receives a request when someone hits a server for which it will then create a request and response objects, that data will then be used and processed in order to generate and send back a meaningful response. 

In order to process that data, in express we use something called middleware. Which can manipulate the request or the response object, or really execute any other code that we like. So middleware doesn't always have to be just about the request or the response object, but it usually is mostly about the request.

### Middleware 
**Hook ===  Middleware**
**Middleware** -> It is called middleware, because it is a function that is executed between, so in the middle of receiving the request and sending the response.

All the middleware together, that we use in our app is called middleware stack.

The order of middleware in the stack is actually defined by the order they are defined in the code. So a middleware that appears first in the code is executed before on that appears later.

We can think of whole process like this, our request and response objects, that were created in the beginning go through each middleware where they are processed or where just some other code is executed, then at the end of each middleware function a `next()` function is called, which is a function that we have access to in each middleware function, just like the request and response objects.

When we call the `next()` function, the next middleware in the stack will be executed with the exact same request and response objects. That happens with all the middlewares, until we reach the last one.

The last middleware function is usually a route handler, so in this handler we do actually not call the `next()` function to move to the next middleware, instead we finally send the response data back to the client. Like this we finished so called request-response cycle. 

## Environment Variables 
**Environment Variables** -> Environment variables are global variables that are used to define the environment in which a node app is running. 

## MongoDB
### MongoDB: An Overview
**MongoDB** -> Is obviously a database, and it is so called no **sequel(NoSQL)**.

In Mongo each database can contain one or more collections. Then, each collection can contain one or more data structures called documents. So each document contains the data, about one single entity.
For example: 
* One blog post or one user or one review.   

Now the collection is like the parent structure, that contains all of these entities. 
For example: 
* A blog collection for all posts. 
* A users collection or a reviews collection.

### What Is MongoDB?
**MongoDB** -> MongoDB is a document database with the scalability and flexibility that you want with the querying and indexing that you need.

 * **Document Based** -> MongoDB stores data in documents(field-value data structures, NoSQL).
 * **Scalable** -> Very easy to distribute data across multiple machines as your users and amount of data grows.
 * **Flexible** -> No document data schema required, so each document can have different number and type of fields.
 * **Performant** -> Embedded data models, indexing, sharding, flexible documents, native duplication, etc.

MongoDB stores data in documents, which are field-value paired data structures like JSON.

Also, MongoDB has built-in scalability making it very easy to distribute data across multiple machines as your apps get more and more users and starts generating a ton of data. 

Another great feature of MongoDB is its flexibility, So there is no need to define a document data schema, before filling it with data, meaning that each document can have a different number and type of fields. We can also change these fields all the time.

MongoDB is also a very performant database system. Thanks to features like embedded data models, indexing, sharding, the flexible documents, native duplication and more.

**BSON** -> Data Format MongoDB uses for data storage, Like JSON **but typed**So MongoDB documents are typed

**Embedding/Denormalizing** -> Including related data into a single document. This allows for quicker access and easier data models (it is not always the best solution though).

## What Is Mongoose, and why use it?
**Mongoose** -> Mongoose is an **Object Data Modeling (ODM)**  library for MongoDB and Node.js, providing a higher level of abstraction.

**Object Data Modeling (ODM)** -> Object data modeling library is just way for us to write JavaScript code, that will then interact with a database. 
* Mongoose allows for rapid and simple development and MongoDB database interactions.
* Features: schema to model data and relationships, easy data validation, simple query API, middleware, etc.

 **Mongoose Schema** -> A Schema is Where we model our data, by describing the structure of the data, default values, and validation.
 **Mongoose model** -> A wrapper for the schema, providing an interface to the database for CRUD operations.
**SCHEMA -> MODEL**

## Application VS Business Logic
### **Application Logic**:
* Code that is only concerned about the application's implementation, not the underlying business problem we are trying to solve (e.g. showing and selling tours).
* Concerned about managing request and responses.
* About the app's more technical aspects.
* Bridge between model and view layers.

### **Business Logic**:
* Code that actually solves the business problem we set out to solve.
* Directly related to business rules, how the business works, and business needs.
* Examples: 
	* Creating new tours in the database.
	* Checking if user's password is correct.
	* Validating user input data.
	* Ensuring only users who bought a tour can review it.

**Fat models/thin controllers** -> offload as much logic as possible into the models, and keep the controllers as simple and lean as possible

## Aggregation
**Aggregation** -> Aggregation operations process data records and return computed results. Aggregation operations group values from multiple documents together, and can perform a variety of operations on the grouped data to return a single result. 

MongoDB provides three ways to perform aggregation:
* The aggregation pipeline.
* map-reduce function.
* single purpose aggregation methods.

## Error Handling In Express: An Overview
**ERROR** === **EXCEPTION**

In Express, there can occur two types of errors: 
* **Operational Errors** -> Operational errors are problems, that we can predict will inevitably happen, at some point in the future and we just need to handle them in advance. They have nothing to do with bugs in our code, instead , they depend on the user, or the system or the network.
	* Invalid path accessed.
	* Invalid user input(validator error from mongoose).
	* Failed to connect to server.
	* Failed to connect to database.
	* Request timeout.
	* Etc...

* **Programming Errors** -> Programming Errors are simply bugs that we developers introduce into our code.
	* Reading properties on `undefined`.
	* Passing a number where an object is expected.
	* Using `await` without `async`.
	* Using `req.query` instead of `req.body`.
	* Etc...

**Operational Errors** -> Problems that we can predict will happen at some point, so we just need to handle them in advance.

**Programming Errors** -> Bugs that we developers introduce into our code. Difficult to find and handle.

## How JSON Web Token (JWT) Authentication Works
**JSON Web Tokens (JWT)** -> So JSON Web Tokens are a stateless solution for authentication. So there is no need to store any session state on the server, which of course is perfect for restful APIs.

Restful APIs should always be stateless.

Most widely used alternative to authentication with JWTs is to just store the user's log-in state on the server using sessions, But that of course does not follow the principle, that says, that restful APIs should be stateless, and that is why we are opting for a solution like JWTs.

Assuming we already have a registered user in our database, this is how a user logs into the app -> So the user's client starts by making a post request with the **username** or **email** and the **password**. The application then checks if the user exists, and if the password is correct, and if so, a unique JSON Web Token, for only that user is created using a secret string, that is stored on a server. 

JWT itself is really just a string, that looks something like this:
* `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxMjMsInVzZXJuYW1lIjoiam9obl9kb2UiLCJleHAiOjE2ODI2MzQ4MDB9.cJkLqz1FJ_w8VBhEuSjmpt5xG-YhSZDpGLJxCQYV4s8`


The server then sends that JWT back to the client, which will store it either in a cookie or in local storage, and just like this the user is authenticated, and basically logged into our application. Without leaving any state on the server. 
So the server does in fact not know, which users are actually logged in, but of course, the user knows that he is logged in, because he has a valid JSON Web Token, which is a bit like a passport to access protected parts of the application.

A user is logged in as soon as he gets back his unique valid JSON Web Token, which is not saved anywhere on the server, and so this process is therefore completely stateless, then, each time a user wants to access a protected route, like his user profile data, for example, he sends his JSON Web Token along with a request.

So it is a bit like showing his passport to get access to that route.

Now once the request hits the server, our app will then verify if the JSON Web Token is actually valid, So if the user is really who he says he is, if the token is actually valid, then the requested data will be sent to the client, and if not, then there will be an error telling the user, that he is not allowed to access that resource, and as long as the user is logged in, this is how it is gonna work each time that he requests data from any protected route.

All this communication must happen over **HTTPS** in order to prevent, that anyone can get access to passwords or JSON Web Tokens. 

### What A JWT Looks Like
So a JSON Web Token looks like this:
* Encoded ->
```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxMjMsInVzZXJuYW1lIjoiam9obl9kb2UiLCJleHAiOjE2ODI2MzQ4MDB9.cJkLqz1FJ_w8VBhEuSjmpt5xG-YhSZDpGLJxCQYV4s8
```

* Decoded ->
```json
{ 
	"user_id": 123, 
	"username": "john_doe", 
	"exp": 1684329076 
}  
```

So essentially, it is an encoding string made up of three parts: 
* **Header** 
* **Payload**
* **Signature** 

**Header** -> The header is just some metadata about the token itself.

**Payload** -> The payload is the data that we can encode into the token, any data really that we want. So the more data we want to encode here, the bigger the JWT. 

**Signature** -> The signature is created using the header, the payload and the secret that is saved on the server. 

**Header** and **Payload** are just plain text, that will get encoded, but not encrypted.

So anyone will be able to decode them and to read them, so we can't store any sensitive data in here, but that's not a problem at all, because in the **Signature** is where things really get interesting. 
The signature is created using the header, the payload and the secret that is saved on the server. This whole process is then called signing the JSON Web Token.


### How Signing and Verifying Works
So the signing algorithm takes the header, the payload and the secret(which is stored on the server) to create a unique signature. So only this data plus the secret can create this signature. 

Then together with the header and the payload, these signature forms the JWT, which then gets sent to the client. 

Once the server receives a JWT to grant access to a protected route, it needs to verify it, in order to determine if the user is really is who he claims to be. 
In other words, it will verify if no one changed the header and the payload data of the token. 

So this verification step will check if no third party actually altered either the header or the payload of the JSON Web Token.

### How does this verification actually work?
So once the JWT is received, the verification will take its header and payload and together with the secret that is still saved on the server, basically create a test signature, but the original signature that was generated, when the JWT was first created is still in the token, and that is the key for this verification, Because now all we have to do is to compare the test signature with the original signature, and if the test signature is the same as the original signature, then it means that the payload and the header have not been modified. 
If they had been modified, then the test signature would have to be different, therefore in this case where there has been no alteration of the data, we can then authenticate the user, and of course, if the two signatures are actually different, well, then it means, that someone tampered with the data.
Usually by trying to change the payload, but that third party manipulating the payload, does of course not have access to the secret, so they cannon sign the JWT. 

So the original signature will never correspond to the manipulated data. Therefore, the verification will always fail in this case. 
That is the key to making this whole system work.

### Summary
Without the secret, no one will be able to manipulate the JWT data, because they cannot create a valid signature for the new data. They could manipulate the data, but it will always fail the verification step.

## Security Best Practices and Suggestions
**Compromised Database**:
* Strongly encrypt passwords with salt and hash (bcrypt).
* Strongly encrypt password reset token (SHA 256).

**Brute Force Attacks**:
* Use `bcrypt` (to make login request slow).
* Implement rate limiting (`express-rate-limit`).
* Implement maximum login attempts.

**Cross-Site Scripting (XSS) Attacks**:
* Store JWT in HTTP Only cookies.
* Sanitize user input data.
* Set special HTTP headers (`helmet` package).

**Denial-Of-Service(DOS) Attack**:
* Implement rate limiting (`express-rate-limit`).
* Limit body payload (in `body-parser`).
* Avoid evil regular expressions.

**NoSQL Query Injection**:
* Use `mongoose` for MongoDB (because of Schema Types).
* Sanitize user input data.

**Other Best Practices and Suggestions**:
* Always use HTTPS.
* Create random password reset tokens with expiry dates.
* Deny access to JWT after password change.
* Don't commit sensitive config data to GIT.
* Don't send error details to clients.
* Prevent Cross-Site Request Forgery (`csurf` package).
* Require re-authentication before a high-value action.
* Implement a blacklist of untrusted JWT.
* Confirm user email address after first creating account.
* Keep User logged in with refresh tokens.
* Implement two-factor authentication.
* Prevent parameter pollution causing Uncaught Exceptions.

## Data Modeling
**Data Modeling** -> Data modeling is the process of taking unstructured data generated by a real world scenario and then structure it into a logical data model in a database.

We do that according to a set of criteria. 

### 1. Types of relationships between data
There are three big types of relationships:
* **One to One** (1:1).
* **One to Many** (1:Many).
* **Many to Many** (Many:Many).

**One to One** (1:1) -> One to one relationship between data is basically, when one field can only have one value.

**One to Many** (1:Many) -> There are three types of relationship in one to many:
* **One to Few** (1:Few) -> Just relates to a few or many relationship.
* **One to Many** (1:Many) -> Relates to hundreds or thousands of relationships.
* **One to Ton** (1:Ton) ->  Relates to millions and more relationships.

difference is based on the relative amount of the many.

 **Many to Many** (Many:Many) -> One document can have **many** relationships, but also that one document can have **many** other relationships too. Example: (One move can have many actors, but one actor can also play in many movies.)

### 2. Referencing VS Embedding
Each time we have tow related datasets we can either represent that related data in a reference or normalized or in an embedded or denormalized form.
* **Reference Dataset Form**.
* **Normalized Dataset Form**.
* **Embedded Dataset Form**.
* **Denormalized Dataset Form**.

**Referenced Dataset Form** -> In the referenced form we keep two related datasets and all the documents separated. So  again all the data is nicely separated, which is exactly what normalized means

**Embedded Dataset Form** -> 

In relational databases all data is always represented in normalized form, but in NoSQL database like MongoDB we can denormalize data into a denormalized form simply by embedding the related document right into the main document. 

### 3. When to embed and when to reference? A Practical Framework
* **1.  Relationship Type** -> How two datasets are related to each other.
* **2.  Data Access Patterns** -> How often data is read and written. Read/write ratio.
* **3. Data Closeness** -> How "much" the data is related, how we want to query.

1. First we look at the type of relationships that exists between datasets.
2. Second we try to determine the data access pattern of the dataset that we want to either embed or reference, this just means to analyze how often data is read and written in that dataset.
3. At last we look at **Data Closeness** (Term We made), it means how much the data is really related and how we want to query the data from the database.

Now to take the decision we need to combine all of these 3 criteria.

**Embedding**:
1. **Relationship Type**
	* **1:FEW**
	* **1:MANY**
2. **Data Access Patterns**
	* Data is mostly **read**. 
	* Data does **not** change quickly.
	* **High** read/write ration.
3. **Data Closeness**
	 * Datasets **really** belong together.


**Referencing**:
1. **Relationship Type**
	* **1:MANY** 
	* **1:TON**
	* **MANY:MANY**
2. **Data Access Patterns**
	* Data is **updated** a lot.
	* **Low** read/write ration.
3. **Data Closeness**
	 * We frequently need to query both dataset **on their own**.

**1. Relationship Type**
So usually, when we have **One To Few** relationship, we will always embed the related dataset, into the main dataset.

Now in a **One To Many** relationship things are a bit more complicated, so it is okay to either embed or reference.

On a **One To Ton** or **Many To Many** Relationship we usually always reference the data. That is because if we actually did embed in this case we could quickly create way too large document. So solution to that is referencing or normalizing the data.

**2. Data Access Patterns**
If the dataset that we are deciding about is mostly read and the data is not updated a lot, then we should probably embed that dataset. 

If our data is updated a lot, then we should consider referencing or normalizing the data.

So a high read/write ration just means, that there is a lot more reading than writing, So we prefer to embed.

On other hand if read/write ration is low, then we choose to reference.


**3. Data Closeness**
If the two datasets, really intrinsically belong together, then they should probably be embedded into one another.

If we frequently need to query both datasets, on their own then that is a very good reason to normalize the data into two separate datasets, even if they are closely related.

### 4. Types of Referencing
* **Child Referencing**.
* **Parent Referencing**.
* **Two-Way Referencing**.

**Child Referencing** -> In child referencing, we basically keep references to the related child documents in a parent document, and they are usually stored in an array.

However, the problem here is that this array of IDs can become very large if there are lots of children. 
This is an anti-pattern in MongoDB, So something that we should avoid at all costs. 

Also child referencing makes it so, that parents and children are very tightly coupled, which is not always ideal.

Child Referencing is best used in **1:FEW** relationships.

**Parent Referencing** -> In parent referencing, In each child document we keep a reference to the parent element, Therefore the name parent referencing.

The child always knows its parent, But in this case, the parent actually knows nothing about the children, not who they are and not how many they are.
So they are way more isolated and more standalone. 

Parent Referencing is best used in **1:MANY** and **1:TON** relationships.

**Two-Way Referencing** -> In short, Child Referencing and Parent Referencing Combined in one.

Two-Way Referencing is best used in **MANY:MANY** relationships.

### Summary
* The most important principle is: Structure your data to **match the ways that your application queries and updated data**.
* In other words: identify the question that arise from your **application's use cases** first, and then model your data so that the **questions can get answered** in the most efficient way.
* In general, **always favor embedding**, unless there is a good reason not to embed. Especially one 1:FEW and 1:MANY relationships.
* A 1:TON or a MANY:MANY relationship is usually a good reason to **reference** instead of embedding.
* Also, favor **referencing** when data is updated a lot and if you need to frequently access a dataset on its own.
* use **embedding** when data is mostly read but rarely updated, and when two datasets belong intrinsically together.
* Don't allow arrays to grow indefinitely. Therefore, if you need to normalize, use **child referencing** for 1:MANY relationships, and **parent referencing** for 1:TON relationships.
* Use **two-way referencing** for MANY:MANY relationships.