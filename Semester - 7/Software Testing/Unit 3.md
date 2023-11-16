# Unit 3

### Black box Testing:

Black box testing is a technique of software testing which examines the functionality of software without peering into its internal structure or code.

Black box testing generally has 3 "uses":

- Functional testing: This is testing the main functionality of the program/product. Generally done by the software engineers.

- Non functional Testing: This is testing things like performance, responsiveness, reactivity, scalability etc. 

- Regression Testing: This is ensuring that the program/project is up to or better than the standards as it was before changes were made to the code.

There are a few tools used in regression testing. QTP, Selenium for func and regression testing. LoadRunner and Jmeter for non func.

We do black box testing ,in general, to improve the user experience, rather than improving the code.

#### Black box testing techniques:

- **Requirement based**
  
  - Requirements Traceability Matrix

- **Positive and negative**
  
  - Positive testing ensures that the valid data is accepted and processed correctly.
  
  - Negative testing ensure that the invalid data is not accepted and dealt with in a matter such that the program does not crash.

- **Specification based**
  
  - Equivalence partitioning: This divides the input data into multiple equal parts from which test cases can be derived. All inputs in one part must exhibit similar or same behavior to each other. This is essentially creating "classes" of inputs.
  
  - Boundary value analysis: This is giving the edge cases as test cases.
  
  - Decision tables: This is a techniques where we test the business logic and rules. This is a very good way to handle testing a sequence of inputs or a combination of inputs. Remember this is a *table* not a *flowchart*.
  
  - State based: This is where we test the programmatic logic. We test based on finite state machines and ensure the program follows the rules set by the FSM.

---

### Gray Box Testing

This is essentially black box testing but with some access to internal structure and code. 

All testing is done like black box. This means that we do not test the source code but rather the algorithms and structure, yadda yadda.

This is often seen done casually by software engineers during development. However this is not restricted to them.

In gray box we take inputs valid for black box testing or white box testing. We run tests like black box while going deeper into the parts of the project/ program.

##### Grey box testing techniques:

- Matrix testing: This is defining and testing all variables in a program.

- Regression testing: Same as black box.

- Orthogonal Array Testing: No info provided.

- Pattern Testing: This is testing done on historical system defects and tries to understand the root cause of the defect.