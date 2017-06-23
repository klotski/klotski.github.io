---
layout: default
title: 软件测试
category: MOOC
---

推荐书籍：
[惠特克, 阿尔邦, 卡罗洛. Google软件测试之道. 人民邮电出版社, 2013](https://www.amazon.cn/gp/product/B00FH36R6G/)
[James A. Whittaker, Jason Arbon, Jeff Carollo. How Google Tests Software. Addison-Wesley Professional, 2012](https://www.amazon.com/dp/0321803027/)

---

Evaluation: 简单问题复杂化！

Definitions of Bug: **Fault, Error & Failure**

 - Software Fault: A **static** defect in the software.
 - Software Error: An incorrect **internal** state that is the manifestation of some faults.
 - Software Failure: **External**, incorrect behavior with respect to the requirements or other description of the expected behavior.

**PIE Model**

 - Execution/Reachability: The location or locations in the program that contain the fault must be reached.
 - Infection: The state of the program must be incorrect.
 - Propagation: The infected saste must propagate to cause some output of the program to be incorrect.

**Testing** vs. **Debugging**

- Testing is to reveal a bug *by executing test and observing failure.*
- Debugging is to fix a bug *by locating, understanding and correcting fault.*

**Verification** vs. **Validation**

- Verification: The evaluation of whether or not a product, service, or system complies with a regulation, requirement, specification, or imposed condition. It is often an in ternal process.
- Validation: The assurance that a product, service, or system meets the needs of the customer and other identified stakeholders. If often involves acceptance and suitability with external customes.


## Graph in Testing

Source Code -> Control Flow Graph (控制流图)
Requirement Specification -> Finite State Machine (有限状态机)
Use Case Diagram -> Activity Diagram

Test Path
:    A path that starts at an initial vertex and ends at a final vertex. 

Test path represent execution of test cases.

* Some test paths can be executed by many tests.
* Some test paths cannot be executed by any tests.

**Test and Test Path**

* path(t): The test path executed by test *t*.
* path(T): The set of test paths executed by the set of tests *T*.

## Graph Coverage Criteria

**Reach**

* Syntactic reach: A path exists in the graph
* Semantic reach: A test exists taht can execute that path

**Graph Coverage**

We use graphs in testing as follows:

* Developing a model of the software as a graph
* Requiring tests to cover specific sets of vertices, edges or subpaths

### **Structural Coverage**

Defined on a graph just in terms of vertices and edges

* Source code
* Requirement specification
* Design diagram

**Test Criteria**

Test Requirements (TR): Describe properties of test paths

**Satisfaction**

Given a set TR of test requirements for a criterion C, a set of tests T satisfies C on a graph if and only if for every test requirement in TR, there is a test path in path(T) that meets the test requrement tr

**Vertex Coverage (VC)**

* TR contains each reachabloe vertex in G.

**Edge Coverage (EC)**

* TR contains each reachabloe edge in G.

**Covering Multiple Edges**

* Edge-pair coverage requires pairs of edges

* Edge-Pair Coverage (EPC):
  TR contains each reachable path of length to length to up 2, inclusive, in G.

Complete Path Coverage (CPC): TR contains all paths in G.

n-Path Coverage (nPC): TR contains each reachable path of length up to n, inclusive, in G.

* VC(n=0), EC(n=1), EPC(n=2), CPC(n=∞)

**Subsume**

* C1 >= C2 does not imply that *T1* satisfying C1 can detect any fault detected by *T2* which satisfies C2.


