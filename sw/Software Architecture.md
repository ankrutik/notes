# Architecture

## Broad overview questions to ask when looking at architecture
- What the components?
- What is the relationship between
	- components
	- environment
- What are the principles?

## Structures
- Static Structures: design time elements like classes, packages, etc.
- Dynamic Structures: run time elements like information flow, caches, etc.

## System Properties
- externally visible behaviour: 
	- *what does a system do?*
	- functional specs or features
- quality properties: 
	- *how does a system do it?*
	- performance under load, response time

**Principles** of Design and Evolution are force consistency in internal implementation and exposing underlying assumptions.

A **candidate architecture** is a specific arrangement of static and dynamic structures that might potentially fulfill the system's externally visible behaviour and quality properties.

**Architectural element**:
- clear set of responsibility
- clear set of boundaries
- interfaces that provide a service to other elements

**Stakeholders**; triangle of quality, time, cost

**Architectural Description** explains the architecture to the stakeholder

#### Links

#### Tags

#### References
https://vedcraft.com/architecture/introduction-to-software-architecture/
[[Software Systems Architecture Rozanski Nick, Woods Eoin]]