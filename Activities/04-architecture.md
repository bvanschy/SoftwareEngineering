# Architecture
Performed by the “Solutions architect” role.

## Necessary Skills and Knowledge
- Technical
  - Architectural patterns
  - Architectural styles
  - Design patterns
  - Software engineering
  - Design
  - Programming
  - Platform
- Management
  - Projects
  - People
  - Process
- Leadership
- Communication and collaboration
- Diplomacy
- Negotiation
- Business domain
- Business processes

## Design
Characteristics of architectural-relevant components:

- Affect overall system structure and behavior
- Influence quality attributes
- Influence constraints
- Rarely change
- Difficult to change

Top-down design

- Series of decomposition steps
- Good for forecasting and planning

Bottom-up design

- Assembling small parts into emerging architecture
- Problematic with large teams and large projects

## Best practices
- Modular
  1.	System: boundaries and interfaces with external systems
  2.	Subsystems: logical separation of responsibilities, relationships
  3.	Module: logical area of responsibility
  4.	Component: independently deployable, pluggable, replaceable, single function
- Aspect-oriented programming
- Build architecture incrementally
- Postpone decisions until the last responsible moment
- Domain-specific languages

## Package and Component Principles
- Reuse/Release Equivalence Principle (REP)
  - The granule of reuse is the granule of release
  - Either all classes in a component are reusable for a single purpose or none of them are
- Common Reuse Principle (CRP)
  - The classes in a component are reused together
  - If you reuse one of the classes in a component, you reuse them all
- Common Closure Principle (CCP)
  - The classes in a component should be closed together against the same kinds of changes
  - A change that affects a component affects all its classes and no other components
- Acyclic Dependencies Principle (ADP)
  - Allow no cycles in the component dependency graph
- Stable-Dependencies Principle (SDP)
  - Depend in the direction of increasing stability (decreasing changeability)
- Stable-Abstractions Principle (SAP)
  - A component should be as abstract as it is stable

## Class Structure Principles
Abstraction

- The essential characteristics that distinguish the component from all others
- Provides crisply defined conceptual boundaries relative to the viewer’s perspective

Encapsulation

- Grouping the elements of an abstraction that constitute its structure and behaviour
- Separates different abstractions from each other providing explicit barriers

Information Hiding

- Concealing the implementation details from its clients (in order to handle complexity and minimize coupling)

Modularization

- Meaningful decomposition of a software system and grouping into subsystems and components
- Physical containers for functionalities or responsibilities

Separation of Concerns

- Different or unrelated responsibilities should be separated from each other

Coupling

- Measures the strength of association established by a connection from one module to another
- Low coupling is good

Cohesion

- Measures the degree of connectivity between the functions and elements of a single module
- High cohesion is good

Sufficiency, Completeness, and Primitiveness

- Sufficient: every component captures the necessary characteristics of its abstraction
- Complete: every component captures all the relevant characteristics of its abstraction
- Primitive: each operation of a component is easily implemented

Separation of Policy and Implementation

- A component deals with either policy or implementation but not both
- Policy: context-sensitive decisions, semantics and interpretation of information, assembly of disjoint computations, selection of parameter values
- Implementation: execution of a fully-specified algorithm

Separation of Interface and Implementation

- A component should consist of an interface and an implementation
- Interface: defines the functionality and specifies how to use it, accessible by clients
- Implementation: code for the functionality, not accessible by clients

## Documentation
Objectives:

- Communicate with stakeholders
- Lead design and construction
- Educate

Documentation:

- System overview
- View catalog
- Views
- UML (structural and behavioural) diagrams
- Interfaces
- Relationships between views
- How quality attributes affect viewpoints
- Other constraints, business rules
- Alternatives, decisions, rationale, justification

Viewpoints:

- Logical, Module
  - Static decomposition (subsystems, modules, components, classes)
  - Uses relationship (exports, imports)
  - Layers
  - Class inheritance
  - Object models
  - E-R diagrams
  - Responsibility
- Process, Component-and-Connector
  - Dynamic aspects
  - Process
  - Communication
  - Behaviour
  - Concurrency
  - Synchronization
  - Shared data or repository
  - Client-server
  - Error handling
  - Binding time
- Physical, Execution
  - Deployment (hardware, tasks, threads, processes, etc.)
- Development, Code
  - Static organization of files, folders, libraries, includes, etc. in the development environment
- Contextual – business analysis
- Conceptual – requirements
- Data design, input/output
- Operation
- Cross-cutting concerns
  - Caching
  - Configuration
  - Error detection/correction
  - Internationalization
  - Logging
  - Messaging
  - Monitoring
  - Persistence
  - Real-time constraints
  - Security (confidentiality, integrity, availability, authentication, authorization)
  - State management
  - Synchronization
  - Transactions
  - Validation

## Quality Attribute Tactics
### Availability Tactics
Fault detection tactics

- Ping/echo
- Heartbeat (dead man timer)
- Exceptions

Fault recovery tactics

- Voting
- Active redundancy (hot restart)
- Passive redundancy (warm restart, dual redundancy, triple redundancy)
- Spare
- Shadow operation
- State resynchronization
- Checkpoint/rollback

Fault prevention tactics

- Removal from service
- Transactions
- Process monitor

### Modifiability Tactics
Localize modifications tactics

- Maintain semantic coherence
- Anticipate expected changes
- Generalize the module
- Limit possible options

Prevent ripple effects tactics

- Hide information
- Maintain existing interfaces
- Restrict communication paths
- Use an intermediary

Defer binding time tactics

- Runtime registration
- Configuration files
- Polymorphism
- Component replacement
- Adherence to defined protocols

### Performance Tactics
Resource demand tactics

- Increase computational efficiency
- Reduce computational overhead
- Manage event rate
- Control frequency of sampling
- Bound execution times
- Bound queue sizes

Resource management tactics

- Introduce concurrency
- Maintain multiple copies of either data or computations
- Increase available resources

Resource arbitration tactics

- Scheduling policy

### Security Tactics
Resisting attacks tactics

- Authenticate users
- Authorize users
- Maintain data confidentiality
- Maintain integrity
- Limit exposure
- Limit access

Detecting attacks tactics

- Intrusion detection system through network

Recovering from attacks tactics

- See availability tactics for restoration
- Maintain an audit trail for identification

### Testability Tactics
Input/Output tactics

- Record/playback
- Separate interface from implementation
- Specialize access routes/interfaces

Internal monitoring tactics

- Built-in monitors

### Usability Tactics
Runtime tactics

- Support user initiative (cancel, undo, aggregate, show multiple views)
- Support system initiative (maintain a model of the task, the user, the system)
Design-time tactics
- Separate the user interface from the rest of the application

## Architectural Patterns
### Domain Layer Patterns
Transaction Script

- Organize business logic by procedures where each procedure handles a single request from the presentation

Domain Model

- An object model of the domain that incorporates behaviour and data
Table Module
- An instance of a class that represents a database table (or view) and handles the business logic for all the rows

Service Layer

- The boundary of the application that exposes operations and coordinates the application’s response to each operation

### Data Layer Patterns
Gateway

- Wraps a complex API to create a simple API for a specific usage

Table Data Gateway

- An object (Façade) that wraps a specific database table where one instance handles all the rows in the table

Row Data Gateway

- An object that wraps a single row in a specific database table (or view)
- Encapsulates database access
- No domain logic included

Active Record

- An object that wraps a single row in a specific database table (or view)
- Encapsulates database access
- Adds domain logic on that data

Mapper

- An object that sets up communication between 2 independent objects
- The independent objects do not depend on any  of the other components

Data Mapper

- A Mapper layer that moves data between in-memory data objects and a database
- The data objects and database remain independent (no dependencies)
- Put methods needed by the domain code into an interface referenced by the domain package

### Object-Relational Data (Behavioural) Patterns
Unit of Work

- Maintains a list of objects affected by a business transaction
- Opens a database transaction
- Does any concurrency checking
- Coordinates the writing out of changes to the database
- Handles any concurrency problems
- Can be provided by a Registry

Identity Map

- Keeps every loaded object in a map to ensure that each objects gets loaded only once
- Looks up objects using the map when referring to them
- Can be provided by a Registry

Lazy Load

- An object that doesn’t contain all the data but knows how to get the rest

### Object-Relational Data (Structural) Patterns
Identity Field

- Saves a database key field in an object to maintain identity between the in-memory object and a database row

Foreign Key Mapping

- Maps an object association to a database foreign key

Association Table Mapping

- Saves a many-to-many association to a separate table containing foreign keys

Dependent Mapping

- One class that is composed of instances of another class maps its children to the database

Embedded Value

- Maps a small object field into several fields of the parent object’s database table

Serialized LOB

- Saves a graph of objects by serializing them into a single large object (LOB) and is stored in a single database field

Single Table Inheritance, Table per Hierarchy

- Represents an inheritance hierarchy of classes as a single table that has columns for all the fields of the various classes

Class Table Inheritance, Table per Type

- Represents an inheritance hierarchy of classes with one table for each class

Concrete Table Inheritance, Table per Concrete Type

- Represents an inheritance hierarchy of classes with one table per concrete class in the hierarchy

Inheritance Mappers

- A structure to organize database mappers that handle inheritance hierarchies

### Object-Relational Data (Metadata) Patterns
Metadata Mapping

- Holds details of object-relational mapping

Query Object

- An object that represents a database query

Repository

- Mediates between the domain and data mapping layers using a collection-like interface for accessing domain objects
- Can help minimize duplicate query logic
- Provides a more object-oriented view of the persistence layer

### Presentation Layer Patterns for MVC
Model View Controller

- Splits user interface interaction into 3 distinct roles

Page Controller

- An object that handles a request for a specific page or action on a web site

Front Controller

- A controller that handles all requests for a web site

Template View

- Renders information into HTML by embedding markers (executable, interpretable) in an HTML page

Transform View

- A view that transforms domain data into HTML

Two Step View

- Turns domain data into HTML in 2 steps
- First step is forming some kind of logical page without any specific formatting
- Second step is rendering the logical page into HTML

Application Controller

- Handles screen navigation and application flow
- Provides controllers the appropriate commands for execution against the model and the correct view to use depending on the application context

### Distribution Patterns
Remote Façade

- Provides a coarse-grained façade on fine-grained objects to improve efficiency over a network

Data Transfer Object

- An object that carries data between processes in order to reduce the number of method calls

### Offline Concurrency Patterns
Optimistic Offline Lock

- Prevents conflicts between concurrent business transactions by detecting a conflict and rolling back the transaction

Pessimistic Offline Lock

- Prevents conflicts between concurrent business transactions by allowing only one business transaction at a time to access data

Coarse-Grained Lock

- Locks a set of related objects with a single lock

Implicit Lock

- Allows framework or layer supertype code to acquire offline locks
- Locking tasks that cannot be overlooked should be handled implicitly by the application

### Session State Patterns
Client Session State

- Stores session state on the client
- Bad for a large amount of data
- Bad for secure data

Server Session State

- Keeps the session state on a server system in a serialized form
- Requires serializing state to a shared store for clustering or failover

Database Session State

- Stores session data as committed data in the database
- State is stored in tabular form

### General Patterns
Layer Supertype

- A type that acts as the supertype for all types of the same kind in its layer

Separated Interface

- Defines an interface in a separate package from its implementation

Registry, Service Locator

- A well-known object that other objects can use to find common objects and services
- Eliminates the need to pass an object several layers down a call stack
- Thread-specific objects can be used to prevent concurrency problems
Plugin
- Links classes during configuration rather than compilation

Service Stub

- Removes dependency upon problematic services during testing

Record Set

- An in-memory representation of tabular data
- Provided by the framework, such as DataSet

### Structure Patterns
Layers

- Helps to structure applications that can be decomposed into groups of subtasks where each group is at a particular level of abstraction
- Organizes low- and high-level operations
- Define level criteria, not too many or too few layers, name layers and assign tasks, specify larger services for higher level and smaller services for lower level, specify the interfaces, structure content of each layer, specify layer communication, decouple layers, design error-handling strategy

Pipes & Filters

- A structure for systems that process a stream of data
- Divides the overall task into several sequential processing steps
- Each processing step is encapsulated in a filter component
- Data is passed through pipes between adjacent filters
- Recombining filters allows you to build families of related systems

Blackboard

- Useful for problems for which no deterministic solution strategies are known
- Several specialized independent subsystems assemble their knowledge to build a possibly partial or approximate solution
- Partial solutions are combined, changed, or rejected at multiple levels of abstraction
- The blackboard is the central data store
- Knowledge sources read from and write to the blackboard
- The control component monitors the blackboard and schedules knowledge source valuations according to a strategy

### Distributed Systems Patterns
Broker (SOA)

- Structures distributed software systems with decoupled components that interact by remote service invocations
- Each broker is responsible for coordinating communication, such as forwarding requests, as well as for transmitting results and exceptions
- Service oriented architecture
- Brokers act as a service bus which interact with client-side and server-side proxies

### Interactive Systems Patterns
Presentation-Abstraction-Control

- A hierarchy of cooperating agents
- Each agent is responsible for a specific aspect of the application’s functionality
- Each agent consists of three components: presentation, abstraction, and control
- The control component connects the presentation and abstraction components, and allows the agent to communicate with other agents
- One top-level agent, several intermediate-level agents, many bottom-level agents
- The top-level agent provides the functional core
- The bottom-level agents represent self-contained concepts that users can act on
- The intermediate-level agents represent combinations of or relationships between bottom-level agents
- Use when the atomic concepts are large and each require their own interaction design

Model-View-Presenter

- User gestures are handed off by the widgets to a presenter
- The presenter coordinates changes in a domain model
- One version factors the UI into a view and controller where the view handles simple mapping to the underlying model and the controller handles input response and complex view logic
- Another version has passive views that invoke a generic method on the presenter which retrieves data from the view, accesses the model, and updates the view with changes

Model-View-ViewModel (MVVM)

- The View knows about the ViewModel and binds to it
- The ViewModel knows about the Model and subscribes to changes
- View defines screen formatting with no business logic
- Model implements domain model including data, business, and validation logic
- ViewModel handles the view logic, invokes model methods, formats model data, implements user commands

### Adaptable Systems Patterns
Microkernel

- Applies to software systems that must be able to adapt to changing system requirements
- Separates a minimal functional core from extended functionality and customer-specific parts
- A socket for plugging in extensions and coordinating their collaboration
- The microkernel provides communication and low-level services
- Other components include internal and external servers, adapters, and clients

Reflection

- For adaptable systems
- A mechanism for changing structure and behaviour of software systems dynamically
- Supports the modification of fundamental aspects such as type structures and function call mechanisms
- A meta level part and a base level part
- The meta level provides information about selected system structure and behaviour making the software self-aware
- The base level includes the application logic and uses the information provided by the meta level




# References
Bass, Len, et al. *Software Architecture in Practice, Second Edition*. Addison-Wesley, 2003.

Buschmann, Frank, et al. *Pattern-Oriented Software Architecture: A System of Patterns*. Wiley, 1996.

Fowler, Martin, et al. *Patterns of Enterprise Application Architecture*. Addison-Wesley, 2002.

House, Cory. *Architecting Applications for the Real World in .NET*, [PluralSight](http://www.pluralsight.com/courses/architecting-applications-dotnet), 2014.

Simmons, Chris. *Developer to Architect*, [PluralSight](http://www.pluralsight.com/courses/developer-to-architect), 2013.

Smith, Steve. *Creating N-Tier Applications in C#*, [PluralSight](http://www.pluralsight.com/courses/n-tier-apps-part1), 2012.
