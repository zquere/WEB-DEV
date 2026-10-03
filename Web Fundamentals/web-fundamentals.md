# 🌐 Web Fundamentals

> A detailed, human-friendly guide to understanding what actually happens when you open a website.

This chapter is the foundation of the entire Web Development journey.

Before learning HTML, CSS, JavaScript, React, Node.js, databases, or any framework deeply, it is worth understanding the environment in which all of those technologies operate.

You do **not** need to become a network engineer to learn web development.

But you should be able to answer questions like:

- What actually happens when I type `google.com` into a browser?
- What is the difference between the Internet and the Web?
- What is a server?
- How does my browser find a server?
- What is DNS doing?
- What exactly is an IP address?
- What is a URL?
- What happens when an HTTP request is sent?
- What is the difference between HTTP and HTTPS?
- What are GET and POST?
- What does a `404` actually mean?
- What are headers?
- Why does a website remember that I logged in?
- What are cookies and sessions?
- Why do websites use caches?
- Why does a CDN make websites faster?
- What does "hosting a website" actually mean?
- What is SSL/TLS doing when a website uses HTTPS?

By the end of this chapter, the goal is to have a clear mental model of the web rather than a collection of definitions.

---

# 📚 Table of Contents

1. [The Big Picture](#-the-big-picture)
2. [Internet vs Web](#1-internet-vs-web)
3. [Client and Server](#2-client-and-server)
4. [Browser](#3-browser)
5. [Web Server](#4-web-server)
6. [Domain Names](#5-domain-names)
7. [DNS](#6-dns)
8. [IP Addresses](#7-ip-addresses)
9. [URLs](#8-urls)
10. [HTTP](#9-http)
11. [HTTPS](#10-https)
12. [HTTP Methods](#11-http-methods)
13. [HTTP Status Codes](#12-http-status-codes)
14. [Request / Response](#13-request--response)
15. [Headers](#14-headers)
16. [Cookies](#15-cookies)
17. [Sessions](#16-sessions)
18. [Caching](#17-caching)
19. [CDN](#18-cdn)
20. [Hosting](#19-hosting)
21. [SSL/TLS Basics](#20-ssltls-basics)
22. [Putting Everything Together](#-putting-everything-together)
23. [What Happens When You Open a Website?](#-what-happens-when-you-open-a-website)
24. [A More Realistic Example](#-a-more-realistic-example)
25. [Common Misconceptions](#-common-misconceptions)
26. [Developer Tools](#-developer-tools)
27. [Things You Should Be Able to Explain](#-things-you-should-be-able-to-explain)
28. [Practice Questions](#-practice-questions)
29. [Mini Projects / Experiments](#-mini-projects--experiments)
30. [Final Mental Model](#-final-mental-model)

---

# 🧭 The Big Picture

Let's start with the simplest possible picture.

Imagine you open your browser and type:

```text
https://example.com/products
```

A lot more happens than:

```text
Browser → Website
```

A simplified version looks like this:

```text
                    INTERNET
                        │
                        │
              ┌─────────▼─────────┐
              │      Browser      │
              │      Client       │
              └─────────┬─────────┘
                        │
                        │ DNS lookup
                        ▼
                 ┌─────────────┐
                 │     DNS     │
                 └──────┬──────┘
                        │
                        │ IP address
                        ▼
                 ┌─────────────┐
                 │ Web Server  │
                 │ / Backend   │
                 └──────┬──────┘
                        │
                        │
                 ┌──────▼──────┐
                 │  Database   │
                 └─────────────┘
```

And if HTTPS is being used, TLS is involved in establishing a secure connection before application data is exchanged.

A more complete picture is:

```text
User
  │
  ▼
Browser
  │
  ├── DNS ───────────────► Domain → IP
  │
  ├── TLS ───────────────► Secure connection
  │
  └── HTTP Request ──────► Server
                              │
                              ├── Application
                              │
                              ├── Database
                              │
                              └── Other services
                              │
                              ▼
                         HTTP Response
                              │
                              ▼
                           Browser
                              │
                              ▼
                       Rendered Web Page
```

This chapter explains every major part of that picture.

---

# 1. Internet vs Web

One of the first things you should understand is that **the Internet and the Web are not the same thing**.

They are related, but they are different concepts.

## 🌍 What is the Internet?

The **Internet is a global network of interconnected computer networks**.

It allows computers and other devices to communicate with each other.

Your:

- laptop
- phone
- server
- router
- cloud machine
- IoT device

can communicate across networks using Internet protocols.

Think of the Internet as the **infrastructure**.

A rough analogy:

```text
Internet = roads, highways, railway tracks, shipping routes, etc.
```

The Internet provides the underlying connectivity.

---

## 🌐 What is the Web?

The **World Wide Web** is a system that operates over the Internet.

Websites and web applications use technologies such as:

- HTTP
- HTTPS
- URLs
- HTML
- CSS
- JavaScript
- Web browsers
- Web servers

The Web is therefore **one service that uses the Internet**.

Other things also use the Internet:

```text
Internet
│
├── Web
├── Email
├── Online gaming
├── File transfer
├── Video calls
├── Messaging
└── Many other protocols/services
```

So:

> The Web uses the Internet, but the Internet is much bigger than the Web.

---

## 🧠 Simple analogy

Imagine a city.

The:

```text
Road network = Internet
```

And:

```text
A particular transportation service using those roads = Web
```

The roads can be used by cars, buses, ambulances, delivery trucks, etc.

Similarly, the Internet can carry many kinds of communication.

---

## ❌ Common mistake

Wrong:

> "The Internet is basically websites."

More accurate:

> Websites are part of the Web, and the Web operates using the Internet.

---

# 2. Client and Server

The client-server model is one of the most important ideas in web development.

## 💻 What is a Client?

A **client** is a device or program that requests a service or resource.

When you use a browser to open a website, the browser acts as a client.

Examples:

```text
Chrome
Firefox
Safari
Edge
Mobile applications
Command-line programs
API clients
```

The client asks another computer for something.

For example:

```text
Client:
"Give me /products"
```

---

## 🖥️ What is a Server?

A **server** is a system that provides a service or resource to clients.

For a website, a server might:

- receive requests
- run application code
- read a database
- authenticate users
- return HTML
- return JSON
- return images
- process payments
- perform calculations

The word "server" can mean both:

1. The physical/virtual machine.
2. The software running on that machine that handles requests.

That distinction matters.

---

## 🔄 Client-server communication

Basic example:

```text
Client                         Server
  │                               │
  │──── Request ────────────────►│
  │                               │
  │                               │
  │◄──── Response ───────────────│
  │                               │
```

For a webpage:

```text
Browser
   │
   │ GET /index.html
   ▼
Web Server
   │
   │ HTML
   ▼
Browser
```

---

## 🍔 Restaurant analogy

A useful mental model is a restaurant.

```text
You            → Client
Waiter         → Communication layer
Kitchen        → Server/application
Storage room   → Database/storage
Menu           → Available resources
Order          → Request
Food           → Response
```

You don't normally walk into the kitchen and directly manipulate the food.

You make a request through the appropriate interface.

Similarly, a browser doesn't normally directly manipulate a website's database.

It communicates with the server.

---

## ⚠️ Important point

A server doesn't necessarily mean a giant physical computer in a data center.

A server can be:

- a physical machine
- a virtual machine
- a container
- a cloud instance
- a serverless function
- a program running on your own computer

The important concept is the **role** it performs.

---

# 3. Browser

A browser is much more than a box where you type URLs.

A modern browser is a complex software platform that can:

- communicate over networks
- interpret HTML
- calculate CSS layouts
- execute JavaScript
- manage cookies
- store data
- enforce security rules
- display images/video
- provide developer tools
- interact with browser APIs

Examples:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

---

## 🧩 What happens inside a browser?

A simplified pipeline looks like:

```text
HTML
 ↓
Parse HTML
 ↓
DOM
 ↓
Parse CSS
 ↓
CSSOM
 ↓
Combine structure + styles
 ↓
Layout
 ↓
Paint
 ↓
Composite
 ↓
Screen
```

JavaScript can interact with the DOM and change the page while it is running.

---

## 🌳 DOM

DOM stands for:

> Document Object Model

Suppose the server sends:

```html
<h1>Hello</h1>
<p>Welcome!</p>
```

The browser turns the document into a structure that JavaScript can interact with.

Conceptually:

```text
Document
│
├── h1
│    └── "Hello"
│
└── p
     └── "Welcome!"
```

JavaScript can then do things like:

```javascript
document.querySelector("h1").textContent = "Hello World";
```

The browser updates the page.

---

## 🧠 Browser as a runtime

The browser also provides an environment for JavaScript.

JavaScript itself is a language.

The browser provides additional APIs such as:

```javascript
document
window
fetch()
localStorage
setTimeout()
```

These are not simply "JavaScript syntax."

They are capabilities exposed by the environment.

This distinction becomes important later.

---

# 4. Web Server

A web server is software designed to handle HTTP requests and return responses.

Popular web server software includes:

- Nginx
- Apache HTTP Server
- Caddy

Application runtimes such as Node.js can also be used to build HTTP servers.

---

## 📦 What can a web server return?

A server might return:

### HTML

```html
<h1>Hello</h1>
```

### CSS

```css
body {
    font-family: sans-serif;
}
```

### JavaScript

```javascript
console.log("Hello");
```

### JSON

```json
{
  "name": "Lamon",
  "age": 18
}
```

### Images

```text
photo.jpg
logo.png
```

### Other files

Almost anything can potentially be transferred over HTTP.

---

## Static vs dynamic responses

### Static

A static server might simply return an existing file:

```text
Request
  ↓
index.html
  ↓
Response
```

### Dynamic

A dynamic application may generate a response:

```text
Request
  ↓
Backend
  ↓
Business logic
  ↓
Database
  ↓
Generate response
  ↓
Client
```

For example:

```text
GET /profile
```

The backend may:

1. identify the user
2. query the database
3. retrieve profile data
4. generate JSON
5. send it back

---

# 5. Domain Names

Computers communicate using IP addresses, but humans don't want to memorize addresses like:

```text
142.250.x.x
```

So we use domain names.

Examples:

```text
google.com
github.com
example.com
```

A domain name is a human-friendly name associated with Internet resources.

---

## Domain name structure

Consider:

```text
www.example.com
```

It can be thought of as:

```text
www        → subdomain
example    → domain name
com        → top-level domain
```

The complete name is called a domain name.

---

## Top-Level Domain

Examples:

```text
.com
.org
.net
.in
.dev
.io
```

The TLD is the final part of the domain.

---

## Subdomains

A domain can have subdomains:

```text
www.example.com
api.example.com
blog.example.com
admin.example.com
```

These can be configured to point to different services.

For example:

```text
example.com
    │
    ├── www.example.com → Website
    ├── api.example.com → API
    └── admin.example.com → Admin system
```

---

# 6. DNS

DNS stands for:

> Domain Name System

DNS translates domain names into IP addresses and provides other DNS information.

A simple mental model is:

```text
Domain Name
     ↓
DNS
     ↓
IP Address
```

For example:

```text
example.com
     ↓
DNS lookup
     ↓
93.184.216.34
```

The exact address returned depends on the domain's DNS configuration and can change.

---

## 📞 DNS analogy

Think of DNS like a phone contact list.

You remember:

```text
"Mom"
```

Your phone knows the number associated with that contact.

Similarly:

```text
example.com
```

is a human-friendly identifier.

DNS provides information that helps the network locate the appropriate service.

---

## DNS hierarchy

DNS is distributed and hierarchical.

A simplified structure:

```text
                Root
                 │
       ┌─────────┼─────────┐
       │         │         │
      .com      .org      .in
       │
   example.com
       │
   www.example.com
```

---

## DNS records

DNS supports different record types.

### A

Maps a domain to an IPv4 address.

```text
example.com → 192.0.2.1
```

### AAAA

Maps a domain to an IPv6 address.

### CNAME

Creates an alias to another hostname.

### MX

Specifies mail servers.

### TXT

Stores text information used for things such as verification and email-related configuration.

### NS

Identifies authoritative name servers.

---

## DNS caching

DNS results can be cached.

Your browser, operating system, router, or DNS resolver may remember previous results.

This prevents a DNS lookup from being performed from scratch every time.

That is one reason websites can load more efficiently after the first visit.

---

# 7. IP Addresses

An IP address identifies a network interface or endpoint in an IP network.

There are two major versions:

```text
IPv4
IPv6
```

---

## IPv4

IPv4 addresses are 32 bits.

Example:

```text
192.168.1.10
```

They are commonly written as four decimal numbers.

---

## IPv6

IPv6 uses 128 bits.

Example:

```text
2001:db8::1
```

IPv6 provides a vastly larger address space.

---

## Public vs private IP addresses

### Private IP

Used inside private networks.

Examples include ranges such as:

```text
192.168.x.x
10.x.x.x
172.16.x.x – 172.31.x.x
```

These aren't generally directly reachable from the public Internet.

Your laptop may have:

```text
192.168.1.25
```

while your router has a public IP assigned by your Internet provider.

---

## Public IP

A public IP can be reachable across the public Internet, subject to routing and firewall rules.

A server hosting a public website needs an Internet-reachable path.

---

## IP vs Domain

This is important:

```text
Domain = human-friendly name

IP = network address
```

They are not the same thing.

DNS connects the two.

```text
example.com
      ↓
     DNS
      ↓
IP address
```

---

# 8. URLs

URL stands for:

> Uniform Resource Locator

A URL tells a client where a resource is located and how to access it.

Example:

```text
https://www.example.com:443/products?id=42#reviews
```

Let's break it apart.

```text
https://
   │
   └── Scheme / Protocol

www.example.com
   │
   └── Host

:443
   │
   └── Port

/products
   │
   └── Path

?id=42
   │
   └── Query string

#reviews
   │
   └── Fragment
```

---

## Scheme

```text
https://
```

The scheme tells the client which protocol or mechanism is being used.

Common examples:

```text
http
https
```

---

## Host

```text
www.example.com
```

The host identifies the destination.

It may contain:

```text
hostname
```

or sometimes an IP address.

---

## Port

Examples:

```text
http  → commonly 80
https → commonly 443
```

Ports identify services/process endpoints on a host.

A URL can explicitly specify a port:

```text
https://example.com:8443/
```

---

## Path

```text
/products
```

The path identifies a resource or route.

Examples:

```text
/
/about
/products
/products/42
/users/123/profile
```

In modern applications, a path does not necessarily correspond to a physical file.

---

## Query string

```text
?id=42&sort=price
```

Query parameters provide additional information.

For example:

```text
/products?category=laptops&sort=price
```

The server can use these values to determine what data to return.

---

## Fragment

```text
#reviews
```

The fragment is generally handled by the client/browser.

For a traditional document, it can identify a section on the page.

Example:

```text
/docs#installation
```

---

# 9. HTTP

HTTP stands for:

> Hypertext Transfer Protocol

HTTP defines how clients and servers communicate.

It is one of the core protocols of the Web.

A simplified exchange:

```text
Client
  │
  │ HTTP Request
  ▼
Server
  │
  │ HTTP Response
  ▼
Client
```

---

## HTTP is a protocol

A protocol is a set of rules for communication.

For HTTP, those rules describe things such as:

- how requests are structured
- how responses are structured
- methods
- headers
- status codes
- message bodies
- caching behavior

---

## HTTP is application-layer communication

The Internet has multiple layers of networking.

You don't need to memorize every layer immediately, but it helps to know that HTTP sits above lower-level networking protocols.

Very simplified:

```text
Application
    │
   HTTP
    │
Transport
    │
   TCP / QUIC
    │
Internet
    │
   IP
    │
Link / Physical
```

Modern HTTP/3 uses QUIC, which runs over UDP.

HTTP/1.1 and HTTP/2 commonly use TCP-based connections.

---

# 10. HTTPS

HTTPS stands for:

> HTTP Secure

More precisely, HTTPS is HTTP sent over a secure TLS connection.

Instead of:

```text
HTTP
 ↓
Network
```

you can think of:

```text
HTTP
 ↓
TLS
 ↓
Network
```

TLS provides security properties such as:

- encryption
- integrity
- server authentication

---

## Why HTTPS matters

Without encryption, someone able to observe network traffic could potentially see sensitive information.

With HTTPS, application data is protected by the TLS connection.

For example:

```text
HTTP:
username=alex
password=12345
```

would be a terrible way to transmit credentials.

HTTPS encrypts the data while it is traveling across the network.

---

## HTTPS does NOT mean

HTTPS does not automatically mean:

- the website is trustworthy
- the company is legitimate
- the application has no vulnerabilities
- your data is safe after the server receives it

HTTPS primarily secures communication between the client and server endpoint covered by the TLS connection.

A malicious website can also use HTTPS.

---

# 11. HTTP Methods

HTTP methods describe the intended operation for a request.

The most commonly encountered methods are:

```text
GET
POST
PUT
PATCH
DELETE
```

---

## GET

Used to retrieve data.

Example:

```http
GET /products
```

Meaning:

> Give me the products resource.

Another example:

```http
GET /users/42
```

Meaning:

> Give me user 42.

GET requests should generally be safe and should not be used to perform destructive actions.

---

## POST

Usually used to submit data or create a resource.

Example:

```http
POST /users
```

Body:

```json
{
  "name": "Alex",
  "email": "alex@example.com"
}
```

The server may create a new user.

---

## PUT

Usually represents replacing a resource with the supplied representation.

Example:

```http
PUT /users/42
```

Body:

```json
{
  "name": "Alex",
  "email": "new@example.com"
}
```

---

## PATCH

Used for partial modification.

Example:

```http
PATCH /users/42
```

Body:

```json
{
  "name": "Alex"
}
```

Only the specified field may be changed.

---

## DELETE

Used to request deletion of a resource.

```http
DELETE /users/42
```

---

## CRUD relationship

A useful mapping is:

```text
CREATE  → POST
READ    → GET
UPDATE  → PUT / PATCH
DELETE  → DELETE
```

This is useful, but it is not a law of nature. Real APIs can have other designs.

---

# 12. HTTP Status Codes

HTTP responses contain a status code that tells the client broadly what happened.

The major categories are:

```text
1xx → Informational
2xx → Success
3xx → Redirection
4xx → Client error
5xx → Server error
```

---

## 1xx — Informational

These indicate that the request is being processed or that additional communication is expected.

You will encounter them less often in normal application development.

---

## 2xx — Success

### 200 OK

The request succeeded.

```http
HTTP/1.1 200 OK
```

Common for:

```text
GET requests
```

---

### 201 Created

A resource was successfully created.

Common after:

```text
POST /users
```

---

### 204 No Content

The request succeeded, but there is no response body.

Common for some successful update or delete operations.

---

# 3xx — Redirection

### 301 Moved Permanently

The resource has permanently moved.

### 302 Found

A temporary redirect behavior.

### 304 Not Modified

Often used with caching.

It tells the client that its cached representation is still valid under the request's conditional validation.

---

# 4xx — Client Error

These generally indicate that the request could not be fulfilled because of something about the request or client's authorization.

### 400 Bad Request

The server cannot process the request because it is invalid.

### 401 Unauthorized

Authentication is required or has failed.

The name is slightly confusing:

```text
401 → authentication problem
403 → permission problem
```

### 403 Forbidden

The server understood the request but refuses to authorize it.

### 404 Not Found

The requested resource was not found.

This does not necessarily mean "the server is down."

### 405 Method Not Allowed

The resource exists, but that HTTP method is not allowed for it.

---

# 5xx — Server Error

These indicate that the server encountered a problem handling a valid-looking request.

### 500 Internal Server Error

A generic server-side error.

### 502 Bad Gateway

A gateway/proxy received an invalid response from an upstream server.

### 503 Service Unavailable

The service is temporarily unable to handle the request.

Possible reasons include:

- overload
- maintenance
- temporary failure

---

# 13. Request / Response

This is one of the most important concepts in web development.

A client sends a **request**.

A server sends a **response**.

---

## HTTP Request

A simplified request:

```http
GET /products HTTP/1.1
Host: example.com
Accept: text/html
User-Agent: Mozilla/5.0
```

Let's break it down.

```text
GET /products HTTP/1.1
│   │         │
│   │         └── HTTP version
│   └──────────── Resource
└──────────────── Method
```

Then headers:

```text
Host: example.com
Accept: text/html
User-Agent: ...
```

And some requests also contain a body.

---

## Request body

For example:

```http
POST /users HTTP/1.1
Content-Type: application/json

{
  "name": "Alex",
  "email": "alex@example.com"
}
```

The body contains data being sent to the server.

---

## HTTP Response

A simplified response:

```http
HTTP/1.1 200 OK
Content-Type: text/html

<h1>Hello</h1>
```

It contains:

```text
Status line
Headers
Body
```

---

## Full exchange

```text
CLIENT

GET /products HTTP/1.1
Host: example.com
Accept: application/json


                 ↓
              NETWORK
                 ↓


SERVER

HTTP/1.1 200 OK
Content-Type: application/json

[
  {
    "id": 1,
    "name": "Laptop"
  }
]
```

The browser receives the response and processes it.

---

# 14. Headers

HTTP headers provide metadata about a request or response.

Think of headers as information **about the message**.

---

## Request headers

Examples:

```http
Host: example.com
User-Agent: Mozilla/5.0
Accept: application/json
Authorization: Bearer ...
Content-Type: application/json
Cookie: session_id=abc123
```

---

## Response headers

Examples:

```http
Content-Type: text/html
Content-Length: 1234
Cache-Control: max-age=3600
Set-Cookie: session_id=abc123
Location: /login
```

---

## Content-Type

Tells the receiver what kind of content is being sent.

Examples:

```http
Content-Type: text/html
Content-Type: text/css
Content-Type: application/javascript
Content-Type: application/json
image/png
```

---

## Authorization

Used to provide authentication credentials or tokens.

Example:

```http
Authorization: Bearer eyJ...
```

Do not expose real credentials or tokens in public repositories.

---

## Cache-Control

Controls caching behavior.

Example:

```http
Cache-Control: max-age=3600
```

This can tell caches that the response can be considered fresh for a specified period.

---

## User-Agent

Provides information about the client software.

Example:

```http
User-Agent: Mozilla/5.0 ...
```

---

# 15. Cookies

A cookie is a small piece of data that a server can ask a browser to store and send with later requests.

Cookies are commonly used for:

- sessions
- preferences
- authentication state
- analytics
- other application state

---

## Setting a cookie

A server can send:

```http
Set-Cookie: session_id=abc123
```

The browser stores it according to the cookie's rules.

Later, the browser may send:

```http
Cookie: session_id=abc123
```

---

## Cookie flow

```text
First request
     │
     ▼
Server
     │
     │ Set-Cookie
     ▼
Browser
     │
     │ stores cookie
     │
     ▼
Later request
     │
     │ Cookie: session_id=abc123
     ▼
Server
```

---

## Important cookie attributes

### Secure

A `Secure` cookie is sent only over HTTPS connections.

### HttpOnly

An `HttpOnly` cookie cannot normally be read by JavaScript through `document.cookie`.

This can reduce the impact of certain XSS scenarios involving cookie theft.

### SameSite

Controls when cookies are sent in cross-site contexts.

Common values:

```text
Strict
Lax
None
```

### Expires / Max-Age

Controls cookie lifetime.

---

## Cookies are not databases

A cookie is not a replacement for a database.

Do not think:

```text
Cookie = user's entire account
```

More commonly:

```text
Cookie
   ↓
Session identifier
   ↓
Server
   ↓
Session data / database
```

---

# 16. Sessions

HTTP itself is fundamentally stateless: each request is a separate HTTP exchange.

But applications often need to remember users across requests.

That is where sessions can help.

---

## The problem

Suppose you log in.

The browser sends:

```text
POST /login
```

The server verifies your credentials.

Now you visit:

```text
GET /profile
```

How does the server know that the second request belongs to the user who just logged in?

A common solution is a session.

---

## Traditional session model

```text
Browser
   │
   │ Login
   ▼
Server
   │
   │ Create session
   ▼
Session Store
   │
   │ session_id = abc123
   ▼
Browser
   │
   │ Cookie: session_id=abc123
   ▼
Server
   │
   │ lookup abc123
   ▼
User session
```

The cookie may contain only an identifier.

The actual session information can live on the server.

---

## Session vs cookie

These are related but not identical.

### Cookie

Data stored by the browser and sent according to cookie rules.

### Session

Server-side or otherwise managed state associated with a client/user across requests.

A session can be identified using a cookie.

---

# 17. Caching

Caching means storing data temporarily so it can be reused instead of being fetched or generated again.

Caching exists at many layers.

```text
Browser Cache
      ↓
OS / Network Cache
      ↓
CDN Cache
      ↓
Reverse Proxy Cache
      ↓
Application Cache
      ↓
Database Cache
```

---

## Why cache?

Without caching:

```text
Every request
     ↓
Server
     ↓
Database
     ↓
Generate response
```

This can be expensive.

With caching:

```text
Request
   ↓
Cache
   ↓
Already available?
   │
   ├── YES → Return cached data
   │
   └── NO  → Fetch/generate → Store → Return
```

---

## Browser caching

Your browser may cache:

- images
- CSS
- JavaScript
- fonts
- other resources

This can make repeat visits faster.

---

## Cache-Control

Servers can provide caching instructions.

Example:

```http
Cache-Control: max-age=3600
```

The exact caching behavior depends on the directives and the type of cache.

---

## Cache invalidation

One of the classic problems in software is:

> How do we know when cached data is no longer valid?

Suppose you change:

```text
style.css
```

but the browser still uses an old cached version.

A common technique is asset versioning/fingerprinting:

```text
style.a81f32.css
```

When the file changes:

```text
style.91cd72.css
```

The URL changes, so caches know it is a different resource.

---

# 18. CDN

CDN stands for:

> Content Delivery Network

A CDN is a distributed network of servers designed to deliver content efficiently to users in different geographic locations.

---

## The problem

Suppose your application server is located in:

```text
United States
```

and your user is in:

```text
India
```

Sending every static resource directly from the origin may involve substantial network distance.

A CDN can cache and serve appropriate content from an edge location closer to the user.

---

## CDN architecture

```text
                    Origin Server
                         │
              ┌──────────┼──────────┐
              │          │          │
              ▼          ▼          ▼
           Edge A      Edge B     Edge C
              │          │          │
              ▼          ▼          ▼
           Users       Users       Users
```

---

## Example

Without CDN:

```text
User in India
      │
      └──────────────► Server in USA
```

With CDN:

```text
User in India
      │
      ▼
Nearby CDN Edge
      │
      ├── cached resource → return
      │
      └── cache miss → origin server
```

---

## What can a CDN deliver?

Common examples:

- images
- CSS
- JavaScript
- fonts
- videos
- downloads
- cached API responses in appropriate architectures

CDNs can also provide services such as:

- TLS termination
- traffic filtering
- DDoS protection
- edge logic
- request routing

The exact features depend on the provider.

---

# 19. Hosting

Hosting means making an application or resource available on a server or platform that users can access.

---

## Simple example

Suppose you create:

```text
index.html
style.css
script.js
```

These files exist only on your laptop.

Other people cannot access them through the public Internet unless you make them available through some accessible server/service.

Hosting provides that availability.

---

## Static hosting

For a simple website:

```text
HTML
CSS
JavaScript
Images
```

a static hosting platform can serve these files.

Architecture:

```text
Browser
   │
   ▼
Hosting Server
   │
   ├── index.html
   ├── style.css
   ├── script.js
   └── image.png
```

---

## Dynamic hosting

A dynamic application might look like:

```text
Browser
   │
   ▼
Web Server
   │
   ▼
Backend Application
   │
   ▼
Database
```

The server runs application code and generates responses.

---

## Types of hosting

You will eventually encounter:

### Shared hosting

Multiple websites share a server environment.

### Virtual Private Server

A virtualized server with more control.

### Dedicated server

A physical server allocated to one customer/workload.

### Cloud hosting

Resources provided through cloud infrastructure.

### Serverless

You deploy functions/services without managing traditional servers directly.

"Serverless" does **not** mean there are no servers.

It means server management is abstracted away from you.

---

# 20. SSL/TLS Basics

This topic is often explained badly, so it is worth understanding properly.

---

## SSL vs TLS

SSL stands for:

> Secure Sockets Layer

TLS stands for:

> Transport Layer Security

Modern systems use TLS.

SSL is the older technology and is obsolete.

People still say:

> "SSL certificate"

even when they technically mean a certificate used with TLS.

---

## What TLS provides

TLS is designed to provide:

### 1. Encryption

Others observing the network should not be able to simply read the protected application data.

### 2. Integrity

The connection provides mechanisms to detect unauthorized modification of protected data.

### 3. Authentication

Certificates help the client authenticate the server's identity.

---

## Certificate

A website presents a digital certificate during TLS setup.

The certificate contains information about the identity associated with the certificate and is digitally signed by a certificate authority chain.

The browser verifies the certificate according to its trust rules.

---

## Simplified TLS process

Very simplified:

```text
Browser
   │
   │ ClientHello
   ▼
Server
   │
   │ ServerHello + Certificate
   ▼
Browser
   │
   │ Verify certificate
   ▼
Secure cryptographic setup
   │
   ▼
Encrypted communication
```

The real TLS handshake is more detailed, especially across TLS versions and connection types.

---

## Certificate Authorities

Browsers maintain trust in certificate authorities (CAs).

A CA can issue certificates for domains after appropriate validation.

The browser checks whether the certificate chain leads to a trusted authority and whether other certificate conditions are satisfied.

---

## HTTPS connection

Putting it together:

```text
Browser
   │
   │ 1. Connect to server
   ▼
TLS Handshake
   │
   │ 2. Establish secure connection
   ▼
Encrypted HTTP
   │
   │ 3. Request
   ▼
Server
   │
   │ 4. Response
   ▼
Browser
```

---

# 🔗 Putting Everything Together

Now let's connect all 20 topics.

Suppose you type:

```text
https://shop.example.com/products?id=42
```

into your browser.

What happens?

---

## Step 1 — Browser reads the URL

The browser identifies:

```text
Scheme:
https

Host:
shop.example.com

Path:
/products

Query:
id=42
```

---

## Step 2 — DNS

The browser needs to determine where `shop.example.com` should connect.

It may use cached DNS information or query a DNS resolver.

Eventually, the hostname is resolved to an appropriate IP address.

```text
shop.example.com
        ↓
       DNS
        ↓
IP address
```

---

## Step 3 — Network connection

The browser establishes the appropriate network connection to the server.

Depending on the HTTP version and environment, different transport mechanisms may be involved.

For example:

```text
HTTP/1.1 or HTTP/2 → commonly TCP
HTTP/3 → QUIC over UDP
```

---

## Step 4 — TLS

Because the URL uses:

```text
https://
```

TLS is established.

The browser verifies the server certificate and establishes cryptographic keys for the secure connection.

---

## Step 5 — HTTP request

The browser sends something conceptually like:

```http
GET /products?id=42 HTTP/1.1
Host: shop.example.com
Accept: text/html
User-Agent: ...
Cookie: ...
```

---

## Step 6 — Server receives the request

The request may pass through infrastructure such as:

```text
CDN
   ↓
Load Balancer
   ↓
Reverse Proxy
   ↓
Web Server
   ↓
Application
```

Not every website has all of these components, but large systems often do.

---

## Step 7 — Application processes the request

The application might:

```text
Read query parameter
       ↓
Check authentication
       ↓
Check cache
       ↓
Query database
       ↓
Process business logic
       ↓
Generate response
```

---

## Step 8 — Server responds

For example:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Cache-Control: no-cache

<html>
...
</html>
```

---

## Step 9 — Browser receives response

The browser processes the HTML.

It may discover more resources:

```text
HTML
 │
 ├── style.css
 ├── app.js
 ├── logo.png
 └── font.woff2
```

The browser makes additional requests for resources it needs.

---

## Step 10 — Browser renders

Eventually:

```text
HTML
 +
CSS
 +
JavaScript
 +
Images
 +
Fonts
      ↓
Browser rendering
      ↓
Pixels
      ↓
Your screen
```

And you see the webpage.

---

# 🧠 What Happens When You Open a Website?

Here is the simplified complete flow:

```text
                    YOU
                     │
                     ▼
                  BROWSER
                     │
                     │ URL
                     ▼
                  DNS
                     │
                     │ IP
                     ▼
              NETWORK CONNECTION
                     │
                     ▼
                   TLS
                     │
                     │ Secure connection
                     ▼
               HTTP REQUEST
                     │
                     ▼
              CDN / PROXY / SERVER
                     │
                     ▼
               APPLICATION
                     │
                     ▼
                DATABASE
                     │
                     ▼
               APPLICATION
                     │
                     ▼
              HTTP RESPONSE
                     │
                     ▼
                  BROWSER
                     │
              ┌──────┼──────┐
              ▼      ▼      ▼
             HTML    CSS    JS
              │      │      │
              └──────┼──────┘
                     ▼
                  RENDER
                     │
                     ▼
                  SCREEN
```

This is the mental model you should keep.

---

# 🧪 A More Realistic Example

Imagine an e-commerce website:

```text
https://shop.example.com/products/42
```

You open it.

## Browser

The browser understands the URL.

## DNS

DNS helps locate the service.

## CDN

The request may pass through a CDN.

## TLS

HTTPS establishes secure communication.

## HTTP

The browser sends:

```http
GET /products/42
```

## Server

The server receives the request.

## Authentication

The server may inspect a cookie.

```http
Cookie: session_id=abc123
```

## Backend

The backend identifies the user/session.

## Database

The backend queries:

```text
SELECT * FROM products WHERE id = 42;
```

## Response

The server sends product information.

It could return HTML:

```html
<h1>Laptop</h1>
<p>₹75,000</p>
```

or JSON:

```json
{
  "id": 42,
  "name": "Laptop",
  "price": 75000
}
```

depending on the application architecture.

## Browser

The browser renders the result.

---

# ❌ Common Misconceptions

## "DNS is the Internet"

No.

DNS is one system used to resolve names and provide DNS records.

---

## "A domain is an IP address"

No.

A domain is a name.

DNS can provide information that maps the name to IP addresses or other targets.

---

## "A server is always a physical computer"

Not necessarily.

A server can be a process, virtual machine, container, cloud service, or physical machine.

---

## "HTTPS makes a website trustworthy"

No.

HTTPS protects the connection and authenticates the server according to certificate validation.

It does not guarantee that the website itself is honest or secure.

---

## "HTTP and HTTPS are completely different protocols"

They are different schemes, but HTTPS is essentially HTTP carried over TLS.

---

## "404 means the Internet is broken"

No.

A `404 Not Found` response means the server handling the request says the requested resource was not found.

---

## "401 means I don't have permission"

Not exactly.

The usual distinction is:

```text
401 → authentication required/failed
403 → request understood, but access forbidden
```

---

## "Cookies are the same as sessions"

No.

Cookies are client-side stored data sent according to cookie rules.

Sessions are application state associated with a client/user across requests.

A cookie is often used to identify a server-side session.

---

## "Serverless means no servers"

No.

Servers still exist.

The difference is that the platform manages more of the server infrastructure for you.

---

## "A CDN is just hosting"

Not exactly.

A CDN is a distributed delivery network. It can cache and serve content from edge locations and provide additional network services.

---

## "The browser downloads one file when I open a website"

Usually not.

A page may cause requests for:

```text
HTML
CSS
JavaScript
Images
Fonts
Videos
API data
```

---

# 🛠️ Developer Tools

Your browser already contains an excellent tool for learning these concepts.

Open DevTools.

Usually:

```text
F12
```

or:

```text
Ctrl + Shift + I
```

---

# 🌐 Network Tab

The Network tab is especially important.

Open a website and inspect the requests.

You will see things such as:

```text
Name
Status
Type
Initiator
Size
Time
```

Click a request and inspect:

```text
Headers
Payload
Response
Preview
Timing
```

This is where the theory becomes real.

---

## Inspect a request

You may see:

```text
Request URL
Request Method
Status Code
Remote Address
Referrer Policy
```

Then headers:

```text
Accept
Cookie
User-Agent
Content-Type
Authorization
```

And response information:

```text
Content-Type
Cache-Control
Set-Cookie
Content-Length
```

---

# 🧪 Things to Experiment With

## Experiment 1 — Inspect a website

Open any website.

Open:

```text
DevTools → Network
```

Reload the page.

Look at:

- document request
- CSS requests
- JavaScript requests
- image requests
- fonts
- API requests

Try to identify which requests are HTML, CSS, JS, images, and API responses.

---

## Experiment 2 — Inspect status codes

Find requests returning:

```text
200
301
302
304
404
```

where available.

Understand why each response received that status.

---

## Experiment 3 — Inspect headers

Click a request.

Find:

```text
Request Headers
Response Headers
```

Try to identify:

```text
Content-Type
Cache-Control
Set-Cookie
User-Agent
Accept
```

---

## Experiment 4 — Use curl

You can make HTTP requests without a browser.

For example:

```bash
curl https://example.com
```

This is useful because it makes the request/response model much more visible.

Try:

```bash
curl -I https://example.com
```

This requests headers only using curl's behavior for a HEAD request.

---

## Experiment 5 — Inspect DNS

On systems with appropriate command-line tools, try:

```bash
nslookup example.com
```

or:

```bash
dig example.com
```

These commands let you inspect DNS information.

---

## Experiment 6 — Inspect an IP

Try:

```bash
ping example.com
```

Be aware that ping uses ICMP and does **not** test HTTP itself.

This is an important distinction.

---

# 🧠 Questions You Should Be Able to Answer

After finishing this chapter, you should be able to explain:

### Internet

- What is the Internet?
- What is the Web?
- How are they different?

### Client / Server

- What is a client?
- What is a server?
- How do they communicate?

### Browser

- What does a browser do?
- What is the DOM?
- How does HTML become a webpage?

### Web Server

- What does a web server do?
- What is the difference between static and dynamic content?

### Domains

- What is a domain?
- What is a subdomain?
- What is a TLD?

### DNS

- Why is DNS needed?
- What does a DNS resolver do?
- What are A, AAAA, CNAME, MX, and TXT records?

### IP

- What is an IP address?
- What is IPv4?
- What is IPv6?
- What is the difference between public and private IPs?

### URLs

- What are scheme, host, port, path, query, and fragment?

### HTTP

- What is HTTP?
- What is an HTTP request?
- What is an HTTP response?

### HTTPS

- Why does HTTPS exist?
- What does TLS provide?
- What does a certificate do?

### Methods

- When would you use GET?
- POST?
- PUT?
- PATCH?
- DELETE?

### Status codes

- What does 200 mean?
- 201?
- 301?
- 304?
- 400?
- 401?
- 403?
- 404?
- 500?
- 503?

### Headers

- What are headers?
- What does Content-Type mean?
- What is Cache-Control?
- What is Set-Cookie?

### Cookies

- What is a cookie?
- How does a browser receive a cookie?
- What do Secure and HttpOnly mean?

### Sessions

- Why do applications need sessions?
- How can a cookie identify a session?

### Caching

- Why do we cache?
- Where can caching happen?
- What is cache invalidation?

### CDN

- What is a CDN?
- Why can a CDN reduce latency?
- What is an edge location?

### Hosting

- What does hosting mean?
- What is static hosting?
- What is dynamic hosting?
- What does serverless actually mean?

---

# 📝 Practice Questions

## Beginner

1. What is the difference between the Internet and the Web?
2. What is a client?
3. What is a server?
4. Why do we use domain names?
5. What does DNS do?
6. What is an IP address?
7. What does HTTPS mean?
8. What is a URL?
9. What is HTTP?
10. What is a cookie?

---

## Intermediate

11. Explain what happens after entering a URL into a browser.
12. Explain the difference between HTTP and HTTPS.
13. Explain GET vs POST.
14. Explain PUT vs PATCH.
15. Explain 401 vs 403.
16. Explain 404 vs 500.
17. Explain cookies vs sessions.
18. Explain browser cache vs CDN cache.
19. Explain public vs private IP addresses.
20. Explain a static website vs a dynamic application.

---

## Advanced Thinking

21. Why doesn't a browser directly query a website's database?

22. Why is DNS distributed instead of being one giant global database?

23. Why can a website still be malicious even when it uses HTTPS?

24. Why can changing a file's URL help with cache invalidation?

25. Why might a CDN improve performance?

26. Why doesn't a `404` necessarily mean the server is down?

27. Why is `401` different from `403`?

28. Why does HTTP need headers?

29. Why does a browser make many HTTP requests when loading one webpage?

30. What happens if DNS works but the server is unreachable?

31. What happens if DNS works and the server is reachable, but TLS certificate validation fails?

32. What happens if TLS works but the HTTP request returns `500`?

These questions are much more useful than memorizing definitions because they force you to connect the concepts.

---

# 🧩 Mini Projects / Experiments

## Project 1 — HTTP Inspector

Use browser DevTools to document:

```text
Request URL
Method
Status
Request Headers
Response Headers
Response Type
Timing
```

Do this for five different resources.

---

## Project 2 — Build a Tiny HTTP Server

Later, after learning Node.js, build a simple server:

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
    res.writeHead(200, {
        "Content-Type": "text/plain"
    });

    res.end("Hello from my server!");
});

server.listen(3000);
```

Then visit:

```text
http://localhost:3000
```

Now the client-server model becomes something you have actually built.

---

# 🧠 Final Mental Model

You don't need to memorize this chapter word-for-word.

Instead, understand the relationships.

```text
                    INTERNET
                       │
                       │
             ┌─────────▼─────────┐
             │      CLIENT       │
             │     Browser       │
             └─────────┬─────────┘
                       │
                       │ Domain name
                       ▼
                      DNS
                       │
                       │ IP address
                       ▼
                Network Connection
                       │
                       ▼
                     TLS
                       │
                       │ Secure channel
                       ▼
                    HTTP
                       │
                 ┌─────┴─────┐
                 │           │
              Request      Response
                 │           │
                 ▼           ▲
              Server ─────────┘
                 │
          ┌──────┼───────┐
          │      │       │
       Backend  Cache  Database
          │
          ▼
       Application
          │
          ▼
        Response
```

And around that system:

```text
Domain
  ↓
DNS
  ↓
IP
  ↓
Hosting
  ↓
Server
  ↓
HTTP/HTTPS
  ↓
Application
  ↓
Database
```

while:

```text
Browser
  ↓
Cookies
  ↓
Sessions
  ↓
Caching
  ↓
DOM
  ↓
Rendered UI
```

and:

```text
CDN
 ↓
Caches content closer to users
```

---

# 🏁 The One Story to Remember

When you type:

```text
https://example.com
```

you can think about it like this:

```text
1. I enter a URL.
        ↓
2. The browser understands the URL.
        ↓
3. DNS helps find the server's network address.
        ↓
4. The browser establishes a network connection.
        ↓
5. TLS secures the HTTPS connection.
        ↓
6. The browser sends an HTTP request.
        ↓
7. The request reaches the server.
        ↓
8. The server/application processes it.
        ↓
9. It may use caches and databases.
        ↓
10. The server sends an HTTP response.
        ↓
11. The browser receives the response.
        ↓
12. The browser requests additional resources.
        ↓
13. HTML, CSS, JavaScript, images, etc. are processed.
        ↓
14. The browser renders the final interface.
        ↓
15. I see the website.
```

That is the foundation.

Once this makes sense, technologies like:

```text
HTML
CSS
JavaScript
React
Node.js
Express
REST APIs
Databases
Authentication
Deployment
```

stop looking like unrelated technologies.

They become different pieces of the same system.

---

# 🚀 What Comes Next?

After understanding these fundamentals, the natural progression is:

```text
Web Fundamentals
       ↓
HTML
       ↓
CSS
       ↓
JavaScript
       ↓
DOM
       ↓
Browser APIs
       ↓
Frontend Development
       ↓
React
       ↓
Node.js
       ↓
Express
       ↓
REST APIs
       ↓
Databases
       ↓
Authentication
       ↓
Deployment
       ↓
Full-Stack Projects
```

**Do not rush past the fundamentals.**

You don't need to memorize every networking detail before moving on, but you should understand the core model well enough that when you later see a request in DevTools, an API endpoint in JavaScript, a cookie in a response, or a database call in a backend, you understand where it fits.

---

> **The web is not magic.**
>
> It is a collection of systems communicating through well-defined rules.
>
> The better you understand those rules, the easier it becomes to understand everything built on top of them.
