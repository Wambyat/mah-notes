# Unit 1

**Software testing** is the activity to detect and identify the defects in the software.

**Software Quality** is a field of study that describes the desirable attributes of software products.

These are different software quality parameters:

* Bug Free

* On time delivery

* Staying within budget

* Meeting requirements

* Maintainability

### Software Quality Model:

* Functional suitability

* Reliability

* Operability

* Performance efficiency

* Security

* Compatibility

* Maintainability

* Transferability

<img title="" src="images/2023-09-29-19-23-41-image.png" alt="" data-align="center" width="859">

### Software quality-in-use model:

* Effectiveness

* Efficiency

* Satisfaction

* Safety

* Usability

Deming's PDCA cycle: Plan, Do, Check, Act. Quality is often measured in MTTF (Mean Time To Fail). MTBF is mean time between failure. 

QA (Quality Assurance) is process oriented. QC (Quality Control) is product oriented. The cost of quality of a project should be around 3-5%. 

Cost for quality can have a few different forms. 

* Prevention cost

* Appraisal Cost

* Internal Failure cost

* External failure cost

<u>Error</u>: Human mistake

<u>Bug</u>: Deviation from expected behavior

<u>Failure</u>: Deviation identified by end user

Spiral model is the version release one. RAD (Rapid Application Development) is where we divide the project into small modules and a team is assigned to each one.

---

#### Static Testing

##### Review:

We check if documents are correct and complete.

##### Walkthrough:

This is an informal review.

##### Inspection:

This is the most formal review. Usually 3-8 people will be present for this.

##### Verification:

This is checking if we are making the right product.

---

#### Dynamic Testing

Validation: This is where we make sure we are making the product correctly.

---

### Levels of Testing

#### Unit Testing:

This is where we test one unit or module. A few techniques are:

- Path testing

- Control Structure Testing

- Conditional Coverage

- Loops Coverage

- Mutation Testing

#### Integration Testing:

This is done on 2 or more modules. It is focused on the communication between the modules. It is white box testing,

#### System Testing:

This is testing the entire system working. It is generally black box testing.It generally is:

- UI testing

- Functional Testing

- Non functional testing

- Usability testing 

#### UAT (User Acceptance Test):

This is usually the last phase. It has 2 phases.

###### Alpha Testing: The customers come to the developers and do some testing

###### Beta Testing: The software is installed in the user environment and tested there.

---

## Quality Management

Quality planning, assurance, control, improvement come under this.

| Quality Assurance                            | Quality Control                                                  |
| -------------------------------------------- | ---------------------------------------------------------------- |
| Defect prevention by focusing on the process | Defect detection and correction by focusing on the built product |
| Done throughout lifecycle                    | Done after product is built                                      |

---

#### ETVX Model

Entry Task Verification eXit.

<img src="images/2023-09-29-22-01-00-image.png" title="" alt="" data-align="center">

---

## Software Testing Life Cycle (STLC)

1. Requirement analysis

2. Test planning

3. Test case development

4. Test environment setup

5. Test execution

6. Retest Defects

7. Test cycle closure

<u>Entry Criteria</u> is the prerequisite items that must be completed before testing can begin.

<u>Exit Criteria</u> is the items that must be completed before testing can be concluded.

---

## Requirement Analysis

Also call requirement phase testing is where the test team studies the requirements from a testing point of view to identify testable requirements. They might also interact with the stakeholders.

Steps:

1. Identify the types of tests

2. Get details on testing priorities

3. Prepare Requirement Traceability Matrix (User requirements to test cases)

4. Identify test environment detail.

5. Automation feasibility

Deliverables are 2 fold. RTM and the automation report.

Exit criteria is when the RTM and automation are signed.

---

## Test planning

This is where a senior QA makes the plan ans strategises. This includes cost and effort estimates, schedule, environments and limitations,

Things to do:

- Documents for the plans

- Tool selection

- Effort estimation

- Determining roles and responsibilities

- Training

Deliverables are the main test plan document. Exit criteria is when the documents are approved.

---

## Test Case Development

This include the creation, verification and improvement of test cases and scripts. Things to do and deliverables are obvious,

Exit criteria is when the cases and scripts are signed. We also have to get test data signed off.

---

## Test Environment Setup

This is where we decide under what software and hardware conditions the product should be tested. This can be done in parallel with test case development. This is where the smoke test is done.

Environment setup is working according to plan. Test data must be complete and smoke test must be done.

---

## Test Case Execution

-_- Only new thing is we complete the RTM in this phase. We make defect report and continue until specified.

We exit when all tests are executed and defects logged.

---

## Test Cycle Closure

This is when we compile everything. We also learn lessons for future test cycles. We make a big evaluation pertaining to the test cycle.

Test closure report signed by client.

---

# Test types

### Based on testing type:

- White box: This is based on testing code

- Grey box: Wierd hybrid

- Black box: This is based on testing requirements

### Based on requirement type:

- Functional

- Non - Functional

### Based on cycle phase:

- Unit testing

- Integration testing

- System testing

### Based on needs:

- Regression testing

- Acceptance testing

- Alpha and beta testing

---
