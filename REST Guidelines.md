Tags: #tech #web 

# Implementation
- Methods
	- GET: Retreive
	- POST: create new
	- PUT: update
	- DELETE: delete
- Status codes
	- 2xx: success
	- 4xx: client error
	- 5xx: server error

# Best Practices
- Flexible content format negotiation
	- support JSON or XML by implementing multiple (de)serializers

# Design Abstracts
- Uniform Interface
	- each URI should be uniquely identified
	- Manipulation of resources thru representation
		- uniform representation in responses
	- Self descriptive messages
		- enough information to know how to process the message
		- information on additional actions
	- Hypermedia as the engine of application state
		- client should have only the initial URI of the application
		- client should be able to dynamically drive all other resources and interaction with hyperlinks
- Client Server model
	- separation of concerns between user interface and data storage
	- ensure portability such that same API can be used for multiple clients
	- changes to client or server should ensure that the contract between them does not break
- Stateless
	- Each interaction should contain all information
	- Server should not maintain context or state between calls
	- Client application must maintain state
- Cacheable 
	- if cacheable, client has the right to reuse the response for similar calls for a given period of time
	- response should be implicitly or explicitly labelled as cacheable
- Layered System ?


# Terminology
A **Resource** is an abstraction of information. In REST, it can be a document, image, service(API), an actual person, etc.

A **Resource Representation** contains:
- data
- metadata
- hyperlinks that can guide client to the next desired state


# Links

# References
https://restfulapi.net/