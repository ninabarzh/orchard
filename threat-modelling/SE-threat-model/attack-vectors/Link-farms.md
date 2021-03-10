# Link farms

Link farms are connected networks of sites (cliques) linking to each other for gaming search engine ranking algorithms.

## Evolution

Link farms were developed by search engine optimizers in 1999 to take advantage of the Inktomi search engine's dependence on link popularity. Inktomi was targeted for manipulation through link farms because it was then used by several independent but popular search engines. Link farm exchanges at the time were merely informal agreements and because there was money to be made, several companies appeared offering automated registration, categorisation, and link page updates to “member web sites”. The Inktomi engine maintained two indexes. Search results were produced from the primary index which was a limited list. Pages with few inbound links fell out of the Inktomi index on a monthly basis. Yahoo was Inktomi’s biggest customer and began complaining because when you typed “Yahoo” they were not number one in their own search results. It was dubbed “the relevancy problem”.

Inktomi then tried to build a tool to “measure the relevance effect of algorithmic changes based on precomputed human judgements” giving a score between 1 and 10. Meanwhile, Google's ranking algorithm depended in part on a link-weighting scheme called PageRank. The PageRank algorithm determines that some links may be more valuable than others, and therefore assigns them more weight than others.

Ah, and there is money to be made. The early link farms were vulnerable to manipulation by webmasters who joined the services, received inbound linkage, and then found ways to hide their outbound links or to avoid posting any links on their sites at all. Link farm managers had to implement techniques to guard “fairness”.

Blackhat SEO link farm products appeared, in particular link-finding software that identified potential reciprocal link partners, sent them template-based emails offering to exchange links or to place articles on their sites (with (hidden) links), and created directory-like link pages for its “members”, for building their link popularity and PageRank “position”.

## Known mitigations

Search engines countered by identifying specific attributes associated with link farm pages and filtering those pages from indexing and search results. In some cases, entire domains were removed from the search engine indexes in order to prevent them from influencing search results. In February 2011, Google launched Google Panda, intended to improve its spam-detection algorithm.

Panda “scores” websites on their content and user-experience to reduce the prominence of websites which have ‘thin’, low quality and duplicate content. It also targets sites which come up short on other site-quality metrics, e.g. high advert-to-content ratios. Panda benefited sites with lots of “high-quality and unique” content and which had recognised and trusted brands, thereby favouring corporate interests over purely informative content.

The Google Panda patent ([US Patent 8,682,892, USPTO, 2014](http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08682892&OS=PN/08682892&RS=PN/08682892)), filed on September 28, 2012, was granted on March 25, 2014. The patent states that Google Panda creates a ratio with a site's inbound links and reference queries, search queries for the site's brand. That ratio is then used to create a site wide modification factor. The site wide modification factor is then used to create a modification factor for a page based upon a search query. If the page fails to meet a certain threshold, the modification factor is applied and, therefore, the page would rank lower in the search engine results page.

### PageRank

PageRank, developed by Larry Page and Sergey Brin, is one of the most widely used page ranking algorithms and is based on the idea of a ’random surfer’. The possibility for a web page to be clicked is determined by:

* The original importance of the webpage
* The total number of web pages that link to it
* The importance and the forward link number of each of these web pages.

If a page has important links to it, its links to other pages also become important. Therefore, PageRank takes the backlinks into account and propagates the ranking through links: a page has a high rank if the sum of the ranks of its backlinks is high.

Pages are seen as Markov Chain states and the probability for moving from a page to another page is modelled as a state transition probability. The output of the algorithm is a probability distribution used to represent the likelihood that a person randomly clicking on links will arrive at any particular page. PageRank can be calculated for collections of documents of any size. It is assumed in several research papers that the distribution is evenly divided among all documents in the collection at the beginning of the computational process. The computations require several passes (iterations) through the collection to adjust approximate PageRank values to more closely reflect the theoretical true value.

In practice, the PageRank concept is vulnerable to:

* Black SEO (adding hidden anchor tags to a site and using link farms and hijacked blogs) because one page is important if it is pointed to by many other pages and it is based on link structure
* Spamming and fake news because it does not distinguish between good and bad authorities.

### TrustRank and Anti-TrustRank

TrustRank can be added to PageRank. Instead of relying on only the number of web links from one page to another it then also uses the variable “trust” it has in an object it is linked to. TrustRank generates trust for all indexed objects and gives objects with a lot of spam content a much smaller score while giving sites which link to trusted authorities a higher score. This prevents cascades of fake news to build up while also penalizing dirty tricks for SEO.

TrustRank selects a small set of seed pages to be evaluated by an expert. Once the reputable seed pages are manually identified, a crawl extending outward from the seed set seeks out similarly reliable and trustworthy pages.

* TrustRank's reliability diminishes with increased distance between documents and seed set.
* The inverse logic also works (Anti-TrustRank). The closer a site is to spam resources, the more likely it is to be spam as well.
* The researchers who proposed the TrustRank approach have continued to refine their work by evaluating related topics, such as measuring spam mass (the measure of the impact of link spamming on a page's ranking).
* So have others. There is now a fast asynchronous Anti-TrustRank algorithm.
* It is important to select good seeds in the Anti-TrustRank algorithm since the ATR scores are propagated from the selected seeds.



