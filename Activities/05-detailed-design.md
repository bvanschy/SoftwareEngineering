# Detailed Design

Performed by the “Application architect” or “Lead developer” role.

Low-level components in design:

- Do not affect overall system structure and behaviour
- Affect component structure and behaviour

## Best Practices

- Small interfaces and classes
- Reusable (abstract and stable)
- Changeable (flexible and concrete)

## Principles
- Single responsibility principle
  - A class should have only one reason to change
- Open/closed principle
  - Open for extension but closed for modification
- Liskov substitution principle
  - Subtypes must be substitutable for their base types
  - Methods not implemented in the derived type is a smell
- Interface segregation principle
  - Clients should not be forced to depend on methods they do not use
- Dependency inversion principle
  - High-level modules do not depend on low-level modules, both depend on abstractions
  - Abstractions should not depend on details, details should depend on abstractions
- You Aren’t Gonna Need It (YAGNI)
- Robustness principle (Postel’s law)
- Don’t Repeat Yourself (DRY)
- Principle of Least Surprise / Least Astonishment
- Keep it simple (KISS)

## Design Patterns
### From Mud to Structure
Interpreter

- Given a language, define a representation for its grammar along with an interpreter that uses the representation to interpret sentences
- Every regular expression defined by the grammar is represented by an abstract syntax tree

Rules Engine

- Production Rule System organizes logic through a set of production rules, each having a condition and an action

### Creation
Abstract Factory

- Provides an interface for creating families of related or dependent objects without specifying their concrete classes

Prototype

- Specify the kinds of objects to create using a prototypical instance, and create new objects by cloning this prototype
- Reduces the number of classes

Builder

- Separate the construction of a complex object from its representation so that the same construction process can create different representations

Singleton

- Ensures a class only has one instance, and provides a global point of access to it

Factory Method

- Defines an interface for creating an object, but makes factory subclasses decide which class to instantiate
- Allows a class to defer instantiation to factory subclasses

### Structural Decomposition
Whole-Part

- Helps aggregate components that together form a semantic unit
- The Whole encapsulates its constituent components, the Parts, organizes their collaboration, and provides a common interface to its functionality
- Direct access to the Parts is not possible

Composite

- Compose objects into tree structures to represent part-whole hierarchies
- Clients treat individual objects and compositions of objects uniformly

### Organization of Work
Master-Slave

- Supports fault tolerance, parallel computation, and computational accuracy
- A master component distributes work to identical slave components and computes a final result from the results of the slaves

Chain of Responsibility

- Avoid coupling a sender of a request to its receiver by giving more than one object a chance to handle the request
- Chain the receiving objects and pass the request along the chain until an object handles it

Command

- Encapsulates a request as an object
- Allows you to parameterize clients with different requests and queue or log the requests
- Supports undoable operations

Mediator

- An object that encapsulates how a set of objects interact
- Promotes loose coupling by keeping objects from referring to each other explicitly
- Allows you to vary their interaction independently

Active Object

- Decouples method execution logic from method invocation scheduling
- Simplifies synchronized access to an object that resides in its own thread of control
- Commonly used in multi-threaded distributed systems

### Access Control
Proxy

- Makes the clients of a component communicate with a representative rather than to the component itself
- Can enhance efficiency, easier access, and protection from unauthorized access

Façade

- Provides a unified interface to a set of interfaces in a subsystem
- Defines a higher-level interface that makes the subsystem easier to use

Iterator

- Provides a way to access elements of an aggregate object sequentially without exposing its underlying representation

### Service Variation
Bridge

- Decouples an abstraction hierarchy from its implementation hierarchy so that the two can vary independently

Strategy

- Defines a family of algorithms, encapsulates each one, and make them interchangeable
- Allows the algorithm to vary independently from clients that use it

State

- Allows an object to alter its behaviour when its internal state changes
- The object will appear to change its class

Template Method

- Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses
- Subclasses can redefine certain steps of an algorithm without changing the algorithm’s structure

Null Object

- Provides an object as a surrogate for the lack of an object of a given type
- Provides intelligent “do nothing” behaviour, hiding the details from its collaborators

### Service Extension
Decorator

- Attaches additional responsibilities to an object dynamically
- Provides a flexible alternative to subclassing for extending functionality

Visitor

- Represents an operation to be performed on the elements of an object structure
- Allows you to define a new operation without changing the classes of the elements on which it operates

Extension Object

- Each object in the hierarchy maintains a list of extension objects that can be retrieved by name
- The extension object provides methods that manipulate the original hierarchy object

### Management
Command Processor

- Separates the request for a service from its execution
- Manages requests as separate objects, schedules their execution, and provides additional services such as the storing of request objects for later undo

View Handler

- Helps to manage all views
- Allows clients to open, manipulate, and dispose of views
- Coordinates dependencies between views and organizes their update

Memento

- Captures and externalizes an object’s internal state so that the object can be restored to this state later

### Adaptation
Adapter

- Converts the interface of a class into another interface that clients expect
- Allows classes to work together that couldn’t otherwise because of incompatible interfaces

### Communication
Publisher-Subscriber, Observer

- Helps to keep the state of cooperating components synchronized
- Enables one-way propagation of changes: one publisher notifies any number of subscribers about changes to its state

Forwarder-Receiver

- Provides transparent inter-process communication for software systems with a peer-to-peer interaction model
- Introduces forwarders and receivers to decouple peers from the underlying communication mechanisms

Client-Dispatcher-Server

- Introduces a Dispatcher as an intermediate layer between clients and servers
- Provides location transparency by means of a name service, and hides the details of the establishment of the communication connection between clients and servers

Event Aggregator

- Channels events from multiple objects into a single object to simplify registration for clients
- Responds to any event from a source object by propagating that event to the target objects

### Resource Handling
Flyweight

- Uses sharing to support large numbers of fine-grained objects efficiently

### Other
Monostate

- Enforces singular behaviour among multiple instances

## Domain-Driven Design
Ubiquitous Language

- Common terminology/semantics between development team and domain experts

Modeling paradigm

- Connect model with implementation
- Object-oriented programming

Domain layer

- Contains the domain model implementation

Associations

- Unidirectional association to simplify
- Qualifier to simplify (dictionary instead of list)
- Eliminate association to simplify

Entity object

- An object defined by its identity and continuity
- Reduce definition to key and parameters used to query

Value object

- An object defined by its attributes
- No identity
- Treated as immutable

Service object

- A domain operation not naturally part of an Entity or Value
- Defined in terms of domain elements
- Stateless

Module, Package

- High cohesion, low coupling
- Named from the ubiquitous language

Aggregate

- Group of objects with one root Entity
- Access through root only
- Non-root Entities are locally unique
- Delete entire aggregate at once
- Invariants apply to entire aggregate

Factory

- Responsible for creating complex objects and Aggregates
- Outside objects being created
- Inside owner of created objects or a dedicated Factory object or Service

Repository

- For each type of object needing global access
- Encapsulate data store access
- Intention-revealing interface
- Can support specification-based queries in addition to hard-coded queries

Constraint

- Model a constraint through separate object(s)

Process

- Model a process through Service or Strategy objects

Specification

- Predicate-like value objects that determines if an object satisfies some criteria
- For validating
- For querying
- For creating

Analysis patterns

- Reusable object models

Large, complex models

- Maintain integrity through contexts, boundaries, and relationships
- Distillation – extract the essence
- System structure of modules

Best practices

- Intention-revealing interfaces
- Side-effect-free functions
- Assertions
- Conceptual contours – underlying consistency in the domain
- Standalone classes
- Closure of operations – type of result is the same as the type of arguments
- Declarative design


# References
Evans, Eric. *Domain-Driven Design*. Addison-Wesley, 2003.

Fowler, Martin. *UML Distilled Third Edition*. Addison-Wesley, 2004.

Gamma, Erich, et al. *Design Patterns*. Addison-Wesley, 1995.

Martin, Robert C. and Micah, Martin. *Agile Principles, Patterns, and Practices in C#*. Prentice Hall, 2006.

Seemann, Mark. *Encapsulation and SOLID*, [PluralSight](http://www.pluralsight.com/courses/encapsulation-solid), 2014.

Smith, Steve. *SOLID Principles of Object Oriented Design*, [PluralSight](http://www.pluralsight.com/courses/principles-oo-design), 2010.

Smith, Steve, et al. *Design Patterns Library*, [PluralSight](http://www.pluralsight.com/courses/patterns-library), 2010.

