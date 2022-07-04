# Software Systems Architecture: Working with Stakeholders using Viewpoints and Perspectives by Rozanski Nick, Woods Eoin

## Architecture Fundamentals
Structures
- Static Structures: design time elements like classes, packages, etc.
- Dynamic Structures: run time elements like information flow, caches, etc.

System Properties
- externally visible behaviour: 
	- *what does a system do?*
	- functional specs or features
- quality properties: 
	- *how does a system do it?*
	- performance under load, response time

Principles of Design and Evolution are force consistency in internal implementation and exposing underlying assumptions.

A candidate architecture is a specific arrangement of static and dynamic structures that might potentially fulfill the system's externally visible behaviour and quality properties.

Architectural element:
- clear set of responsibility
- clear set of boundaries
- interfaces that provide a service to other elements

Stakeholders; triangle of quality, time, cost

Architectural Description explains the architecture to the stakeholder

## Viewpoints and Views
View is 
- the representation of one or more structural aspects of an architecture 
- that explains how the architecture meets the concerns of one or more stakeholders

Check following when deciding what to include in a view:
- architectural scope
- element types
- audience and their expertise
- scope of concerns
- level of detail

Viewpoint is patterns, templates, conventions for constructing a type of view.

Viewpoint benefits: 
- separation of concerns that are catered by indepedent aspects
- different communications for different stakeholder groups
- management of complexity
- improved developer focus

Viewpoint pitfalls:
- possible cross-view inconsistency
- selection of wrong set of views
- fragmentation leading to AD difficult to understand

### Catalog
Context:
- relationships, dependencies, interactions between system and its environments

Functional: 
- runtime functional elements
- their responsibilities, interfaces, primary interactions

Information: 
- how does system store, manipulate, manage, distribute information

Concurrency:
- maps functional elements to concurrency units
- how is it coordinated and controlled

Development:
- architecture that helps in building, testing, maintaining, enhancing

Deployment:
- environment where the system will be deployed
- dependencies of the system

Operational:
- how will the system be installed, operated, administered, supported on prod

## Architectural Perspectives
Activities, guidelines, tactics to ensure that a system exhibits certain quality properties across multiple views.

Systemizing:
- determine required quality properties
- assess and review architectural models to ensure that architecture exhibits properties
- identify, prototype, test, select tactics to ensure properties where they are missing

Tactics are not design patterns:
- they do not mandate a particular software structure
- general guidelines on how to design a particular aspect

Apply perspectives earlier in design to avoid going into architectural blind alleys where implementation
- ... is functionally correct
- ... but does not offer quality properties like performance and availability

### Some important perspectives
- Security 
	- controlled access to sensitive system resources
- Performance and Scalability 
	- meeting required performance profile  
	- handling increasing workloads satisfactorily
- Availability and Resilience 
	- available when required
	- coping with failures that will affect availabilty
- Evolution 
	- cope with likely changes
- Regulations
	- confirm to laws, regulations, company policies, rules, standards

### How to use architectural perspectives in different situations
- when working with new area? typical concerns, problems, solutions are not familiar?
	- use as a guide
- need to review models for particular quality property without absorbing new details?
	- use as a store of knowledge
- familiar with environment but don't want to forget anything important?
	- use as a memory aid

### Apply perspectives to views
Architecture Views describs the architecture while Architecture Perspectives guide you thru analysis/modification to ensure quality properties are met.

You can apply all perspectives to all views but you might not always do that.

Create a 2x2 grid, views by perspectives.

See Table 4-1 for *Typical View and Perspective Applicability*

Leads to:
- insights
- improvements
- artifacts: should be preserved

Pitfalls and what to balance:
- applying multiple perspectives to the same view can lead to conflicts
	- multiple quality properties might not be satisfied
- different stakeholders may value one quality property over another
- perspectives contain generalized, established concepts
	-  tweak and apply as per what is relevant to your situation as per relevance and feasiblity


Prioritize and apply only the most relevant perspectives to your architecture.
Selection criteria:
- needs of the stakeholders
- relative importance of quality perspectives to them
- experience and judgement


## Role of the software architect

> Do not think about the solution till you have understood the problem.

Stakeholders will want to think of solutions from day one. An architect has to manage that.




#### Resources
https://www.viewpoints-and-perspectives.info/home/resources/
See:
- Quick Reference Card
- Architectural Description Document Template

#### Links

#### Tags

#### References