# Construction
Performed by “programmers”.

It is unprofessional for programmers to bend to the will of managers who don’t understand the risks of making messes.

## Best Practices
Naming

- Reveal intent
- Reveal all functionality
- Name according to abstraction level, not implementation
- Meaningfully distinctive names from others in the same context
- Pronounceable
- Classes and objects named as nouns or noun phrases
- Methods named as verbs or verb phrases
- Consistent lexicon
- Context added to names if necessary
- Code reads like prose
- Avoid encoding information in the name, like in Hungarian notation
- Avoid negatively named conditionals

Statements

- Only use switch statements in factories to create polymorphic objects
- Encapsulate boundary conditions
- Control blocks should be 1 line long
- Statements in a loop do only one thing
- Use a lookup table over complicated logic if possible
- Ascending order of terms in numerical comparisons

Functions

- Descriptive names
- 1-4 lines long
- Do only one thing and do it well (cannot be further subdivided)
- Contain statements at only one level of abstraction (1 level below the function name)
- 0 or 1, sometimes 2 parameters (no flags)
- No side effects
- Avoid output arguments
- Remove dead functions (never called)
- Try/catch handles errors, should be the only thing that function does
- Enforce correct call order by client

Comments

- Self-documenting code, express intent in code rather than comments
- Express additional intent information when necessary
- Warn other programmers of consequences of running or modifying code
- TODOs, but should be completed
- Source control keeps track of change history

Formatting

- Detail increases downward
- Declare variables/functions as close to first usage as possible
- Be consistent

Objects and Data

- Abstraction
- Objects hide data, expose behaviour
- Data structures expose data, don’t expose behaviour
- Avoid hybrid object/data structure
- Law of Demeter

Error Handling

- Exceptions instead of return codes
- Throw exception class types based on the caller’s needs
- Never return null
- Never pass null

Unit Tests

- Test everything that could break
- Keep as clean as production code
- One tested concept per test
- Fast, independent, repeatable, self-validating (pass or fail), written before production code
- Test all boundary cases

Concurrency

- Separate concurrency code
- Collections tools (e.g., System.Collections.Concurrent)
- Synchronization tools (e.g., System.Threading)
- Producer-Consumer algorithm
- Readers-Writers algorithm
- Dining Philosophers algorithm
- Limit access to shared data
- Use copies or partitions of data instead of sharing data

General

- Respect language boundaries by source file
- Respect level of abstraction boundaries
- Follow standard conventions
- Keep configuration/default values at the highest level
- Prefer clarity over performance
- Use the right tool for the job

## Rules for Simple Design
1. Run all the tests
2. No duplication
3. Express intent
4. Minimize number of classes and methods

## Test Driven Development
- Don’t write any production code until you have written a failing unit test
- Write a failing unit test that is no more than sufficient to fail
- Then write production code that is no more than sufficient to pass
- Then refactor the unit tests and production code

## Refactoring
### Smells
- Duplicated code
- Long routine
- Long or deeply nested loop
- Large class
- Large number of parameters in a parameter list
- Changes within a class tend to be within different regions for different reasons
- Poor cohesion within a class
- Need for parallel changes (classes, inheritance hierarchies, case statements)
- Feature envy
- Related data items used together are not encapsulated
- Primitive data type used for a higher level of abstraction
- Switch statements instead of polymorphism
- Very small classes
- Generality, flexibility that isn’t needed
- Data member that have meaningful data only sometimes
- Chained method calls
- A middleman object that only passes data through
- Inappropriate abstraction involving pass-through data by a routine
- Exposed information that other classes shouldn’t know about
- Public data member
- Methods that do the same thing but have different signatures
- Classes with no behaviour
- Is-A relationship when only part of the parent is needed
- Comments that answer ‘what’ or ‘how’ instead of ‘why’
- Inconsistent level of abstraction of an interface
- Poor routine name
- Global variable
- Repetitive setup or takedown requirement of a routine
- A class hierarchy that does more than one job
- Procedural code written in an object-oriented language
- Presentation classes contain domain logic

### Refactorings
Data

- Replace Magic Number with Symbolic Constant
- Rename a variable with an informative name
- Replace references to an intermediate variable with the expression (**Inline Temp**)
- Replace an expression with a routine (**Replace Temp with Query**)
- Introduce an intermediate variable (**Introduce Explaining Variable**)
- Convert a multi-use variable to multiple single-use variables (**Split Temporary Variable**)
- Modify a new local variable instead of a parameter (**Remove Assignments to Parameters**)
- Convert a primitive data type to a class (**Replace Data Value with Object**)
- Convert a set of type codes to a class or enumeration (**Replace Type Code with Class**)
- Convert a set of type codes to a class with subclasses
  - **Replace Type Code with Subclasses**
  - **Replace Type Code with State/Strategy**
- Change an array to an object (**Replace Array with Object**)
- Encapsulate a collection instead of returning it (**Encapsulate Collection**)
- Replace a traditional record with a data class (**Replace Record with Data Class**)
- Use getter and setter for a field inside a class (**Self Encapsulate Field**)

Statements

- Decompose a complex Boolean expression with well-named intermediate variables
- Extract a complex Boolean expression into a well-named function
- Decompose a conditional into well-named functions (**Decompose Conditional**)
- Consolidate duplicated fragments within different blocks of a conditional
  - **Consolidate Conditional Expression**
  - **Consolidate Duplicate Conditional Fragments**
- Use break or return statements instead of a loop control variable (**Remove Control Flag**)
- Return as soon as possible instead of using a return value
  - **Replace Nested Conditional with Guard Clause**
- **Replace Conditional with Polymorphism**
- Use null objects instead of testing for null (**Introduce Null Object**)
- Make an assumption explicit with an assertion (**Introduce Assertion**)

Routines

- **Rename Method**
- **Extract method**
- Move a method inline (**Inline Method**)
- Convert a long routine to a class (**Replace Method with Method Object**)
- Replace a complex algorithm with a simple algorithm (**Substitute Algorithm**)
- **Add Parameter**
- **Remove Parameter**
- Separate query and command (**Separate Query from Modifier**)
- Combine and parameterize nearly duplicate routines (**Parameterize Method**)
- Separate routines whose behaviour depends on the parameters
  - **Replace Parameter with Explicit Methods**
- Pass a whole object rather than specific fields (**Preserve Whole Object**)
- Pass specific fields rather than a whole object
- Create an object to encapsulate a set of parameters (**Introduce Parameter Object**)
- Call a method to retrieve a value instead of accepting it as a parameter
  - **Replace Parameter with Method**
- Encapsulate downcasting by returning most specific type (**Encapsulate Downcast**)

Classes

- Use reference objects that point to a single value object (**Change Value to Reference**)
- Use value objects instead of many reference objects (**Change Reference to Value**)
- Replace an overridden routine that returns a constant with initialization of the parent
  - **Replace Subclass with Fields**
- Pull a routine, field, or constructor body up into its superclass
  - **Pull Up Field**
  - **Pull Up Method**
  - **Pull Up Constructor Body**
- Push a routine, field, or constructor body down into its derived class
  - **Push Down Field**
  - **Push Down Method**
- Extract specialized code into a subclass (**Extract Subclass**)
- Combine similar code into a superclass (**Extract Superclass**)

Interfaces

- Move a routine to another class (**Move Method**)
- Move a data member to a different class (**Move Field**)
- Separate 1 class into 2 classes (**Extract Class**)
- Eliminate a class (**Inline Class**)
- Hide a composite part (C): change A calls B; A calls C to A calls B; B calls C (**Hide Delegate**)
- Remove a middleman (B): change A calls B; B calls C to A calls B; A calls C (**Remove Middle Man**)
- Replace inheritance with composition (**Replace Inheritance with Delegation**)
- Replace composition with inheritance (**Replace Delegation with Inheritance**)
- Introduce a foreign routine in client class instead of server class (**Introduce Foreign Method**)
- Introduce an extension class: inherit, wrap, or extend original class (**Introduce Local Extension**)
- Encapsulate a public member variable (**Encapsulate Field**)
- Remove setters (**Remove Setting Method**)
- Hide unused exposed routines (**Hide Method**)
- Separate 1 interface into 2 interfaces (**Extract Interface**)
- Collapse superclass/subclass (**Collapse Hierarchy**)
- Combine similar algorithms into a single template algorithm (**Form Template Method**)

System

- Add a definitive reference source for data that exists somewhere inaccessible
  - **Duplicate Observed Data**
- **Change Unidirectional Association to Bidirectional**
- **Change Bidirectional Association to Unidirectional**
- Use factory method instead of constructor (**Replace Constructor with Factory Method**)
- **Replace Error Code with Exception**
- Replace exceptions with error codes
- Test first instead of catching exception (**Replace Exception with Test**)

## Algorithms

ToDo

## Data Structures

ToDo


# References
Fowler, Martin. *Refactoring: Improving the Design of Existing Code*. Addison-Wesley, 1999.

House, Corry. *Clean Code: Writing Code for Humans*, [PluralSight](http://www.pluralsight.com/courses/writing-clean-code-humans), 2013.

Martin, Robert C. *Clean Code*. Prentice Hall, 2009.

McConnell, Steve. *Code Complete*. Microsoft Press, 2004.

Smith, Steve. *Refactoring Fundamentals*, [PluralSight](http://www.pluralsight.com/courses/refactoring-fundamentals), 2013.
