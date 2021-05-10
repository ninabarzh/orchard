# Python

Python is one of the most used language on the internet and the [PyPI](https://pypi.org/) repository contains the most used libraries. Everybody can upload packages to it. 

## What can possibly go wrong?

* Packages added to PyPI do not undergo review. PvPI is run by volunteers and expecting them to review each and every addition would be entirely unrealistic.
* Some packages may have the appearance of open source software (they are freely available), but they are not explicitly open source. 
* Although Python 3 has been out for more than a decade, and support for Python 2 ended January 1, 2020. Many production sites are still running Python 2.7 and are open to security vulnerabilities.
* A developer runs `pip freeze` on a development machine, dumps the resulting list of packages and versions into a `requirements.txt`, and then uses that file to set up a production environment. When pinning dependencies, the project is frozen in time and leaves the project exposed to new security vulnerabilities when these are found and remediated for those open source dependencies. 
* In 2.7, implicit relative imports do not specify a location relative to the current module. If the module is found in the system path it is imported, which could be dangerous. It could be possible to create a malicious module with the same name as a popular module and then smuggle it into a popular open source library. If the malicious module is found in the system path before the real module it is imported instead. In 3, implicit relative imports are no longer supported.
* Developers often use `pip`, the standard package installer for Python, although `Pipenv` is the more secure alternative.
* String formatting has become extremely flexible and powerful (f-strings are particularly interesting) and the potential for exploits kept pace.
* Pickle allows for serialisation and deserialisation of Python object structures. Deserialising pickled python object structure from an untrusted source can result in malicious code execution. 
* PyYAML has a similar vulnerability. Using `yaml.load` on a YAML file from an untrusted source could execute Python code. PyYAML however, offers `yaml.safe_load`.


