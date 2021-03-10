# Doorway pages

Doorway pages (alias SEO poisoned pages, bridge pages, portal pages, jump pages, gateway pages, entry pages) are keyword­-stuffed pages designed to rank highly in search engine results and redirect users to a rogue site. Such doorway pages can easily be generated and managed with a so-called SEO kit.

* The attackers often use holidays and other timely occasions that are likely to generate a lot of search interest, such as elections.
* By hosting [search engine poisoning](../attacks/Search-engine-poisoning.md) within a legitimate site, the attackers can piggyback on the reputation of that site, making it harder for the search engines to identify and remove the rogue links. To upload to the legitimate site vulnerabilities in content management system or hosting web server are used.
* Doorway pages are generated dynamically (often by Perl or PHP scripts) and extract text from search results from any major search engine. The latest “hot” keywords can be found in resources like Google Trends. Metadata is extracted from the search engine results and added to the links on doorway pages. The generated content can also be cached by the SEO kit.
* The doorway page links to other doorway pages so they'll be indexed, and/or links to the doorway pages that are posted on other legitimate web sites in forums, blog comments sections, guest books, social networking status updates, and so forth. This gets the pages indexed by the search engine crawlers.
* If a searcher clicks on a typical doorway page link from a search engine results page, in most cases they will be redirected to another page by a fast Meta refresh command, JavaScript and server side redirection, from the [server configuration file](Misconfigurations.md), or simply by tricking the visitor into clicking on a link to get them to the desired destination page.

## False positives

Landing pages are regularly misconstrued to equate to Doorway pages within the literature. These are content rich pages designed to redirect traffic within the context of pay-per-click campaigns and to maximize SEO campaigns. 


