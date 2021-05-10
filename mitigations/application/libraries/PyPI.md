# PyPI

* Assume that there are malicious packages within PyPI. Do a bit of research on the package you want to install and carefully spell out the package name when installing it (a package named for a common misspelling of a popular package could execute malicious code).
* Make yourself familiar with the licenses necessary for the projects you use, so you are sure that you are not compromising yourself legally.
* Scan for security vulnerabilities with [Bandit](https://bandit.readthedocs.io/en/latest/), available through the Python Packaging Index (PyPI)
* Use `Pipenv`, a tool for managing the competing interests of having a predictable development environment and having an up-to-date development and production environment. It uses a two-file system that separates abstract dependency declarations from the last tested combination. 
* Even when using Python 3, it is still important to keep in mind that import statements execute the code within the target module.
* The requests library handles SSL certificate verification. This library uses a package called `certifi` to validate the trustworthiness of certificate authorities. Maintaining the most updated version of certifi and ***never ever pin this dependency***. Oh, and do not bypass a certificate verification request. 
* Do not deserialise data from an untrusted source, and for PyYAML always use `yaml.safe_load`.
* Look into dependency analysis tools. There are some free tools available such as [ochrona](https://github.com/ochronasec/ochrona-cli).
