# SonarQube Cloud Integrations
## WHAT IS SONARQUBE?
    - SonarQube is a Code Quality Assurance tool that collects and analyzes source code, and provides reports for the code quality of your project.      
    - Sonarqube also ensures code reliability, Application security, and reduces technical debt by making your code base clean and maintainable. Sonarqube also provides support for 27 different languages.

### Dynamic Code Analysis
**Dynamic Code Analysis** relies on studying how the code behaves during execution. The objective is to find errors in a program while it is running, rather than by repeatedly examining the code offline. Some things that Dynamic code analysis does are:
1. **Code Coverage**: Computing how much a piece of code gets tested by test suites
2. **Memory error detection**: Checking whether or not memory leaks or errors occur
3. **Fault localization**: Locating the buggy code to a specific location
4. **Invariant Inference**: Observes the values that the program computes, and then report properties that were true over the observed executions, and this likely true over all executions.
5. **Security Analysis**: Detect security problems.
6. **Concurrency errors**: Dynamic Uses runtime error detection to expose defects such as race conditions, exceptions, resource and memory leaks, and security attack vulnerabilities
7. **Program slicing**: Consists of reducing the program to the minimum form that still produces the selected behavior.
8. **Performance Analysis**: dynamically tracing software applications at runtime and captures data that can be used to analyze and identify the causes of poor performance.

### Principles
1. The code should follow a specific convention.
2. The code should be following established good practices and have been followed.
3. Checked for potential bugs and performance, security, or vulnerabilities issues.
4. Is the code duplicated anywhere.
5. Does the code make logical sense, or is it too complex.
6. Does the public API have good documentation and comments
7. Does the code have unit tests.
8. Does the code follow good software design and architecture principles.