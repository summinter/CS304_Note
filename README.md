# CS304 Software Engineering

Summary of the lecture slides from Sustech CS304 Software Engineering 

## Lecture 1

1. What is SE? 

   The application of a systematic,
   disciplined, quantifiable approach to the
   development, operation, and maintenance of
   software

## Lecture 2

1. Software configuration management (SCM)
   1. Four aspects
      1. Change Control
      2. Version Control
      3. Building
      4. Releasing
2. Version Control System(VCS):is a software system that keeps track of
   the changes made to a set of files so that you can recall a specific
   version
3. SVN:
   1. Creating a Local Copy In SVN
      1. svn checkout  <address_to_remote> <name_of_local_dir>
   2. Commit local change :To commit the local changes made to a file that svn is tracking to the server:
      1. svn commit –m “msg”
   3. update your local copy with the changes on the server
      1. svn up
   4. To tell svn about a new file to track
      1. svn add <name_of_file>
   5. More command
      1. svn st: shows the status of files in the current svn directory
      2. svn rm: removes a file from the set of tracked files (will be removed on the remote server as well
      3. svn mv: moves a file from one directory to another (or renames if in same directory)
      4. svn diff: diff between two revisions, or diff a file to see
         uncommitted local cha
4. SVN Directory Layout
   1. Trunk
   2. Branches
   3. Tags:  Mark a state of the code (release for e.g)
5. Git uses a distributed model: Many operations are local
6. pull request:let you tell others about changes you've pushed to a
   GitHub repository. Once a pull request is sent, interested parties
   can review the set of changes, discuss potential modifications, and
   even push follow-up commits if necessary
7. Basic Git workflow:
   1. Modify files in your working directory
   2. Stage files, adding snapshot of them  to your staging area
   3. Do a commit, which takes the files as they are in the staging
      area and stores that snapshot permanently to your Git directory
8. Version control: parallel work
   1. What happens if two people are changing same software at same time?
      1. One solution (locking): Impossible! First person must lock software before making changes. Second person must wait until lock is released
      2. Another solution (merging): The second person to check in the
         software must merge the changes. Automatic merging works most of the time (but can silently introduce bugs)
9. Build management
   1. How do you build the product?
      1. Which compiler? Which flags?
      2. Which source files?
      3. Which libraries should be linked?
10. SCM(Supply Chain Management)
    1. Keep track of how software changes over time and be able to
       reproduce any version of the software
    2. Control how software changes; make sure needed changes have
       been made and no improper changes have made
11. SCM according to the SEI
    1. Identification
       1. Versions
       2. Baseline:is a software configuration item that has been reviewed
          and agreed upon, and that can be changed only through formal change control procedures
       3. Release: Release is a software configuration item that the developers give to other people
          1. Release should be a baseline
    2. Control
       1. Who is allowed to read/write configuration items?
       2. How do you know if changes are allowed/correct?
    3. Status accounting
       1. Reporting the status of components and change requests
    4. Audit and review
12. Various tests
    1. Smoke test
       1. Ensure that the system still runs after you make a change
    2. Unit test
       1. Ensure that a module is not broken after you make a change
    3. Regression test
       1. Ensure that existing code doesn’t get worse as you make other improvements



## Lecture 3

1. waterfall process avtivities
   1. ![image.png](https://i.loli.net/2021/06/06/pYJZsatodv1crL6.png)
   2. ![image.png](https://i.loli.net/2021/06/06/9KoXcCvq7kl4A53.png)
   3. ![image](https://user-images.githubusercontent.com/49226728/120919891-a2c0ea00-c6ee-11eb-890c-e3c451210599.png)
2. EXTREME PROGRAMMING(XP)
   1. Radically different from the rigid waterfall process
      1. Replace it with a collaborative and iterative design process
   2. Main idea
      1. Don’t write much documentation
         1. Working code and tests are the main written product
      2. Implement features one by one
      3. Release code frequently
      4. Work closely with the customer
      5. Communicate a lot with team members
   3. XP IS AN ITERATIVE PROCESS
3. PAIR PROGRAMMING
   1. air programming is a simple, straightforward
      concept. Two programmers work side-by-side at
      one computer, continuously collaborating on the
      same design, algorithm, code, and test. It allows
      two people to produce a higher quality of code
      than that produced by the summation of their
      solitary efforts.
4. user stories
   1. A user story represents a feature customers want in the software
5. STORY POINTS![image](https://user-images.githubusercontent.com/49226728/120919900-b409f680-c6ee-11eb-9a7c-e44c0ed46f67.png)
6. Test-first programming/ Test-driven development
   1. 。它要求在[编写](https://baike.baidu.com/item/%E7%BC%96%E5%86%99/1517598)某个[功能](https://baike.baidu.com/item/%E5%8A%9F%E8%83%BD/10346898)的[代码](https://baike.baidu.com/item/%E4%BB%A3%E7%A0%81/86048)之前先编写测试代码，然后只编写使测试通过的功能代码，通过测试来推动整个开发的进行。这有助于编写简洁可用和高质量的代码，并加速开发过程。
   2. Improve quality - find bugs
   3. Measure quality
      1. Prove there are no bugs? (Is it possible?)
      2. Determine if software is ready to be release
      3. Determine what to work o
      4. See if you made a mistake
   4. Learn the software
   5. Grade MPs 

## Lecture 4

1. WHAT IS A TEST?
   1. Run program with known inputs (test inputs/data), check results (with test oracles)
2. TERMINOLOGY
   1. MISTAKE, FAULT/BUG, FAILURE, ERROR
      1. mistake: programmer make mistakes
      2. fault: 只要程序中存在这种使系统失效的条件，那么这就叫Fault。(不管有没有执行到)
      3. failure: 一个系统不能执行所要求的功能时，即为Failure.
      4. error:如果这段程序很不幸，在运行的时候，中间有些步骤，或者中间变量与你设计的不同，这就叫Error. Error是能够导致系统出现Failure的系统内部状态。
3. test fixture
   1. A test fixture is the state of the test
      1. Objects and variables used by more than one test
      2. Initializations (prefix values
      3. Reset values (postfix values
   2. They should be initialized in a @Before method
      1. JUnit runs them before every @Test method
   3. Can be deallocated or reset in an @After method
      1. JUnit runs them after every @Test method
4. PARAMETERIZED TESTS
   1. Parameterized unit tests call constructor for each logical set
      of data values
      1. Same tests are then run on each set of data values
      2. List of data values identified with @Parameters annotation
5. Contract Model: Assume, Act, Assert
   1. Assumptions (Preconditions) Limit Values Appropriatel
   2. Action Performs Activity Under Scrutiny
   3. Assertions (Postconditions) Check Result
6. Test Driven Development (TDD)
   1. Kent Beck's rules
      1. Never write a single line of code unless you have a failing automated
         test. 
      2. Eliminate duplication
   2. ![image](https://user-images.githubusercontent.com/49226728/120919909-bf5d2200-c6ee-11eb-8147-ba78e252cd36.png)
   3. ![image](https://user-images.githubusercontent.com/49226728/120919916-c4ba6c80-c6ee-11eb-8e2e-d58a3d20fc65.png)



## Lecture 5

1. Code Coverage

   1. Code coverage is a measure used to describe the degree to
      which the source code of a program is executed when a
      particular test suites runs
   2. ![image](https://user-images.githubusercontent.com/49226728/120919926-d26ff200-c6ee-11eb-9f60-e7348fe2ebe8.png)
   3. Equation for Computing Coverage
      1. ![image](https://user-images.githubusercontent.com/49226728/120919944-d6037900-c6ee-11eb-9888-b974cde8781d.png)
   4. branch coverage
      1.![image](https://user-images.githubusercontent.com/49226728/120919952-d9970000-c6ee-11eb-8603-2bd242bf16da.png)

2. Mutation Testing 

   1. Why Mutation?
      1. Mutant processes are created to try to mimic
         typical syntactic errors made by programmer
      2. Many differing mutants are run against the
         specified tests to assess the quality of the tests
      3. The tests are attributed a score between 0 and
         1, as to whether they can distinguish between
         the original and the mutants
   2. How does it works
      1. create the mutant
      2. try to kill the mutant
         1. ![image](https://user-images.githubusercontent.com/49226728/120919968-e61b5880-c6ee-11eb-9844-d00795186326.png)
         2. meaning:![image](https://user-images.githubusercontent.com/49226728/120919972-e9aedf80-c6ee-11eb-96de-ea6e2dcafe2c.png)

   

   

## Lecture 6

1. Phrases in Maven
   1. validate: validate the project is correct and all necessary information is available
   2. compile编译: compile the source code of the project
   3. Test测试: test the compiled source code using a suitable unit testing framework. These tests should not
      require the code be packaged or deployed
   4. Package打包: take the compiled code and package it in its distributable format, such as a JAR.  integration-test: process and deploy the package if necessary into an environment where integration tests
      can be run
   5. verify: run any checks to verify the package is valid and meets quality criteria
   6. Install安装: install the package into the local repository, for use as a dependency in other projects locally
   7. deploy: done in an integration or release environment, copies the final package to the remote repository for
      sharing with other developers and projects
   8. clean: cleans up artifacts created by prior builds
   9. site: generates site documentation for this project
2. Coverage = Reachability (可达性)
   1. Dead code: code that cannot be reached![image](https://user-images.githubusercontent.com/49226728/120919976-f29fb100-c6ee-11eb-801e-7c49b254876a.png)
3. Measures of the product are called “technical metrics”
4. Lines of code is valid metric when
   • Same language
   • Standard formatting
   • Code has been reviewed
5. CYCLOMATIC COMPLEXITY 
   1. A measure of logical complexity
   2. Tells how many tests are needed to execute every statement of program
   3. 圈复杂度用来衡量一个模块判定结构的复杂程度，数量上表现为线性无关的路径条数，即合理的预防错误所需测试的最少路径条数。圈复杂度大说明程序代码可能质量低且难于测试和维护，根据经验，程序的可能错误和高的圈复杂度有着很大关系。
   4. how to compute
      1. Number of predicates + 1
      2. Number of edges - number of nodes + 2
      3. Number of regions of the flow graph

​      

6. Function point
   1. Count number of inputs, number of outputs, number
      of algorithms, number of tables in database
   2. “Function points” is function of above, plus fudge
      factor for complexity and developer expertise
   3. You need training to measure function points
7. MARTIN’S COUPLING METRIC
   1. Ca : Afferent coupling: the number of classes outside this module that
      depend on classes inside this module
   2. Ce : Efferent coupling: the number of classes inside this module that
      depend on classes outside this module
   3. Instability = Ce / (Ca + Ce)
   4. packages on which it depends. • High value of the metric Ce> 20 indicates instability of a package
   5. High values of metric Ca usually suggest high component stability.
   6. There are two types of components:
      1. Many outgoing dependencies and not many of incoming ones (value I is close to 1), are unstable due to the possibility of easy changes to these packages;
      2. Many incoming dependencies and not many of outgoing ones (value I is close to 0), therefore they are more difficult in modifying due to their greater responsibility
8. LIST OF METRICS![image](https://user-images.githubusercontent.com/49226728/120919977-f8959200-c6ee-11eb-836d-de0bf7b3360e.png)
9. REVERSE ENGINEER: From code to design, maybe to requirements

## Lecture 9

1. static testing
   1. no dynamic execution
   2. detect possible defects in an early stage
2. Tools for Static Analysis
   1. Checkstyle
   2. PMD
   3. FindBugs
      1. FindBugs works by analyzing Java bytecode (compiled class files), so you don't even need the program's source code
      2. Concentrates on detecting potential bugs and performance issues



## Lecture 10

1. Defensive Programming:
   1. Making sure that no warning produced by Static Analysis is a form of defensive programming
2. Fault Tolerance
   1. Backward Recovery:
      1. Record system state at specific events (checkpoints). After failure, recreate state at last checkpoint.
3. The security goal
   1. The security goal is to make sure that the agents (people or
      external systems) who interact with a computer system, its data, and its resources, are those that the owner of the system would wish to have such interactions
   2. Techniques: Barriers
      1. Place barriers that separate parts of a complex system:
         1. Isolate components, e.g., do not connect a computer to a
            network
         2. Firewalls
         3. Require authentication to access certain systems or parts of systems
      2. Every barrier imposes restrictions on permitted uses of the system
         1. Barriers are most effective when the system can be divided into subsystems with simple boundaries
   3. Techniques: Authentication & Authorization
      1. Authentication establishes the identity of an agent:
      2. Authorization establishes what an authenticated agent may do:
   4. Techniques: Encryption
      1. Allows data to be stored and transmitted securely, even when the bits are viewed by unauthorized agents
4. java doc comment
   1. @param - Parameter name, Description
   2. @return - Description
   3. @throws - Exception name, Condition under which
      the exception is throw
   4. javadoc comments must be immediately before:
      • a class (plain, inner, abstract, or enum)
      • an interface
      • a constructor
      • a method
      • a field (instance or static)
   5. Anywhere else, javadoc comments will be ignored!
   6. Do not mention the type in @param and @return tags--
      javadoc will do this (and get it right)
   7. Rules for writing summaries
      1. The first sentence should summarize the the purpose of the element
      2. For methods, omit the subject and write in the third-person narrative form
      3. Use the word this rather than “the” when referring to instances of the current
         class
      4. • Do not add parentheses to a method or constructor name unless you want to specify a particular signature
5. Types of Software Reuse
   1. Application System Reuse
      1. reusing an entire application by incorporation of one
         application inside another (COTS reuse)
      2. development of application families (e.g. MS Office
   2. Component Reuse
      1. components (e.g. subsystems or single objects) of
         one application reused in another application
   3. Function Reuse
      1. reusing software components that implement a
         single well-defined function
6. Economics of Reuse
   1. Quality
      1. with each reuse additional component defects are identified and removed which improves quality. 
   2. Productivity
      1. since less time is spent on creating plans, models, documents, code, and data the same level of functionality can be delivered with less effort
         so productivity improves.
   3. Cost
      1. savings projected by estimating the cost of building
         the system from scratch and subtracting the costs
         associated with reuse and the actual cost of the
         software as deliverer
   4. Cost analysis using structure points
      1. can be computed based on historical data regarding
         the costs of maintaining, qualification, adaptation,
         and integrating each structure point
7. Component-Based Software Engineering
   1. CBSE is an approach to software development that relies on
      reuse
   2. CBSE emerged from the failure of object-oriented
      development to support reuse effectively
   3. Objects (classes) are too specific and too detailed to support
      design for reuse work
   4. Components are more abstract than classes and can be
      considered to be stand-alone service provider
8. Commercial Off-the-Shelf Software (COTS)



## Lecture 11

1. MVC pattern
   1.![image](https://user-images.githubusercontent.com/49226728/120919980-fe8b7300-c6ee-11eb-95f7-b0646b932d9d.png)
   2. view
      1. :Little logic; just display
   3. model
      1. Logic related to persistent storage
      2. DB system (MySQL)
         1. each DB entity maps to a single DAO and a
            single Bean
      3. Beans: placeholders for data related to an iTrust entity (e.g., Patient)
         1. minimal functionality (only store data)
         2. Other supporting classes
            1. load beans from database result sets
            2. validate beans based on input
            3. any other custom logic needed.
      4. DAOs (DB Access Objects): Java objects that
         interact with the DB
         1. reflect contents in the DB
         2. offer to interact with the DB
         3. query and update the DB (e.g., from Action
            classes)
         4. should not have many branches (assuming
            incoming data is valid and any exception is
            handled by the Action classes)
   4. Controller
      1. Handle all logic
         1. validate data
         2. process DB query results
      2. Everything between Action classes and DAO classes
         1. Action classes
            1. exception handling
            2. a method <= 15 lines
         2. Validators
         3. Custom business logic
      3. Action classes delegate responsibilities to
         other classes
         1. Delegate any input validation to a Validator
         2. Log transactions for auditability
         3. Delegate any custom business logic, such as
            risk factor calculations
         4. Delegate database interaction
         5. Handle exceptions in a secure manner

 

## Lecture 13

1. DevOps: Development + IT Operations
2. Continuous Integration
   1. “Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily - leading to multiple integrations per day. Each integration is verified by an automated build (including test) to detect integration errors as quickly as possible.
   2. Automate the build
   3. Make your build self-testing
      1. Automated tests: Tests that can be run from the command line
      2. Smoke Test: A quick set of tests run on the daily build.
         1. Cover most important functionalities of the software
         2. but NOT exhaustive Check whether code catches fire or “smoke” (breaks)
         3. Expose integration problems earlier
   4. CI Server
      1. An external machine that automatically pulls your latest repo code and fully builds all resources.
3. Levels of Software Testing
   1. ![image](https://user-images.githubusercontent.com/49226728/120919986-04815400-c6ef-11eb-9548-b632a6ed30e1.png)
   2. Integration testing
      1. Integration testing: Verify software quality by testing
         two or more dependent software modules as a group
4. Incremental Integration Testing
   1. Develop a functional "skeleton" system
   2. Design, code, test, debug a small new piece
   3. Integrate this piece with the skeleton
   4. Advantages:
      1. Errors easier to isolate, find, fix
      2. System is always in a (relatively) working state
   5. Disadvantages
      1. May need to create "stub" versions of some features that have not yet been integrated
5. Top-down integration
6. Bottom-up integration
7. "Sandwich" integration
8. Stub versus Driver
   1. Both are used to replace the missing software and
      simulate the interface between components
   2. Create dummy code![image](https://user-images.githubusercontent.com/49226728/120919993-0ea35280-c6ef-11eb-833d-224ddea2f0b3.png)
   3. Stub: Dummy function gets called by another function
   4. Driver: Dummy function to
9. Continuous Delivery
   1. to build software so that it is always in a state where it could be put into production
   2. e we are continuously running a deployment pipeline that tests if this software is in a state to be delivered.
   3. Cont. Delivery vs. Deployment![image](https://user-images.githubusercontent.com/49226728/120919995-15ca6080-c6ef-11eb-9c7e-4f2de3f66406.png)
   4. ![image](https://user-images.githubusercontent.com/49226728/120919999-195de780-c6ef-11eb-999e-edaaf09bf88a.png)
10. Deployment strategies
    1. Strategy 1: Zero-downtime deployment
       1. Deploy version 1 of your service
       2. Migrate your database to a new version
       3. Deploy version 2 of your service in parallel to the version 1
       4. If version 2 works fine, bring down version 1
       5. Deployment Complete!
    2. Strategy 2: Blue-green deployment
       1. Maintain two copies of your production environment (“blue” and “green”)
       2. Route all traffic to the blue environment by mapping production URLs to it
       3. Deploy and test any changes to the application in the green environment
       4. “Flip the switch”: Map URLs onto green & unmap them from blue.
11. What is difference between Continuous Integration and Continuous
    Delivery ?
    1. Continuous Delivery requires automated testing before release.
12. Regression Testing
    1. 在实际的开发中，不免会碰到这样的问题：某个功能或模块在新版中从正常状态退化到了不正常的工作状态。出现了软件功能的退化。工程师应该在新版本上运行所有的测试用例（test case），以验证没有退化情况发生，这一过程就是回归测试。
    2. 目的：
       1. 验证新的代码的确修正了缺陷；
       2. 验证新的代码有没有破坏模块的现有功能，有没有退化。
13. Flaky Tests
    1. Test which could fail or pass for the same code



## Lecture 14

1. Security engineering
   1. ² Tools, techniques and methods to support the development and maintenance of systems that can resist malicious attacks that are intended to damage a computer-based system or its data.
   2. A sub-field of the broader field of computer security
2. Security dimensions
   1. Confidentiality
      1. Information in a system may be disclosed or made accessible to people or programs that are not authorized to have access to that information.
   2. Integrity
      1. Information in a system may be damaged or corrupted making 
   3. Availability
      1. Access to a system or its data that is normally available may not be possible.
3. Security levels
   1. infrastructure security
      1. which is concerned with maintaining the security of all systems and networks that provide an infrastructure and a set of shared services to the organization.
   2. application security
      1. which is concerned with the security of individual
         application systems or related groups of systems
   3. operational security
      1. y, which is concerned with the secure operation and use of the organization’s systems.
   4. Application security is a software engineering problem where the system is *designed* to resist attack
   5. Infrastructure security is a systems management problem where the infrastructure is *configured* to resist attack

  

   

   
