# Refactoring: Improving the Design of Existing Code

## Chapter 1 - Refactoring, a first example

1. ### When do you have to do refactoring?

    *When you find you have to add a new feature to a program, and the program's code is not structured in a convenient way to add the feature, first refactor the program to make it easy to add the feature, then add the feature.*

2. ### The First Step in Refactoring
   *Before you start refatoring, check that you have a solit suite of tests. These tests must be self-checking.*

   *Refactoring changes the programs in small steps. if you make a mistake, it is easy to find the bug.*

   *Any fool can write code that a computer can understand. Good programmers write code that humans can understand.*

## Chapter 2 - Principles in refactoring

1. ### Defining Refactoring
   - *Refactoring: to make the software easier to understand and modify but make little or no change in the observable bebhavior.*

   - *Adding function: the existing code shouldn't be changed, the new capabbilities are added. Adding tests and getting the tests to work.*

   - *Refactoring: Not adding function, only restructure the code. Don't add any tests, only change tests when you absolutely need to in order to cope with a change in an interface.*

   - *As you develop loftware, you probabbly find yourself swapping hats frequently: Add new function -> thing will be done easier if the code were structured differently -> refactoring -> Add new function -> code is hard to understand -> refactoring.

2. ### Why should you refactor?
   - *Refactoring improves the Design of Software
   - *Refactoring makes software easier to understand
   - *Refactoring helps you find bugs
   - *Refactoring helps you program faster

3. ### When should you refactor?

   #### The Rule of Three
      1. Refactor when you add funtion
      2. Refactor when you need to fix a bug
      3. Refactor as you do a code review
   #### What is it that makes programs hard to work with?

      1. Programs that are hard to read are hard to modify
      2. Programs that have duplicated logic are hard to modify
      3. Programs that require additional behavior that requires you to change running code are hard to modify
      4. Programs with complex conditional logic are hard to modify
   #### Indirection pros:
      1. To enable sharing of logic
      2. To explain intention and implementation separately
      3. To isolate change
      4. To encode conditional logic
   #### Refactoring and Performance
      *Build the program in a well-factored manner without paying attention to performance until you bbegin a performance optimization stage, usually fairly late in development.*

      *During the performance optimization stage, you follow a specific process to tune the program. You begin by running the program under a profiler that monitors the program and tells you where it is consuming time and space. this way you can find that small part of the program where the performance hot spots lie. Then you focus on those performance hot spots and use the same optimizations you would use if you were using the constant attention approach.*

## Chapter 3 - Bad smells in code
1. ### Duplicated code
   - Extract Method
   - Pull Up Field
   - Form Template Method
   - Substitute Algorithm
   - Extract Class
2. ### Long Method
   - Extract Method
   - Replace Temp with Query
   - Introduce Parameter Object
   - Preserve Whole Object
   - Replace Method with Method Object
   - Decompose Conditional
3. ### Large Class
   - Extract Class
   - Extract Subclass
   - Extract Interface
   - Duplicate Observed Data
4. ### Long Parameter List
   - Replace Parameter with Method
   - Preserve Whole Objbect
   - Introduce Parameter Object
5. ### Divergent change
   *Divergent change occurs when one class is commonly changed in different ways for different reasons.*
6. ### Shotgun Surgery
   *Similar to divergent change but in the opposite. Everytime you make a kind of change, you have to make a lot of little changes to a lot of different classes.*
   - Move Method
   - Move Field
   - Inline Class
7. ### Feature Envy
   *The method use data from other class than data of the one it actually is in.*
   *Solution: Move method to the class with most data is used. Strategy, Visitor and Self Delegation Pattern.
   - Move Method
   - Extract Method
8. ### Data clumps
   *Data items group together -> Create object for them*
   - Extract Class
   - Introduce Parameter Object
   - Preserve Whole Object
9. ### Primitive Obsession
   *Don't use primitive type -> Use Small object create by primitive type
   - Replace Data Value with Object
   - Replace Type Code with Class
   - Replace Type Code with Subclasses
   - Replace Type Code with State/Strategy
   - Extract Class
   - Introduce Parameter Object
   - Replace Array with Object
10. ### Switch Statements
   *Use polymorphism to replace switch statements*
   - Extract Method
   - Move Method
   - Replace Type Code with Subbclasses
   - Replace Type Code with State/Strategy
   - Replace Conditional with Polymorphism
   - Replace Parameter with Explicit Methods
   - Introduce Null Object
11. ### Parallel Inheritance Hierarchies
   *Special case of shotgun surgery. Every time you make a subbclass of one class, you have to make a subclass of another. 
12. ### Lazy Class
   - Collapse Hierarchy
   - Inline Class
13. ### Speculative Generality
   *Code that handle things that aren't required*
   - Collapse Hierarchy
   - Inline Class
   - Remove Paraeter
   - Rename Method
14. ### Temporary Field
   *Flag variabble*
   - Extract Class
   - Introduce Null Obbject
   - Method Object
15. ### Message Chains
   *Client ask one oject for another object then asks for another object and so on*
   - Hide Delegate
   - Extract Method
   - Move Method
16. ### Middle Man
   *The delegation go too far.*
   - Remove Midde Man
   - Inline Metho
   - Replace Delegation with Inheritance
17. ### Inappropriate Intimacy
   *One class uses the internal fields and methods of another class*
   - Move Method
   - Move Field
   - Change Bidirectional Association to Unidirectional
   - Extract Class
   - Hide Delegate
   - Replace Delegation with Inheritance
18. ### Alternative Classes with Different Interfaces
   *Two classes perform identical functions but have different method names.*
   - Rename Method
   - Move Method
   - Extract Superclass
19. ### Incomplete Library Class
   *Sooner or later, libbraries stop meeting user needs. The only solution to the prolem - changing the libbrary - is often impossible since the library is read-only*
   - Introduce Foreign Method
   - Introduce Local Extension
20. ### Data Class
   *Classes are dumb data holders and are almost certainly bbeing manipulated in far too much detail by other classes.*
   - Encapsulate Field
   - Encapsulate Collection
   - Remove Setting Method
   - Move Method
   - Extract Method
   - Hide Method on getters and setters
21. ### Refused Bequest
   *Subclass uses only some of the methods and properties inherited from its parets, the hierarchy is off-kilter.*
   - Push Down Method
   - Push Down Field
   - Replace Inheritance with Delegation
22. ### Comments
   *A method is filled with explanatory comments*
   - Extract Method
   - Rename Method
   - Introduce Assertion
   - When you feel the need to write a comment, first try to refactor the code so that any coment bbecomes superfluous
## Chapter 4 - Building Tests
   - *Make sure all tests are fully automatic and that they check their own results*
   - *A suite of tests is a powerful bug detector that decapitates the time it takes to find bugs*
   - *Run your tests frequently. Localize tests whenever you compile - every test at least every day.*
   - *When you get a bug report, start by writing a unit test that exposes the bug.*
   - *It is better to write and run incomplete tests than not to run complete tests.*
   - *Don't forget to test that exceptions are raised when things are expected to go wrong.*
   - *Don't let the fear that testing can't catch all bugs stop you from writing the tests that will catch most bugs*