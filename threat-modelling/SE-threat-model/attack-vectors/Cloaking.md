# Cloaking

With cloaking techniques visitors and crawler are served different content, such as is the case in sneaky redirects (code swapping), where a page is optimised for a search engine and when top ranking is reached, swapped for another page. Cloaking can be part of an attempt to mislead search engines.

Simple forms of cloaking can be based on:

* HTTP Referer (the URL of the page on which a user clicked a link)
* User-Agent (information on a user's system, in particular OS and browser used)
* IP address of visitor

More complex forms can be based on behavioural analysis. Parameters in which crawlers differ heavily from a natural user behaviour:

* The quantity, sorting of and latency between subsequent HTTP requests
* The presence of a check for robots.txt file (some spiders do not)

Without the use of cloaking, the content fetched by a search engine crawler, the “crawler view”, and the user “direct view” will be identical, but a doorway page will have scripts to detect whether it is an actual user loading the content in a web browser, in which case the user will be redirected (based on the user’s action, such as mouse movement or rendering of the page in the web browser) to the final landing page containing the malicious content.

* In so-called “mosaic cloaking” dynamic pages are constructed as tiles of content and only in parts of the pages JavaScript and CSS are changed, decreasing the contrast between the cloaked page and the “friendly” page while increasing the capability for targeted delivery of content to various spiders and human visitors.
* In “IP delivery” different content is served based upon the requester's IP address, allowing for location based search results. Search engines and people can see the same pages. This technique is sometimes used by graphics-heavy sites that have little textual content for crawlers to analyse.

## False positives

For the most part cloaking is used to deceive search engines, but cloaking can also be used for less nefarious purposes:

* Providing human users with content that search engines can not parse, for example an easily digestible, text-only version of a page or to provide link-based access to a database normally only accessible via forms, but .
* Increasing accessibility of a site to visitors with disabilities.
* Delivering content based on location or previous online behaviour (comes with a serious privacy issue!).

## Known mitigations

Cloaking is considered to be highly manipulative and heavily penalised by search engines, including the complete removal of sites from being indexed.

* Cloaking can be discovered by crawling a website twice, once with a crawler the cloaker believes is from a search engine, and once with a crawler the cloaker believes is not a search engine and comparing results. This is perhaps not good enough, because pages can change between downloads for legitimate reasons.
* Existing gold standard fraud datasets using rule-based heuristics assume fraudsters create objects in a short period of time, from the same IP address, or have a skewed rating distribution. Difficult to validate, and fraudsters keep learning and adapting too.
* Fraud de-anonymization algorithms have been developed but would make us the petty tyrant we fight.
* Better yet, maybe build a spam classifier that reliably detects a large fraction of the currently existing spam categories, and in combination with that perhaps unsupervised ML can be trained to label spam or not-spam for the future.


