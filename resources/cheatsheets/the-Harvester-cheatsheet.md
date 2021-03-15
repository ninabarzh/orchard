# the Harvester cheatsheet

The [theHarvester version in kali](https://github.com/laramies/theHarvester) has been completely overhauled. The tool gathers emails, names, subdomains, IPs and URLs using multiple public data sources which includes a whole list of search engines for passive information gathering, plus active tools "DNS brute force" (dictionary brute force enumeration) and "Screenshots": Take screenshots of subdomains that were found.

## Options

    -d: Domain to search or company name
    -b: data source: baidu, bing, bingapi, dogpile, google, googleCSE, googleplus, google-profiles, linkedin, pgp, twitter, vhost, virustotal, threatcrowd, crtsh, netcraft, yahoo, all
    -s: start in result number X (default: 0)
    -v: verify host name via dns resolution and search for virtual hosts
    -f: save the results into an HTML and XML file (both)
    -n: perform a DNS reverse query on all ranges discovered
    -c: perform a DNS brute force for the domain name
    -t: perform a DNS TLD expansion discovery
    -e: use this DNS server
    -p: port scan the detected hosts and check for Takeovers (80,443,22,21,8080)
    -l: limit the number of results to work with (bing goes from 50 to 50 results, google 100 to 100, and pgp doesn't use this option)
    -h: use SHODAN database to query discovered hosts

## Examples

    theharvester -d [domain] -l 500 -b google -h harvester_results.html
    theharvester -d [domain] -b pgp
    theharvester -d [name] -l 200 -b linkedin
    theharvester -d [domain] -b googleCSE -l 500 -s 300



