# npm

* Avoid publishing secrets (API keys, passwords or other secrets) to the npm registry. 
  * When updating the `.gitignore` file, also update `.npmignore`.
  * The ignore files function as blacklist. Instead, use the `files` property in `package.json`. It works as a whitelist and specifies the array of files to be included in the package (the ignore file functions as a blacklist). They can be used together to determine which files should explicitly be included and excluded from the package. The `files` property in `package.json` takes precedence over the ignore file.
  * Before publishing do a dry run by adding the `--dry-run` argument to the publish command to review what will be in the tarball.
* Enforce the lockfile (`yarn install --frozen-lockfile`, `npm ci`)
* Reduce attack surface
  * Do not immediately and blindly upgrade to new versions; wait a while (but not until they are outdated of course).
  * Before upgrading, review changelog and release notes.
  * When installing packages, add the `--ignore-scripts` suffix to disable the execution of scripts by third-party packages.
  * Perhaps add `ignore-scripts` to the `.npmrc` project file or the global npm configuration.
* Maintain project health
  * Run `npm outdated` to see if any packages are out of date.
  * Run `npm doctor` to review the npm setup.
    * Check that the official npm registry is reachable and displays the currently configured registry.
    * Check Git is available.
    * Review installed npm and Node.js versions.
    * Run permission checks on the local and global `node_modules`, and package cache folders.
    * Check the local npm module cache checksum.
* Audit for vulnerabilities in open source dependencies. Scan with `snyk` and/or `npm audit`. See [Comparing npm audit with Snyk](https://www.nearform.com/blog/comparing-npm-audit-with-snyk/)
