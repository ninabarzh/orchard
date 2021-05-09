# Choosing file sharing services

[Google Drive](https://transparencyreport.google.com/) and [Dropbox](https://www.dropbox.com/transparency/reports) are probably not really private. The problem with their privacy policies and terms of service is not that they are malicious - they're there to help provide the service, but that they could be misused easily. There is no language that compels either to act in a user's interest. Alternatives that do use such language exist.

## Dropbox 
Edward Snowden has warned against the cloud storage service Dropbox which he says is [hostile to privacy](https://www.theguardian.com/world/video/2014/jul/17/edward-snowden-video-interview), and called for more services to offer the //zero knowledge// which have no decrypted access to user data.

//"They just put … Condoleezza Rice on their board… who is probably the most anti-privacy official you can imagine. She's one of the ones who oversaw Stellar Wind and thought it was a great idea. Another indicator they are indeed hostile to privacy."//

## Google drive
Google Drive is one of the most widespread cloud-storage services around, but between the National Security Agency (NSA) and Google's own overreaching terms of service, your files may be open to snooping from both organizations. [[https://venturebeat.com/2013/06/19/google-issues-clearest-statement-yet-on-nsa-and-prism-no-server-access-no-back-door-no-drop-box-no-free-for-all/|Google denies]] granting the NSA unlimited access to private data.

Google provides a browser, email, a search engine and global navigation and supposedly PRISM can collect information from any of these services as well as from Google Drive, the cloud-storage platform. Drive has two components: Create and Upload.

[Google's privacy policy](https://www.google.com/policies/privacy/) states that Google can collect device, login and location information, and in case of Chrome, also collects browser history, plants cookies and records what other applications were used.

The Google Drive FAQ says the company will not use any data you mark as private for marketing or promotional purposes, but according to its terms of service (Your Content in our Services) Google can //use, host, store, reproduce, modify, create derivative works (such as those resulting from translations, adaptations or other changes we make so that your content works better with our Services) communicate, publish, publicly perform, publicly display and distribute such content.//

## Onionshare

An alternative, especially when distributing unauthorised content is [[https://github.com/micahflee/onionshare/wiki|Onionshare](https://docs.onionshare.org/2.3.1/en/), which allows for sending big files via Tor. When sharing a file, the program creates a Tor Hidden Service — a temporary, anonymous website — hosted on your computer. Give the intended recipient of the file the .onion address for that site, and they can securely and anonymously download it through their Tor Browser.

## Sparkleshare

Another alternative is [Sparkleshare](https://www.sparkleshare.org/). SparkleShare was made to cover [certain use cases](https://github.com/hbons/SparkleShare/wiki) (designers at the  GNOME Usability Hackfest in London came to the conclusion that they didn't have a good (Open Source) collaboration tool to share their work), but doesn't handle every scenario well. It is not suited for full computer backups and large binary files that change often, like video editing projects.

Once its setup, it is as easy to use as Dropbox, but setting it up takes a bit more work than Dropbox. It builds upon two software packages well known for security and reliability: git and ssh, and works with Tor Hidden Services. It runs on Windows, Mac OS X, and GNU/Linux, and tan Android client is in the works.

