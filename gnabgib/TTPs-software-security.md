# TTP's software security

There is no single tool, technique, or process that will guarantee that software is secure. Each approach has its own strengths and limitations. Use a fitting combination:

## Architecture, design and management

* Security testing often lacks systematic approaches enabling problem solving oriented identification, selection and execution of test cases. One approach to solving this problem is to use risk-oriented testing, where software risks analysis is used as the guiding factor to solve decision making problems during testing, in particular selection and prioritisation of test cases.
* Threat modelling can be useful for finding problems before code is developed and for risk analysis, but it is difficult to teach and requires expert participation.
* Architecture and design validation can be important for detecting problems that would be too difficult, time-consuming, or expensive to fix after the product has been deployed, but require expert-level participation.
* Education, training and coaching will help programmers avoid introducing errors into code in the first place, reducing downstream costs, but may be expensive, can face cultural challenges for adoption, and require further coaching as the application and detection methods evolve.

## Implementation

* Coding standards can reduce the number of weaknesses that are introduced into code, which may save on maintenance costs, but can be difficult to integrate into existing projects.
* Automated static code analysis for source code or binary code can give a good code coverage for implementation errors, but report a large number of issues that a developer may not wish to address. And design-level problems require human analysis. Manual code review: Knowing code is going to be reviewed, stimulates looking it over first, and having to explain it to a reviewer, problems that may have been missed before may become apparent. And if something in the code is not immediately clear to the reviewer, this can be taken as an indication that a better name, an additional comment, or a refactoring is required. And a reviewer may find other problems too, including in nearby code and works well for finding subtle errors and design flaws, and for giving an overall assessment of development practices, but can become expensive and may not catch each and every attack vector.
* Automated dynamic code analysis can find issues that are difficult to detect with static analysis, but code coverage is a problem. Manual dynamic code analysis such as pen-testing can be effective for understanding the overall security of the software.

## System administration and environment lock-down

* Application firewalls and external monitoring/control frameworks (web application firewalls, proxies, IPS, Struts, etc.) are useful mostly for protecting software that is known to contain weaknesses, but customisation may be needed, and not all attacks can be automatically detected or prevented.
* Automated vulnerability scanning of web application, web service, databases and network with automated tools can give some surprising results saving a lot of time down the road, and do not take much time and effort. Well worth it.
* In addition, configuration analysis tools that test configurations for adhering to security policies for particular software or devices may exist.
