# Code reviews

## Manual code reviews

Code reviews not only improve code quality, in general they drive increased maintainability by
  * Establishing a common yet evolving mental model 
  * Building confidence in direction and design alternatives/decisions
  * Enabling more effective funding requests
  * Exposing end-user interaction points
  * Establishing consensus on supported workflows
  * Discovering best practices

Code reviews also facilitate increased system effectiveness: Knowing code is going to be reviewed, stimulates looking it over first, and having to explain it to a reviewer, problems that may have been missed before may become apparent. And if something in the code is not immediately clear to the reviewer, this can be taken as an indication that a better name, an additional comment, or a refactoring is required. In addition, a reviewer may spot vulnerabilities, subtle errors, unnecessary code and design flaws, including in nearby code. 

## Pull request reviews
 
Code reviews done by the entire team take a lot of everyone's time, and as a result these reviews become few and far between and only a small percentage of the code base will get reviewed. The "another person reviews changes before commit" usually works better, and in the case of a dedicated reviewer may give the reviewer (and if communicated and documented well for the entire team) an impression of used development practices and architecture "as is".

There are some warnings though: 
* When the change is trivial, it may make little sense to have it reviewed. The discipline to still stick to doing it prevents the slippery slope of declaring changes to be "trivial" when they are not. 
* This is not a very good way to review significant changes to the system or the addition of large new components. For phased changes (not too large refactoring) it can work.
* It can become expensive and may not catch all attack vectors.

Not perfect, but is mentioned as having noticeably improved code quality in several projects if:
* Time is devoted to it
* Debt is accepted
* Churn is identified 
* Pedantry (excessive concern with formalism, accuracy, and precision leading to style over substance) is minimised. 

## Review focus

* Does it work according to intent (spec/user stories)?
* Is it tested?
* Single purpose for a commit?
* Algorithmic complexity
* Exception and error handling
* Exception, class, and variable naming
* Logging sufficiency and level
* Long lines and methods
* Readability


