# Web servers

* [Apache](apache)
  * [Chroot Apache](apache/Chroot-Apache.md)
  * [Hide version and OS identity](apache/Hide-version-and-OS-identity.md)
  * [Disable directory listing](apache/Disable-directory-listing.md)
  * [Restrict file and directory access](apache/Restrict-file-and-directory-access.md)
  * [Install and use mod_security](apache/mod_security.md)
* [Nginx](nginx)


## Notes

* Reduce information disclosure (OS, version, ServerTokens)
* Use a firewall.
* Disable unused services.
* Monitor web traffic for unusual activity.
* Conduct regular, remote security scans.
* Conduct regular, local security scans.
* Guard against application level DOS attacks by limiting field input length.
* Disable url fopen if possible.
* Enable safe mode, include directory and open base restrictions if possible.
* Disable dangerous PHP functions if possible.
* Be careful with naming files *.bak, *.txt or *.inc within the web document root.
* Be careful using version management tools on doc root.