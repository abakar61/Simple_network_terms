# What is a Client?

A **client** is a computer, mobile device, or software application that **requests services, data, or resources from a server** over a network. Clients are commonly used in both **home** and **business (corporate)** networks.

Common examples of clients include:

* Desktop computers
* Laptops
* Smartphones
* Tablets
* Web browsers (Google Chrome, Firefox, Edge)

## How a Client Works

A client cannot always perform every task by itself. When it needs information or a service, it sends a **request** to a server. The server processes the request and sends back a **response**.

The client and server may:

* Be on the **same computer**.
* Be on **different computers** connected through a local network (LAN).
* Be connected over the **Internet**.

## Client-Server Communication

Clients and servers communicate using the **request-response model**:

1. The client sends a request.
2. The server receives the request.
3. The server processes the request.
4. The server sends a response.
5. The client displays or uses the received data.

```
Client
   │
   │ Request
   ▼
Server
   │
   │ Process Request
   ▼
Response
   │
   ▼
Client
```

## Communication Protocols

To exchange data correctly, clients and servers use communication protocols. One of the most common is **TCP/IP (Transmission Control Protocol/Internet Protocol)**.

TCP/IP is responsible for:

* Establishing communication between the client and server.
* Transferring data reliably.
* Detecting and retransmitting lost data packets.
* Ensuring data arrives in the correct order.

## Resources Provided by Servers

A server can provide many types of resources, including:

* Web pages
* Files
* Databases
* Internet access
* Cloud storage
* Applications
* Processing power

## Client-Side vs Server-Side

### Client-Side

Client-side operations run on the user's device.

Examples:

* Web browsers
* HTML
* CSS
* JavaScript

### Server-Side

Server-side operations run on the server.

Examples:

* Database queries
* User authentication
* File storage
* API processing
* Business logic

## Real-World Example

When you open **Google Chrome** and visit **[www.google.com](http://www.google.com)**:

1. Chrome (the client) sends a request.
2. Google's web server receives the request.
3. The server processes it.
4. The server sends the webpage back.
5. Chrome displays the webpage on your screen.

## Key Points

* A **client requests** services or resources.
* A **server provides** services or resources.
* Clients and servers communicate using the **request-response model**.
* Communication usually happens through **TCP/IP**.
* Client-side tasks run on the user's device, while server-side tasks run on the server.
* Common clients include computers, smartphones, tablets, and web browsers.
