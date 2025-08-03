# Go Back to Basics
After 25 years of continuous work in software development, I recently had the opportunity to take a break and reflect on 
my journey. This pause gave me the chance to summarize and document my observations and insights as a developer. Looking 
back at the projects I have contributed to, the people I have worked with, and the teams I have managed, I realized that 
while new technologies are emerging faster than ever, progress in some fundamental areas of software engineering remains 
limited. These basics are well known to almost every developer, yet for various reasons, we often fall short in consistently 
applying them. From my experience in financial technology, most of the recurring issues and challenges are not due to a 
lack of cutting-edge tools, but rather a lack of mastery in these core fundamentals. It is time to "go back to basics."
In this article, I will share my thoughts and findings from an engineer’s perspective.

## Own the code
### Findings:
- Many of our source code repositories lack a clear and intuitive structure, making it challenging for newcomers to 
understand the project. Additionally, some repositories still contain outdated or deprecated code, which can confuse new 
developers.

- Despite Git being a modern version control tool, some team members continue to use outdated practices, treating Git as 
if it were SVN or CVS. This leads to inefficiency and conflicts.

### Thoughts:
As the owner/contributor of our repositories, we have the responsibility to maintain our repositories in a healthy state.

- Ensure that the repository has a well-defined and intuitive structure, or provide a concise overview of the repository 
structure in the Readme. This will enable newcomers to easily understand and locate relevant information.

- Utilize appropriate tools effectively. While using modem tools is important, it is equally crucial to cultivate a modern 
mindset among team members and fully leverage the capabilities of the tools to enhance productivity and quality.

## Keep it tidy
### Findings:
- Many staff write commit messages only because it is required, often using generic terms like "Update."When trying to 
trace back which commit introduce a specific change, it is very hard to tell which "Update" cause the actual update.

- Some team members neglect to write commit messages due to the large number of changes in the commit and a lack of 
understanding on how to write proper commit messages.

- Certain changes included in the commit are unrelated to the commit message, as some developers include personal additions 
that are not relevant to the task at hand. This practice undermines the integrity of the commit and can lead to confusion.

### Thoughts:
Commit messages are crucial assets of our repositories. They play a vital role in linking code changes with features during 
code reviews and pull requests. It is the responsibility of every developer to provide accurate and informative commit 
messages when committing code changes.
- Ensure that each commit message includes the corresponding JIRA ID to effectively link code changes with requirements.
- Implement git hooks to enforce consistent commit message patterns.
- Maintain a focused scope for each commit, addressing one specific change at a time.
- Utilize tools like Copilot chat to assist in summarizing code changes effectively

## Adopt pull request etiquette
### Findings:
- The selection of PR reviewers lacks a structured approach. Reviewers are chosen arbitrarily, without considering their 
level of expertise or experience.
- Some developers choose reviewers based on convenience rather than seeking professional feedback. They may request approval 
urgently instead of actively seeking code review and constructive comments.
- Reviewers don't have much bandwidth and willingness to review the code change. There is already quality gate installed 
as automatic reviewer, why bother to have a human reviewer?

### Thoughts:
Code review through pull requests is a critical practice for maintaining software quality and ensuring consistent design. 
Unfortunately, we have observed numerous instances where well-designed software deteriorates due to deviations from the 
original design and excessive short-term compromises. Ineffective code reviews have accelerated and exacerbated this process.

- A pull request (PR) reviewer is an experienced individual with a deep understanding of the codebase. They possess extensive 
knowledge of the software's design and are responsible for thoroughly reviewing PRs to ensure that the code changes align 
with the original design principles and adhere to established design patterns for scalability and maintainability.
- An effective code review can significantly enhance software quality and prolong its lifespan. As guardians of software 
quality, reviewers should take sufficient responsibility in ensuring this, as it is a crucial aspect of their role as 
experienced developers.
- Ensure that an adequate amount of time is allocated for the code review process, allowing the PR reviewer sufficient 
time to thoroughly review the code changes and provide constructive feedback. To optimize the reviewer's effort, it is 
recommended to keep each pull request small and focused.
- Robotic reviewers can assist in identifying some superficial issues, but they are only auxiliary tools. The true value 
lies in human reviewers who can provide substantial insights and feedback.

## Be disciplined with branches
### Findings:
- There is no defined branch strategy or the use of an inappropriate branch strategy in projects, resulting in chaos and 
reduced development productivity.
- Some team members create new branches but neglect to clean them up, resulting in a buildup of unnecessary code and 
increasing the maintenance burden on the repositories.
- Developers have a limited understanding of GIT commands and struggle to effectively handle complex scenarios, leading 
to mistakes and reduced efficiency.

### Thoughts:
Branches are a crucial aspect of Git that enable developers to work on separate lines of development without impacting 
the main codebase. This feature greatly enhances the productivity of the development team. It is essential to establish 
a disciplined approach to branching and ensure consistent adherence throughout the team.
- Choose a mature branch strategy that aligns with the nature of the project, such as GitFlow, Github Flow, Gitlab Flow, 
or Trunk Based Development (TBD). Each strategy has its advantages and disadvantages. Select an appropriate strategy and 
ensure that the team adheres to it consistently.
- Establish a comprehensive branch lifecycle policy to effectively manage and regulate the number of branches. Ensure the 
repository remains clean and up to date.
- Utilize the configuration and functionality of the version control platform to automate the creation and deletion of 
branches, thereby strengthening the project's management of branches.
- Ensure that team members are proficient in utilizing GIT commands to effectively handle various scenarios.

## Make it easy to use
### Findings
- The repository contains various issues related to the quality and content of the readme files.
  - There is no readme at all.
  - The content in the readme lacks meaningful information and consists of vague statements like "This is a project of abc".
  - Team members treat the readme as a repository for internal notes, utilizing it to store various internal information 
  such as environment details, support group distribution lists, and release schedules.
- Despite the availability of code in the repository for download, it remains challenging for others to successfully build 
and run the project due to the lack of documentation on required special arguments, parameters, or dependencies.
- The repository lacks documentation for the necessary steps to build and run the project, as these instructions are located 
in the CI/CD or runbook external to the repository.

### Thoughts:
- It is crucial to have a comprehensive readme that provides an overview of the project and essential information for 
visitors to understand the repository. Consider the target audience and their specific information needs when organizing 
the readme. Take inspiration from well-established open-source projects to structure the readme effectively, including 
sections such as project description, main features, architectural overview, build and run instructions, quick start guide, 
configuration details, extensibility guidelines, frequently asked questions, and references.
- The project should provide a seamless experience for new developers to build and run by executing a single command, 
without the need for additional instructions. The build process should automatically fetch all dependencies from artifact 
repositories and generate a comprehensive package that includes all necessary files, such as configurations and shell 
scripts. Ideally, users should be able to effortlessly deploy the package to any desired location and initiate it by 
executing a simple shell script.
- Ensure that all necessary information is included in the repository. Utilize a pipeline file to consolidate all build 
steps, if applicable. Additionally, consider using DDL files to store all database initial scripts.

## Keep it clear
### Findings:
Some projects misuse the source code repository by including unusually large binary files, such as jar files, zip files, 
and even database files, resulting in repositories with sizes exceeding 1GB.

- Team members are accustomed to the large size of the repositories. When questioned about the reasons behind the repository's 
size, common responses include "our system is highly complex and contains a substantial amount of code" or "it has always 
been this way since I joined the team," without critically examining the underlying factors contributing to the size.
- Some developers blindly copy Gradle or Maven files from other projects to build a new project, resulting in an unnecessary 
number of files in the output.
- The presence of sensitive information in configuration files or test code poses a significant risk to information security.

### Thoughts
- The source code repository should primarily contain hand-written source code files and exclude generated files or dependencies. 
While certain exceptions may include small icon files as resources or screenshot files referenced in the readme, the majority 
of files in the repository should be manually created source code files.

- To prevent the inadvertent inclusion of non-source code files in the repository, it is recommended to utilize ```.gitignore``` 
files.
- As professional developers, it is essential to critically evaluate the size of our repositories. For instance, the Linux 
kernel's 5.11 release in 2021 consisted of approximately 30.34 million lines of code, occupying around 144 megabytes of 
disk space. We should question whether our project is more complex than the Linux kernel or if there are areas where we 
can optimize and reduce the size of our repositories.
- Developers should take ownership of managing project dependencies and have a clear understanding of their necessity and 
purpose, ensuring that only essential dependencies are included and unnecessary ones are avoided.
- It is imperative to never include any sensitive information, such as secrets or credentials, in the source code repository. 
The repository is accessible to all developers, particularly when transitioning to a platform like GitHub.

## Keep it building
### Findings:
- Despite the majority of the project being integrated with CI/CD tools, there is still a possibility of encountering 
build errors or late detection of failed unit tests due to infrequent builds.
- Team members often overlook the importance of addressing build failures promptly, as they have become accustomed to 
frequent build error alerts.
- Certain critical bugs remain undetected and unresolved during the early stages of development, causing delays in the QA 
testing process

### Thoughts:
Continuous Integration and Continuous Delivery(CI/CD) is a fundamental aspect of Agile software development methodologies. 
Ensuring the continuous building of our project and early detection of any build and test errors are crucial for enhancing 
productivity and efficiency.

- Leveraging webhooks to automatically trigger CI/CD tools upon commit or merge events, enabling prompt detection of any 
build or test errors. Ensuring immediate visibility into the outcome of recent changes (commits) aligns with the core 
principles of Agile software development.
- Prioritize addressing build errors as they can hinder the progress of other team members. To ensure a smooth development 
process, it is crucial to maintain a clean codebase and strive for successful builds as the default expectation.
- It is recommended to automate quality-related steps, such as unit testing, SonarQube checks, vulnerability scanning, and 
smoke testing, as part of the CI/CD process whenever possible. By detecting errors and bugs early in the development cycle, 
significant time and effort can be saved.

## Write Testable Code
### Findings:
- Developers often perceive writing unit tests as time-consuming and effort-intensive. It is not uncommon for them to write
  extensive mock code to cover a simple test point, resulting in a significant time investment. Some developers even express
  that it takes them more time to write test cases than to write the actual code itself.

- The process of writing code and writing test cases is often treated as separate tasks. Developers typically prioritize
  writing code first and then allocate whatever time is left for writing test cases. As a result, the quality of test cases
  can be compromised when time is limited.

- Developers are aware of the importance of adhering to SOLID principles in order to write testable code. However, in
  practice, they often postpone making the necessary code changes for improved testability, expecting a future refactoring
  opportunity that may never materialize.

- To "optimize" efficiency, project managers or team leads may assign senior developers to focus on writing code while
  assigning the task of writing test cases to junior developers or less experienced developers in remote locations.

### Thoughts:
Unit testing, clean code, Test Driven Development (TDD), and code refactoring are all familiar concepts to most developers.
However, it is important to take a step back and examine these concepts from a higher perspective to discover that they
all serve the principles of Agile programming methodology.

- Unit testing is essential for ensuring the quality of your code. It serves as a reliable mechanism to detect any issues
  or defects introduced by changes in a timely manner. For instance, if unit tests are fast enough, we can identify logical
  flaws as quickly as we spot compilation errors in our IDE, greatly enhancing development efficiency.

- Writing unit tests should be straight forward and require minimal complexity, such as excessive mocking or convoluted
  steps. If writing unit test cases becomes difficult or burdensome, it is essential to reflect on the quality of the code
  and identify potential issues that may hinder testability.

- Maintaining clean code is essential for adhering to SOLID principles and ensuring testability. By consistently following
  clean code practices, the process of writing unit tests becomes significantly easier.

- Code refactoring should be an integral part of the entire development process, as it is unrealistic to expect anyone to
  write perfect clean code in a single attempt.
- Test-Driven Development (TDD) is a valuable development approach that aligns with the principles of Agile methodology.
  It integrates coding and unit testing as inseparable components, where the creation of new test cases or the failure of
  existing tests drives the coding process. The challenge of writing test cases also serves as a means to identify code
  smells and prompts developers to refactor their code for improved quality. Test, code, refactor form iterative sprints
  that propel our development work forward until completion. As a result, when time is limited, prioritizing quality over
  features becomes the preferred approach. When we submit code, it is always have quality guaranteed and align with clean
  code standard.

- The preceding statement emphasizes the differentiation between unit testing and other forms of testing. Unit testing,
  classified as a white-box testing technique, is typically conducted by developers who are accountable for writing the code.
  This choice is determined by the development methodology employed.

## Favour Quality over Quantity
### Findings:
- Some teams only care the code coverage numbers without much interests in quality of the test cases, leading to numerous
  pitfalls and traps.
  - The test case is just making the code covered, but not tested.
  - Some teams even create tools to scan and detect ineffective test cases, which is a reactive approach that adds complexity
    to the testing process.
  - Use integration tests to falsely represent unit tests and artificially increase test coverage.

- Some teams prioritize increasing unit test coverage without considering the reasonableness of the tests, resulting in
  developers spending significant effort creating unnecessary test cases. This leads to unnecessary burden and wastage of
  resources.

- Using the number of test cases as the sole indicator of code quality often leads to the creation of ineffective test
  cases. This approach not only fails to improve software quality but also increases the maintenance cost of test cases.

### Thoughts:
- The primary objective of introducing unit tests is to enhance software quality, rather than solely focusing on code
  coverage. Code coverage is just one metric among many that should be considered. It is important to explore other effective
  measurements, such as the number of defects not captured by unit test cases, to assess the overall improvement in software
  quality.

- While unit tests are valuable, they have specific application area and scope, just like other types of tests. Don't try
  to use unit tests to find all defects in the code. Some code, such as integration with other systems (database, messaging,
  web API calls, etc.), is not the focus area of unit tests. Excessive mocking and the use of fancy mocking tools may increase
  code coverage numbers, but they do not significantly contribute to the overall quality. Such code should be covered or
  tested using other types of tests, such as integration tests.

- Establish an appropriate code coverage target. Beyond a certain threshold, increasing unit test coverage does not
  necessarily result in improved quality, but it can lead to higher costs. Alternatively, we can utilize coverage reports
  to identify lines of code or branches that are not covered and determine if they should be included in unit tests or
  tested through other forms of testing.

## Focus on Fast Feedback
### Findings:
- Misunderstanding of the "unit" in unit test. Some developers treat a module as a unit, while some others treat a restful
  controller as a "unit".
- Misunderstanding the concepts of Behavior Driven Development (BDD) and Test Driven Development (TDD)
- Developers often mix integration tests with unit tests, which can significantly slow down the execution of unit tests.
- The unit test cases suffer from inadequate isolation of dependencies, making it challenging to automate their execution.
  Manual steps, such as setting up test data in the database and cleaning up test side effects, are necessary. Furthermore,
  certain cases can only be executed once at a time due to conflicts in critical resource usage.

### Thoughts:
Unit tests play a crucial role in the development process by efficiently identifying and resolving defects. They align
with the principles of Agile methodology, enabling developers to address issues promptly during the development stage.
However, if unit tests are not able to fulfill this purpose effectively, such as when integration tests are used as a
substitute for unit tests, developers may revert to a waterfall approach where all code is written first before writing
test cases.

- Understand some key concepts in unit test correctly
  - In the context of unit testing, the term "unit" refers to the smallest testable component of an application, such as
    a function, method, procedure, module, or object. It is commonly understood that a "unit" typically refers to a method
    within a class.
  - BDD focuses on the behavior and functionality of the software from the user's perspective. TDD, on the other hand,
    is a development approach where developers write tests before writing the actual code. BDD can be seen as a higher-level
    approach that focuses on the overall behavior and collaboration, while TDD is more focused on the technical aspects of
    writing tests and code.

- A well-designed unit test possesses the following characteristics:
  - It can be executed at any time without any additional prerequisites or post-execution steps.
  - It is independent of external systems such as databases or services, allowing it to be executed in any environment.
  - It runs quickly, typically completing within milliseconds.
  - It can be executed multiple times and does not rely on a specific order.

  If a unit test fails to meet any of these criteria, it indicates a potential issue that needs to be addressed.

## Write Readable Tests
### Findings:
- Developers often use generic names like "test1" or "test2" for their test cases, assuming that they understand the
  purpose of each test case during composition. However, this naming convention can lead to confusion and inefficiency when
  other team members or stakeholders review the test cases at a later stage.

- Developers often neglect the importance of providing clear error messages when unit tests fail. This lack of attention
  to detail makes it challenging for developers to quickly identify the cause of the failure and obtain the necessary
  information from the test output or report. As a result, they are forced to spend additional time investigating the source
  code, leading to decreased efficiency and productivity.

- The excessive use of mock code or excessive preparation steps in test cases can lead to a loss of focus for readers.
- Combining multiple test points within a single test introduces complexity and can hinder comprehension. Furthermore,
  if one test point fails, it can impede the execution of subsequent test points, potentially resulting in cascading failures.

### Thoughts:
Unit test code, like any other code, is an integral part of our software delivery process. It is crucial to ensure that
the test code is clean, maintainable, and readable. Here are some key points to consider when writing unit tests.

- When writing unit tests, it is important to select informative and descriptive test names. This helps reviewers understand
  the purpose of the test and saves time when troubleshooting failures. Additionally, providing detailed error messages or
  annotations can provide additional information when a test fails.

- As mentioned in the previous section, if our code is well-designed and follows best practices, the corresponding test
  cases should naturally be straight forward and simple. It is advisable to review and refactor your code if you find that
  the test cases are overly complex and lengthy. Test cases serve as a catalyst for developers to identify any code quality
  issues and facilitate refactoring within their agile development cycle.

- It is recommended to ensure that each test case focuses on a single functionality or scenario. By doing so, a single
  round of unit test execution should be able to uncover all failures, rather than resolving one issue only to encounter
  another.

## Make Meaningful Assertions
### Findings:
- Developers often prioritize writing assertions for the main path of the code and overlook the importance of testing
  error handling scenarios, especially in complex scenarios like below. This is due to the challenges involved in simulating
  these scenarios during test case execution.
  - Retry logic. If something goes wrong, attempt multiple retries, resume execution if any retry succeeds, or throw
    an exception when all retries fail.
  - Complex error handling. Wrap some type of exceptions with another one.
  - Auto recover. Keep trying to connect, when succeeded, continue with normal processing.

- Insufficient or improper assertions may result in missed test points that are critical for ensuring the correctness of
  the code. Even though the lines or branches may be covered by tests, there is still a risk of undetected bugs.

### Thoughts:
- It is important to write test cases that align with the identified test points in the source code. By thoroughly
  understanding the test points, developers can create appropriate test cases with meaningful assertions to cover these
  specific areas of functionality.

- When writing tests, it is important to consider different ways to assert the test results in order to effectively
  validate the desired test points. This can include direct return value assertions, object state assertions, exception
  assertions, or even assertions on the number of times a method is called.

## Ensure Deterministic Results
### Findings:
- Some unit test cases can only run in specific environments due to their dependencies on local system resources such as
  files or OS-specific configurations, which restricts the execution of these test cases to specific locations.

- Some unit test cases are fragile as they heavily rely on external systems or services. If the dependent system or service
  is not functioning properly, the test case will inevitably fail.

- Some unit test cases' execution results are very wield. They failed randomly because the test case execution is running
  in multi-threading context, which may impact the execution result if the test logic depends on thread execution order.

- Some test cases have implicit ordering requirements that are related to mutable states. If the test cases are not executed
  in the predefined order, they will not function correctly. For instance, the delete trade test case can only be executed
  after the create trade test case.

### Thoughts:
- To ensure the portability and reliability of unit test cases across different execution contexts, it is imperative to
  design each test case in a manner that is isolated and independent of specific resources, systems, or services. This
  guarantees consistent and accurate test results regardless of the environment in which the tests are executed.

- If it is difficult to achieve the first point mentioned above, it is advisable to revisit the code to be tested and
  assess its cleanliness and alignment with the SOLID principle.

- It is important to avoid implicit dependencies between test cases, as each test case should be independent and not
  impact the execution or outcome of other test cases. If achieving this independence proves challenging, it is récommended
  to review and refactor the code being tested to eliminate any implicit ordering requirements.

- It is advisable to prioritize testing the logic within a single thread, If there is a genuine need to test the logic
  under a multi-threading context, careful evaluation is necessary. Generally, unit testing is not the appropriate stage
  for conducting tests such as multi-threading tests, performance tests, stress tests, or destructive tests.

## Use the Right Tools for the Job
### Findings:
- Over-reliance on mocking tools in unit testing which results in lengthy and complex test cases that are difficult to
  understand.
- Excessive reliance on unit test case generation tools to expedite the testing process undermines the catalytic effect
  of unit tests in facilitating code refactoring.

### Thoughts:
Mocking tools and case auto-generation tools can provide convenience and time-saving benefits for developers to a certain
extent. However, it is important to note that these tools have limitations and potential side effects. It is crucial to
carefully consider their application scope and suitability for specific scenarios, as there is no universal solution or
silver bullet that can address all issues.

- In typical scenarios, extensive mocking is not often required. Well-designed code can be easily tested using modern
  object-oriented language features such as inheritance, method overriding, and internal anonymous classes to achieve
  dependency isolation.

- In certain projects that utilize dependency injection frameworks like Spring Boot, the Spring Test framework can be
  employed to effectively isolate dependencies during testing.

- Mocking tools and case auto-generation tools can be valuable resources for creating test cases in legacy code bases
  without requiring code modifications. These tools can significantly reduce the effort required by developers.

- It is recommended to adopt a pragmatic approach by incorporating Test-Driven Development (TDD) principles during new
  development. Additionally, leveraging auto-generated tests can be beneficial to enhance test coverage and identify easily
  detectable issues.

- Again, when encountering challenges in writing unit test cases, it is important to prioritize code review and potential
  refactoring as the initial step, rather than relying solely on advanced mocking tools or test case generation tools.

## Conclusion
Mastering the fundamentals of software development is not just a matter of personal discipline—it is the cornerstone of 
building robust, maintainable, and scalable systems. While new technologies and tools continue to emerge, it is the consistent 
application of these basic principles that truly differentiates high-performing teams and successful projects. By going 
back to basics and fostering a culture of craftsmanship, we can reduce recurring issues, accelerate onboarding, and deliver 
higher quality software. Let us not overlook the power of fundamentals in our pursuit of innovation and excellence.
