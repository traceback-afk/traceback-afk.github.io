![django ninja](https://django-ninja.dev/img/hero.png)
# Django Ninja Workshop
Develop API endpoints fast, easy and clean

The purpose of this workshop is to make you familiar with 
REST API development basics and set you on a path to learn more. 
The content of this presentation is written without the use of 
generative artificial intelligence, so please ignore it in case 
you spot a grammatical mistake. Cheers!

# What is an API?
An API or Application Programming Interface is a software that 
acts as an intermediary between the client and the server. 

![rest api model](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Funione.io%2Fassets%2Fimages%2Ftickets%2Fwhat-is-a-rest-api-restful-api%2Fwhat-is-a-rest-api-restful-api-model-unione.png&f=1&nofb=1&ipt=1de367bfef63de13fe31984c0f66f48ade9974adae9bc9de347ade7957537ae0)
# Rest
REST is an acronym for REpresentational State Transfer and an architectural style for distributed hypermedia systems.
REST is not a protocol or a standard, it is an architectural style. Like the other architectural styles, REST also has its guiding principles and constraints.

![rest](https://images.gitbook.com/__img/dpr=2,width=760,onerror=redirect,format=auto,signature=-1730579380/https%3A%2F%2Frestfulapi.net%2Fwp-content%2Fuploads%2FWhat-is-REST.png)

## Uniform Interface
REST defines a consistent and uniform interface for interactions between clients and servers. 
For example, the HTTP-based REST APIs make use of the standard HTTP methods (GET, POST, PUT, DELETE, etc.) 
and the URIs (Uniform Resource Identifiers) to identify resources.

## Client-Server
By separating the user interface concerns (client) from the data storage concerns (server), we improve the portability 
of the user interface across multiple platforms and improve scalability by simplifying the server components.

## Stateless
Each request from the client to the server must contain all of the 
information necessary to understand and complete the request.

## Cacheable
A response should implicitly or explicitly label itself as cacheable or non-cacheable.

If the response is cacheable, the client application gets the right to reuse the response 
data later for equivalent requests and a specified period.

## Layered system
The layered system style allows an architecture to be composed of hierarchical layers 
by constraining component behavior. In a layered system, each component cannot see beyond 
the immediate layer they are interacting with.

## Code on Demand
REST also allows client functionality to be extended by downloading and 
executing code in the form of applets or scripts.

