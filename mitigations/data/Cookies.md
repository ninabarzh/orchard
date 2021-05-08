## Cookie monsters

Third party cookies store our data on a server, a major privacy concern. Although going extinct, third party cookies are still in use by, for example, many Wordpress (feature) plugins. Wordpress covers around 30% of the websites on the internet.

### Webmasters

Make the site GDPR compliant with, for example for Wordpress, plugins like [Complianz – GDPR/CCPA Cookie Consent](https://wordpress.org/plugins/complianz-gdpr/) or [WordPress compliance with GDPR/ePR and CCPA](https://www.cookiebot.com/en/wordpress-cookie-plugin/). Both give a list of all third-party cookies, including the hidden ones, being transmitted by the site to visitors. 

### Users

For not accepting third party cookies:

Firefox: Preferences -> Privacy -> Accept third-party cookies -> Never.

Chrome (also chromium): Settings -> Show advanced settings… -> Content settings -> Block third-party cookies and site data.

When changing the default cookie "lifetime" from "Keep until: they expire" to "Keep until: I close Firefox", Firefox changes any persistent cookies that sites set to session cookies. To allow a site to set a persistent cookie, an exception (site permission) must be made. 

For clearing cookies on exit:

Firefox/Tools -> Options -> Privacy -> "Use custom settings for history" -> Cookies: Keep until: "I close Firefox".

Chrome (also chromium): Settings -> Show advanced settings ... -> Content settings -> Keep local data only until you quit your browser.

When turning on the clearing of history at shutdown and include cookies, a completely separate process runs which does not pay any attention to cookie lifetime or exceptions (site permissions). It just nukes them all. Note that some cookies might survive clearing at shutdown if they are encoded into the session history file, the one Firefox uses to restore previous session windows and tabs.



