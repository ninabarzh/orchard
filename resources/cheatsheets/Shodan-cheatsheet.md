# Shodan cheatsheet

The basic search filters:

* city: find devices in a particular city
* country: find devices in a particular country
* geo: you can pass it coordinates
* hostname: find values that match the hostname
* net: search based on an IP or /x CIDR
* os: search based on operating system
* port: find particular ports that are open
* before/after: find results within a timeframe ([only available via API](Shodan-CLI-cheatsheet.md))

## Examples

Apache servers in Paris:

    apache city:"Paris"

Nginx servers in France:

    nginx country:"FR"

Cisco devices on a particular subnet:

    cisco net:"xxx.xxx.xxx.0/24"

Cleartext wifi passwords:

    html:"def_wirelesspassword"

Surveillance cameras with username: admin and password: password

    NETSurveillance uc-httpd

Citrix Gateways:

    title:"citrix gateway"

Info about mongo DB servers:

    "MongoDB Server Information" port:27017 -authentication

FTP servers allowing fully anonymous access:

    "220" "230 Login successful." port:21

Android root bridges with port 5555.

    "Android Debug Bridge" "Device" port:5555
