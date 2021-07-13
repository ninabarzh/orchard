# npm

The JavaScript ecosystem is the largest in the world, and the npm repository includes nearly 100,000 libraries.
* [npm Security](https://www.npmjs.com/policies/security) 

## What can possibly go wrong?

* Developers accidentally publish secrets (API keys, passwords or other secrets) to the npm registry. If there is a `.gitignore` or a `.npmignore` file, the content of either is used as ignore patterns when preparing a package for publication. If both exist, everything not located in `.npmignore` is published to the registry. 
* Yarn and npm, when detecting an inconsistency between the project’s `package.json` and the lockfile, compensate for it based on the `package.json` manifest by installing different versions than those recorded in the lockfile. This can pull in unintended package versions.
* The npm cli builds on scripts that a package can declare, which are allowed to run at specific entry points during the package’s installation in a project. Some of these script hook entries may be postinstall scripts. This opens the door for adversaries to create or alter packages to execute malicious code.
* Many popular npm packages have been found to be vulnerable and may carry a significant risk without proper security auditing of the project’s dependencies.

