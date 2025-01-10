# REST API

{% hint style="info" %}
<mark style="color:blue;">**A REST API (Representational State Transfer API)**</mark> is a web service that uses standard HTTP methods and a stateless, resource-based architecture to enable communication between clients and servers.
{% endhint %}

* A REST API is an API that works on top of the HTTP protocol.
* It defines a set of functions developers can use to perform requests and receive responses via HTTP protocol such as GET and POST

Conforming to the constraints of the REST architecture is generally referred to as being “**RESTful**”. An API can be considered “**RESTful**” if it has the following features:

* **Client-Server** - The client handles the front end and the server handles the back end. Either can be replaced independently of the other.
* **Stateless** - No client data is stored on the server between requests. The session state is stored on the client.
* **Cacheable** - Clients can cache responses to improve performance.

## RESTful Implementation

A RESTful web service is implemented using HTTP. It is a collection of resources with four defined aspects:

* The base Uniform Resource Identifier (URI) for the web service, such as [http://example.com/resources](http://example.com/resources).
* The data format supported by the web service. This is often JSON, YAML, or XML but could be any other data format that is a valid hypertext standard.
* The set of operations supported by the web service using HTTP methods.
* The API must be hypertext driven.

RESTful APIs use common HTTP methods including POST, GET, PUT, PATCH and DELETE. These correspond to RESTful operations: Create, Read, Update, and Delete (or CRUD).

***

## URI, URN and URL

Web resources and web services such as RESTful APIs are identified using a URI. A URI is a string of characters that identifies a specific network resource. A URI has two specialisations:

* **Uniform Resource Name (URN)** - identifies only the namespace of the resource (web page, document, image, etc.) without reference to the protocol.
* **Uniform Resource Locator (URL)** - defines the network location of a specific resource on the network. HTTP or HTTPS URLs are typically used with web browsers. Other protocols such as FTP, SFTP, SSH, and others can use a URL. A URL using SFTP might look like: sftp://sftp.example.com.

These are the parts of a URI, as shown in the figure:

* **Protocol/scheme** - HTTPS or other protocols such as FTP, SFTP, mailto, and NNTP
* **Hostname** - [www.example.com](http://www.example.com/)
* **Path and file name** - /author/book.html
* **Fragment** - #page155

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-09 at 20.19.40.png" alt=""><figcaption></figcaption></figure>

***

## Anatomy of a RESTful Request

In a RESTful Web service, a request made to a resource's URI will elicit a response. The response will be a payload typically formatted in JSON, but could be HTML, XML, or some other format.

<figure><img src="../../.gitbook/assets/Screenshot 2025-01-09 at 20.22.33.png" alt=""><figcaption></figcaption></figure>

These are the different parts of the API request:

* **API Server** - This is the URL for the server that answers REST requests. In this example it is the MapQuest API server.
* **Resources** - Specifies the API that is being requested. In this example it is the MapQuest directions API.
* **Query** - Specifies the data format and information the client is requesting from the API service. Queries can include:
  * **Format** - This is usually JSON but can be YAML or XML. In this example JSON is requested.
  * **Key** - The key is for authorization, if required. MapQuest requires a key for their directions API. In the above URI, you would need to replace “KEY” with a valid key to submit a valid request.
  * **Parameters** - Parameters are used to send information pertaining to the request. In this example, the query parameters include information about the directions that the API needs so it knows what directions to return: "from=San+Jose,Ca" and "to=Monterey,Ca".

Many RESTful APIs, including public APIs, require a key. The key is used to identify the source of the request. Here are some reasons why an API provider may require a key:

* To authenticate the source to make sure they are authorized to use the API.
* To limit the number of people using the API.
* To limit the number of requests per user.
* To better capture and track the data being requested by users.
* To gather information on the people using the API.
