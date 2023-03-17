## UML

**Why Modelling?** Communicate ideas effectively, Understand a codebase, Improve design

**What is UML**

- modelling language, not a method
- Used to provide abstraction for OO design. Forward design - before writing code. Backward design - after writing code
- can be used as a programming language
- open standard
- still evolving

**Types of UML diagrams**

- structural: static view of the system e.g Class Diagram, Package Diagram
- behavioural: dynamic view of the system i.e Use Case diagram, state diagram

**Class Diagram**

- Class diagram describes the classes in an object-oriented system and the various kinds of static relationships among them
- The following relationships can be represented in class diagrams
    - Association (aggregation, composition, dependency)
    - generalization (inheritance, Implementation
- **Classes** - represented as rectangles  containing three compartments
    - Class Name, attributes, operations
    - The visibility of attributes/operations can be specified using the symbols
        - + Public
        - - private
        - # protected
        - ~ default/package
- **Association** - represented as a link that might be augmented with information like name, direction, multiplicity, role names
- **Association Types**
    - **Aggregation**: corresponds to an “is part of” relationship (represented by a white diamond)
    - **Composition**: a strong form of aggregation (represented by a black diamond)
    - **Dependency**: used to indicate that changing one element might lead to changing another one (represented by a dashed line/arrow)
- **Generalization**  - represented using an open arrow pointing toward the parent class/interface
    - For interfaces, <<interface>> is written above the interface name and a dashed line is used for the arrow
    - Abstract classes, interfaces, abs methods are written in italic font

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e81285e-51ae-42c0-b542-af6ffe9a626a/Untitled.png)

**Use Case** - functional req of a system and what it should do by modelling interactions between the users and system

- Consists of set of scenarios tied together by common user goals
- A scenario is a sequence of steps describing an interaction between a user and a system
- Usually, a use case has a common all-goes-well case, and many alternatives that may include things going wrong and also alternative ways that things go well
- Does not indicate how behaviour is implemented

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/385b91ca-12be-41de-8b90-4c87697b50a3/Untitled.png)

**Use Case Diagram**

- UML diagram that mainly consists of actors and use cases
    - Actors do not have to be human
    - Single actor may perform several use cases and a use case may have several actors performing it
- Models relationships between use cases
    - Include: use when some behaviour is similar across more than one use case
    - Generalization: Used when a use case is similar to another one but does a bit more
    - Extend: Similar to Generalization but with more rules to it. The extending use case may add behaviour only at the specific extension point declared in the base use case
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d01da037-3b8c-44c5-8d61-13eb301729b8/Untitled.png)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/308a8ce0-ec58-4d9c-b699-a2a27ab3e154/Untitled.png)
    

**Interaction Diagram**

- Typically an interaction diagram captures the behaviour of a single use case. The diagram shows a number of example objects and the messages that are passed between these objects within the use case
- Two types of interaction diagrams - sequence and collaboration

**Sequence Diagram**

- objects are shown as boxes at the top of dashed vertical lines called lifelines
- Each message is represented by an arrow between the lifelines of two objects. The order in which these messages occur is shown top to bottom on the page. Control information can be added to messages:
    - Condition: indicates that the message is sent only if the condition is true
    - Iteration marker: shows that a message is sent many times to multiple receiver objects (e.g. iterating over a list).
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dad14666-66ab-44ce-ba7d-507d27a675b7/Untitled.png)
    

### Software Architecture

**What is Software Architecture?**
“The software architecture of a system is the set of structures needed to reason about the system, which  comprise software  elements, relations among them, and properties of both.”

**Architectural Structures**

- Set of elements held together by a relation. Supports reasoning about an attr of the system that is important to some stakeholder
- Three Categories of Structures
    - Module: represent a partitioning of the system into implementation units or modules i.e database module, UI module, etc
    - Component-and-connector structures: represent runtime components and communication vehicles among them
    - Allocation structures: represent the relationship between the system and non-software structures in its environment (e.g. hardware, dev teams)

**Architectural Pattern** 

- Establishes a relationship between a context, problem, and solution
- Often based on quality attributes that must be met i.e Availability, interoperability, modifiability, performance, security, testability, portability

**Modifiability**

- The ease with which change can be made to the system
- Software change is common i.e adding new feat, fix a bug, improve performance.
- Coupling: the probability that a modification to one module will propagate to another
- Cohesion: the measure of how strongly the responsibilities of a module are related
- Modifiability is promoted by low coupling and high cohesion.

**Architectural Pattern Types**

- Module-based  patterns i.e. Layered
- Component-and-connector pattern i.e. Client-Server
- Allocation patterns i.e multi-tier

Layered Pattern

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3bcd4ef4-d1ca-432b-8920-6d131cc0ddff/Untitled.png)

- context: with complex systems there is a need to develop and evolve portions independently
- Problem: software needs to be segmented in a way that promotes portability and modifiability
- Solution: software divided into layers
    - each layer is a grouping of modules that offers a cohesive set of services
    - every piece of software is allocated to exactly one layer
    - closed architecture, only next lower layer uses are allowed
    - open architecture a layer can use services from any lower layer
- Weaknesses
    - Upfront cost and complexity
    - Layers contribute a performance penalty

**Broker Pattern**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26bfe2f0-820f-479f-b4b8-cb85e925ee85/Untitled.png)

- Context: Many systems are constructed from a collection of services distributed across mutliple services
- Problem: How do we structure distributed software so that clients do not need to know the nature of location of service providers
- Solution: insert intermediary called broken between clients and servers
- Benefits: modifiability, availability
- Weaknesses: complexity, latency

**Model View Controller**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/557692f0-c94c-4633-883a-e729be699c69/Untitled.png)

- Context: User interface software is typically the most frequently modified portion of an interactive application
- Problem: How can UI func be separated from App func and still be responsive to UI or changes to underlying app data
- Solution: Separate app function into 3 components
- Model - manages app data, view produces a rep of the model, controller translates user actions into model changes or views changes.
- May be many views/controllers associated with a model
- MVC has several variants
- weakness: not suitable for all UI toolkits

**Pipe and Filter**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b07f93b0-49ca-41ef-94e7-e3ab7ca08b05/Untitled.png)

- Context: many systems are required to transform streams of data from input to output
- Problem: some systems have to be divided into reusable, loosely, coupled components with simple and generic interaction mechanisms
- Solution: Data undergoes a series of transformations performed by a series of filters connected by pipes. Filters typically do not know the identity of their upstream or downstream filter
- Weaknesses: computational overhead, not suitable for interactive systems

**Client Server Pattern**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a2d5f85-5eda-44ac-9ab5-98ac5c75bff9/Untitled.png)

- Context: there are shared resources and services a large number of distributor clients wish to access
- Problem: how to manage the shared resources and services well, promoting modifiability and reuse
- Solution:  clients interact by requesting services of service, which provide a set of services.
    - Some components may act as both clients and servers.
    - There may be one central server or multiple distributed ones
- Weaknesses: single point of failure, the server can be a performance bottleneck

**Peer-to-Peer**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14d3aff9-271c-476e-9a7e-6abe71227830/Untitled.png)

- Context: distributor competition entities need to cooperate and collaborate to provide a service to a distributed community of users
- Problem: how can a set of equal distributor computational entities be connected to each other by a common protocol so they can organize and share their services with high availability and scalability?
- Solution: Peer to peer communications typically request replying erection without the asymmetry found in client/server
    - Any component canon principal interact with any other component by requesting its services
    - Appear to Pierre architecture may have specialized peer nodes called supernodes that have indexing or routing capabilities
- Weakness: managing issues such a security and data consistency is challenging, no guarantees in terms of quality goals

**Service-Oriented Architecture Pattern**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4cae66e3-0e3a-4173-abef-2fa955ee3313/Untitled.png)

- Context: a number of services are offered by service providers and consumed by service consumers
- Problem: How can we support the interoperability of distributed components running on different platforms, written in different implementation languages, provided by different organizations, and distributed across the Internet?
- Solution: Components have interfaces that describe the services they request from other components and the services they provide. Components achieve their computation by requesting services from one another.

- Components -Service providers/consumers, enterprise service bus (basically a broker), registry of services, orchestration server
- Connectors - SOAP, REST, Async messaging connector
- Benefits: Interoperability, Reusability
- Weakness: Design & Implementation complexity, performance overhead of the middleware

### Design Principles

**SOLID Design**

- **Single Responsibility Principle** - A class should have one reason to change
- **Open-Closed Principle** - Software entities should be open for extension but closed for modification
- **Liskov Substitution Principle** - Subtypes must be substitutable for their base types.
- **Interface Segregation Principle** - Clients should not be forced to depend on methods that they do not use
- **Dependency Inversion Principle** - High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

**What is a design pattern?**

- description of communicating objects and classes that are customized to solve a general design problem in a particular context
- Gamma et al. described 23 design patterns divided into three categories: Creational, Structural, Behavioural patterns

**Creational Patterns** - Concern the process of object creation

- **Factory Methods**: Make objects based on input.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f07aead8-eb88-4c30-85e3-a5a3dcb6e4e4/Untitled.png)
    
- **Abstract Factory**: Group similar objects together.
- **Singleton**: Limit a class to one instance.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9e196a0b-8b3b-4aee-b7fd-35c37f842a0f/Untitled.png)
    
- **Prototype**: Copy existing objects to make new ones.
- **Builder**: Create complex objects step-by-step.
- **Object Pool:** Reuse objects instead of creating new ones.

**Structural Patterns** - Deal with the composition of classes or objects

- **Adapter**: Make different interfaces work together.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/13717345-ac17-4d92-b679-392487efa5c3/Untitled.png)
    
- **Bridge**: Decouple abstractions and implementations.
- **Composite**: Create tree structures for objects, allowing clients to treat single objects and groups uniformly.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c95d7d1-edf2-42dc-87be-541eec85ea5b/Untitled.png)
    
- **Decorator**: Add responsibilities to objects without changing their structure.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9aad9210-f977-4f4a-8de6-cdf2e5f7d39f/Untitled.png)
    
- **Facade**: Simplify a complex system with a single, high-level interface for easier use.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d206ff91-4d13-4971-bc9a-c3af73b1b329/Untitled.png)
    
- **Flyweight**: Share common data to save resources.
- **Proxy**: Use an object to control access to another.

**Behavioural Patterns-** Characterize the ways in which classes or objects interact and distribute responsibility

- **Chain of Responsibility**: Pass requests along a chain of handlers.
- **Command**: Turn requests into objects, enabling parameterization, queuing, logging, and undoable actions.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75913ca7-4327-4c92-8cfb-d62782c6ad1d/Untitled.png)
    
- **Interpreter**: Access elements in a collection one-by-one without revealing its structure.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a2aff29a-552f-41b6-a2db-6378a0a18f91/Untitled.png)

- **Iterator**: Access elements in a collection sequentially.
- **Mediator**: Centralize communication between objects.
- **Memento**: Save and restore object states.
- **Observer**: Notify objects of state changes.
- **State**: Change object behaviour based on state.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/723de8f7-16cd-4482-93b9-c59d023bfe1c/Untitled.png)
    
- **Strategy**: Encapsulate algorithms, make them swappable, and allow clients to use them independently
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/036f8c46-03b5-46e0-9226-8f2a2cc6091d/Untitled.png)
    
- **Template Method:** Set an algorithm's structure, allowing subclasses to modify specific steps without changing the overall framework.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4e31448-636a-45c1-bf7f-b754b7e05092/Untitled.png)
    

### Refactoring

Refactoring is the process of changing a software system in such a way that it does not alter the external behavior of the code, yet improves its internal structure.

Advantages of refactoring:

- Improving software design
- Making software easier to understand
- Finding bugs more easily
- Speeding up development

How to: apply changes in sequence of small steps, do not add new functionality, make sure all existing tests pass & add new ones if needed

**Extract Method**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d1f393e9-1ec9-47b4-8f21-41d0bb631a8f/Untitled.png)

******************************************************************Replace Method with Method Object:****************************************************************** Long method that uses local var in a way so you can’t apply Extract Method. Turn method into own obj so all local var become fields, then decompose the method into other methods in same obj

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/27254a53-8081-489a-84fe-987593e7bd67/Untitled.png)

********************************************************************Consolidate Conditional Expression:******************************************************************** Combine sequence of conditional tests with same result into single conditional exp and extract it

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d560bc22-86c1-4116-855c-0ceecb23f2bf/Untitled.png)

**Consolidate Duplicate Conditional Fragments:** The same fragment of code is in all branches of a conditional expression. Move it outside of exp

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/58b844a8-d55e-43fb-a34d-22b659988a89/Untitled.png)

**Remove Control Flag**: Use a break or return instead of a variable acting as a control flag for a series of Boolean expressions.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/decf34bb-8cde-416c-9439-cd8df0a91d0c/Untitled.png)

**Replace Nested Conditional with Guard Clauses:** Use guard clauses for all the special cases when a method has conditional behavior that does not make clear the normal path of execution. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbd7a00d-8cd5-4453-ad21-553c6b2daadf/Untitled.png)

**Replace Magic Number with Symbolic Constant:** Create a constant with a name that reflects its meaning to replace a literal number that has a specific significance.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1013e3d6-799d-4f1a-86f6-b09498ff57e4/Untitled.png)

**Encapsulate Field**: Make a public field private and provide accessors.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c4b6d28-07c3-4e66-8b13-ffce56f0efe9/Untitled.png)

**Encapsulate Collection:** Make a method return a read-only view of a collection and provide add/remove methods.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc1c41c1-8448-4128-bf4f-f64370887b40/Untitled.png)

**Parameterize Method**: Create one method that uses a parameter for different values contained in several methods that do similar things but have different values in their method bodies.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0796d6a0-7585-45f5-8ef5-8b4ae13e4af1/Untitled.png)

**Replace Parameter with Explicit Methods**: Create a separate method for each value of an enumerated parameter that runs different code depending on its value. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6149e54f-abb2-4e42-b439-170beceef4a5/Untitled.png)

**Introduce Explaining Variable**: Put the result of a complicated expression or parts of it in a temporary variable with a name that explains its purpose. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a93d4f3b-fff4-48f3-b921-9dd04914b484/Untitled.png)

**Extract Class:** Create a new class for work that should be done by two classes, and move relevant fields and methods from the old class to the new class.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/247f82ea-3dc0-4cf8-8846-439510975386/Untitled.png)

**Extract Superclass:** Create a superclass for two classes with similar features and move common features to the superclass.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cde32843-56fd-4fa3-86c9-6c3e46deb3c5/Untitled.png)

**Extract Subclass:** Create a subclass for features that are used only in some instances.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4ffd75f4-1404-4058-afbc-36736012843e/Untitled.png)

**Pull up Field/Method:** Move methods with identical fields/methods to the superclass.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8b6efb8b-44ef-49fb-b841-b8ebccabf516/Untitled.png)

**Push down Field/Method:** Move fields/methods of a superclass relevant only for some of its subclasses to those subclasses.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a8668b43-7b79-47d5-9439-d87cf74156d6/Untitled.png)

**Replace Inheritance with Delegation:** Create a field for the superclass, adjust methods to delegate to the superclass, and remove the subclassing if a subclass uses only part of a superclass or does not need to inherit data.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4eab383d-8241-431f-b5ce-9733ff127fa2/Untitled.png)

**Replace Delegation with Inheritance:** Using delegation and writing many simple delegations for the entire interface. Make the delegating class a subclass of the delegate

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c051c994-03df-4483-9158-1b8320e18430/Untitled.png)

**Replace Conditional with Polymorphism:** Having a conditional that chooses different behavior depending on the type of an object. Move each leg of the conditional to an overriding method in a subclass. Make the original method abstract.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4077b48-06dc-4657-939a-ea45f713c7bd/Untitled.png)

**Introduce Null object:** Repeated checks for a null value. Replace the null value with a null object.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4329f364-4c62-4c2c-b5d5-95a7c762c182/Untitled.png)

**Tease Apart Inheritance:** An inheritance hierarchy that is doing two jobs at once. Create two hierarchies and use delegation to invoke one from the other.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b68b8128-6a99-48b3-bc01-9b785d2ac5b7/Untitled.png)

**Code Smells**

A structure in the code that indicates a potentially deeper problem. In many cases, a code smell (and the underlying problem) can be addressed by refactoring.

**Duplicated Code**: The same code structure repeated in more than one place. Relevant refactorings include: Extract method, Extract class, Pull up field/method.

**Long Method**: The longer a method is, the more difficult it is to understand and maintain. Relevant refactorings include: Extract method, Replace method with method object.

**Large Class:** Classes that have too much to do might result in duplicated code. Relevant refactorings include: Extract class, Extract subclass.

**Long Parameter List**: Long parameter lists are difficult to understand and use, and they might become inconsistent. Relevant refactorings include: Replace parameter with method.

**Divergent Change**: One class is commonly changed in different ways for different reasons. Relevant refactorings include: Extract class.

**Feature Envy:** A method seems more interested in a class other than the one it is in (e.g. a method that invokes many getter methods on another object to calculate some value). Relevant refactorings include: Extract method.

**Data Clumps:** The same data items are used together in a lot of places. Relevant refactorings include: Extract class.

**Switch Statements:** The problem with switch statements is essentially that of duplication. Relevant refactorings include: Extract method, Replace conditional with polymorphism, Replace parameter with explicit methods, Introduce null object.

**Inappropriate Intimacy:** Two classes know too much about each other. Relevant refactorings include: Extract class, Replace inheritance with delegation.

**Refused Bequest:** A subclass inherits data/method(s) that it does not need. Relevant refactorings include: Push down field/method.

**Excessive commenting**: Excessive commenting might be a sign of poorly-written code. Relevant refactorings include: Extract method.

### Software Processes

What is a Software Process?

- A software process is a roadmap that helps deliver a high-quality product on time. It incorporates five framework activities: Communication, Planning, Modeling, Construction, Deployment.

**Linear** Process Flow: Communication → Planning → Modelling → Construction → Deployment →

**Iterative**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/db1aac14-dad2-454c-878a-1860c530f46a/Untitled.png)

**Evolutionary**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e6ce2995-5cb0-4cbd-a8e8-65abc234ef21/Untitled.png)

**Parallel** 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e15a488-fe4b-411e-91b0-154d09bb8ae6/Untitled.png)

Process Models - Different software process models can accommodate the generic framework activities, but each applies a different emphasis to these activities and defines a process flow.

**The Waterfall Model**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09d25d81-6d93-4a9b-aa97-09a85bc6e3b8/Untitled.png)

- Advantages:
    - It is easy to understand and plan
    - It works for well-understood small projects
    - Analysis and testing are straightforward
- Disadvantages:
    - It does not accommodate change well
    - Testing occurs late in the process
    - Customer approval is at the end

The Prototyping Model

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/da5d30f0-6303-4765-822f-e037d3407b93/Untitled.png)

- **Advantages**:
    - There is a reduced impact of requirement changes
    - The customer is involved early and often
    - It works well for small projects
    - There is reduced likelihood of product rejection
- **Disadvantages**:
    - Customer involvement may cause delays
    - There may be a temptation to “ship” a prototype
    - Work is lost in a throwaway prototype
    - It is hard to plan and manage

**The** **Spiral Model**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8515ee6-76b2-43cf-82d1-fc30e9db9df2/Untitled.png)

- Advantages:
    - There is continuous customer involvement
    - Development risks are managed
    - It is suitable for large, complex projects
- Disadvantages:
    - Risk analysis failures can doom the project
    - The project may be hard to manage
    - It requires an expert development team

**Agile Models - Scrum**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c6569fb-7c1c-426c-8457-43adba05b387/Untitled.png)

Scrum is one of the most popular agile methodologies. Development proceeds by breaking the project into a series of incremental prototype development periods 2 to 4 weeks in length called sprints. Scrum team consists of a Product owner, Scrum master, and Development team. Scrum artifacts are Product backlog, Sprint backlog, and Code increment.

- Advantages:
    - Higher productivity
    - Continuous involvement of the customer
    - Delivering working software in short iterations
    - Adaptable to changing requirements
- Disadvantages:
    - It might be difficult to control the cost of changes
    - It may not be suitable for large teams
    - It requires expert team members

Agile Models - **Extreme Programming (XP)**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d744ce8b-6cba-49d5-a550-4b0f770bb125/Untitled.png)

Planning: Customers and developers work together to decide how to group stories into the next release.

Design: CRC cards

Coding: Pair programming

Testing: Unit tests (implemented using a framework that enables automation) / Acceptance tests

Advantages:

- It emphasizes customer involvement
- It promotes software quality
- It reduces the cost of fixing issues

Disadvantages:

- There is a dependence on highly skilled team members
- It might not be suitable for large projects
- Minimal documentation

Agile Models - **Kanban**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b5658c4-8d30-4d31-9e12-0726d7c32f3e/Untitled.png)

Kanban is focused on change management and service delivery. It depends on six core practices:

- Visualizing workflow using a Kanban board
- Limiting the amount of work in progress (WIP) at any given time
- Managing workflow to reduce waste
- Making process policies explicit
- Focusing on continuous improvement
- Making process changes collaboratively and involving all team members and other stakeholders as needed

The basis of the daily Kanban standup meeting is a task called “walking the board,” which involves reviewing the progress of work on a Kanban board.

Advantages:

- It allows for early product delivery
- Process policies are written down
- There is continuous process improvement

Disadvantages:

- Less emphasis on planning and testing than other methodologies
- Flexibility can cause developers to lose focus
- Developer reluctance to use measurement

Agile Models - **DevOps** 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f0c464ff-96a7-4058-aee9-0258c7cc11cd/Untitled.png)

This model combines Development and Operations. It involves several stages that loop continuously until the desired product exists: Continuous development, Continuous testing, Continuous integration, Continuous deployment, and Continuous monitoring.

Advantages: There is reduced time to code deployment. The team has developers and operations staff. The team has end-to-end project ownership. There is proactive monitoring of deployed product.

Disadvantages: There is pressure to work on both old and new code. There is heavy reliance on automated tools to be effective. Deployment may affect the production environment. It requires an expert development team.

Project Planning

Before the project can begin, the software team needs to estimate the work to be done, the resources that will be required, and the time that will elapse from start to finish. Once these activities are accomplished, a project schedule can be established.

**Empirical Estimation Models**

- An empirical estimation model uses formulas to predict effort as a function of measures such as LOC-LOC can be estimated based on the requirements.
- It is usually derived using regression analysis on data collected from past software projects.
- Example: 𝐸=𝐴+𝐵×(𝑒𝑣)^C, where A, B, and C are empirically derived constants, E is effort in person-months, and evis the estimation variable (e.g. LOC).

**Estimation using Use Case Points**

- Once use cases have been developed, they can be used to estimate the projected size of a software project.
- The computation of use case points (UCP) takes into account:
    - The number and complexity of the use cases in the system
    - The number and complexity of the actors in the system
    - Various non-functional requirements (e.g. as portability, performance, maintainability) that are not written as use cases
- The UCP value can be computed as follows: UCP = (UUCW + UAW) ×TCF ×ECF, where
    - UUCW: total unadjusted use case weight
    - UAW: total unadjusted actor weight
    - TCF: technical complexity factors
    - ECF: environment complexity factors

**Estimation using Use Case Points (Example)**

- Consider a project with the following:
    - 18 simple use cases, 14 average use cases, and 16 complex use cases (assigned the weights 5, 10, and 15 respectively)
    - 8 simple actors, 12 average actors, and 4 complex actors (assigned the weights 1, 2, and 3 respectively)
    - Past project data: 85 LOC per UCP
    - Average productivity for systems of this type: 620 LOC/pm
    - Labor rate: $8000 per month
    - TCF = 1.04
    - ECF = 0.96
- Estimate the effort and cost of this project.

**Reconciling Estimates**

- Any estimation technique, no matter how sophisticated, must be checked by computing at least one other estimate using a different approach.
- When these different approaches result in different estimates, an aggregate value can be computed using the three-point estimation method: E = (E_opt + 4E_m + E_pes)/6, where E_opt is the optimistic value, E_m is the most likely value, and E_pes is the pessimistic value.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a9dffb00-d6a0-4b91-b40f-4d3ae729a7b1/Untitled.png)

**Risk Analysis:**

- Risk is a potential problem for a software project. It may or may not happen. If it happens, unwanted consequences will occur.
- Types of risks: Project risks, Technical risks, Business risks.
- A proactive risk strategy involves three steps:
    1. Risk Identification
    2. Risk Estimation
    3. Risk Mitigation, Monitoring, and Management

**Risk Identification:**

- Risk identification is a systematic attempt to specify threats to the project plan.
- By identifying known and predictable risks, the project manager takes a first step towards avoiding them when possible and controlling them when necessary.
- One method for identifying risks is to create a risk item checklist.

**Risk Estimation:**

- Risk estimation attempts to rate each risk in two ways:
    - The probability that the risk is real and will occur.
    - The consequences of the problems associated with the risk, should it occur.
- Risk probability can be determined by making individual estimates and then developing a single consensus value.
- Impact is usually determined using some scale (e.g. negligible, marginal, critical, and catastrophic).
- Risks can then be prioritized based on probability and impact.

**Risk Exposure and Risk Reduction Leverage:**

- Risk Exposure (RE) is a measure that quantifies the cost of a risk: RE = P x C, where P is the probability of occurrence for a risk, and C is the cost to the project should the risk occur.
- The RE measure can be used to prioritize risks and to adjust the total cost estimate for a project.
- Risk Reduction Leverage (RLL) is a measure that quantifies the efficiency of a mitigation action.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/316f2d6d-3a92-41b1-800c-d1d0b2e63048/Untitled.png)
    

**Risk Mitigation, Monitoring, and Management:**

- An effective strategy to deal with risk must consider three issues: risk avoidance, risk monitoring, and contingency planning.
- If a software team adopts a proactive approach to risk, avoidance is always the best strategy. This is achieved by developing a plan for risk mitigation.
- Risk-monitoring activities begin as the project proceeds.
- Risk management and contingency planning assumes that mitigation efforts have failed and that the risk has become a reality.