# Browser plugins

There are a lot of browser extensions and plug-ins supposedly protecting users against tracking: 
* The presence or absence of plug-ins provides a large amount of information. `NavigatorPlugins.plugins` (JS) is still supported by some browsers. It returns a PluginArray object, listing the Plugin objects describing the plugins installed.
* Some plug-ins themselves will happily provide websites with a large amount of identifying information about a user, including the list of installed fonts, CPU model and speed, IP addresses, username, hostname, etc. Plus plug-ins can also have their own data and cookie stores, that they allow websites to manipulate.
* Apparently it is even possible to [use the NoScript plugin to gather information](https://hatsoffsecurity.com/2020/05/01/noscript-plugin-forensic-investigation-firefox-tor-browser/) about what sites, or files, a user accessed while in a private browsing session and also whilst using the TOR browser. 