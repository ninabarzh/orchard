## Browser data

The way in which browsers are configured (especially the browser plugins used), together with details of the Operating System in which the browser runs, allows its users to be uniquely identified and tracked. 

### Private browsing

Privacy mode or "private browsing" or "incognito mode" is a privacy feature in some web browsers to disable browsing history and the web cache. This allows for browsing the internet without storing local data that could be retrieved at a later date, as in, **not saving** a history of the pages visited on the Internet. 

  * Private browsing in Chrome is called Incognito. To open an Incognito window in Chrome, click Settings. From the drop-down menu, click New Incognito Window.
  * For a Private Browsing window in Firefox, click Settings. From the drop-down menu, select New Private Window.
  * Turn Private Browsing on or off on an iPhone, iPad, or iPod touch by opening Safari and tapping Settings, Private, and then Done.

### Browser plugins

There are a lot of browser extensions and plug-ins supposedly protecting users against tracking: 
* The presence or absence of plug-ins provides a large amount of information. `NavigatorPlugins.plugins` (JS) is still supported by some browsers. It returns a PluginArray object, listing the Plugin objects describing the plugins installed.
* Some plug-ins themselves will happily provide websites with a large amount of identifying information about a user, including the list of installed fonts, CPU model and speed, IP addresses, username, hostname, etc. Plus plug-ins can also have their own data and cookie stores, that they allow websites to manipulate.
* Apparently it is even possible to [use the NoScript plugin to gather information](https://hatsoffsecurity.com/2020/05/01/noscript-plugin-forensic-investigation-firefox-tor-browser/) about what sites, or files, a user accessed while in a private browsing session and also whilst using the TOR browser. 

### Browser configuration editors

Configuration editors can be used to change some of the browser settings to non-unique nonsense. 

* Firefox: [about:config](https://support.mozilla.org/en-US/kb/about-config-editor-firefox)
* Chrome: [chrome://about](https://www.howtogeek.com/104631/find-hidden-features-on-chromes-internal-chrome-pages/)

### User-agent switchers

You can add your own user-agents, and even mimic being a webspider and switch between them. For a list of convincing user-agents see this [searchable database](http://www.user-agents.org/index.shtml) of user-agents as used by browsers, search-engines spiders and crawlers, web-directories, download managers, link checkers, proxy servers, web filtering tools, harvesters, spambots, and badbots. 

Reuseful user-agent switcher extensions exist to make life easier (not available for all versions though): 

* [Chromium user agent switcher](https://chrome.google.com/webstore/detail/user-agent-switcher-for-c/djflhoibgkdhkhhcedjiklpkjnoahfmg) 
* [Firefox user agent string switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-string-switcher) . 


