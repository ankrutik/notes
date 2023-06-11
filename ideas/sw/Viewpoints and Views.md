# Viewpoints and Views
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

## Catalog
### Context
- relationships, dependencies, interactions between system and its environments

### Functional
- runtime functional elements
- their responsibilities, interfaces, primary interactions

### Information
- how does system store, manipulate, manage, distribute information

### Concurrency
- maps functional elements to concurrency units
- how is it coordinated and controlled

### Development
- architecture that helps in building, testing, maintaining, enhancing

### Deployment
- environment where the system will be deployed
- dependencies of the system

### Operational
- how will the system be installed, operated, administered, supported on prod

#### Links
[[Software Architecture]]

#### Tags

#### References
[[Software Systems Architecture Rozanski Nick, Woods Eoin]]