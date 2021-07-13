# FloCed sites

[FLoC](../browsing/FLoC.md) requires that a website provide an explicit HTTP response header if it wants to opt out of the program. Google is counting on webmasters to not be bothered with this task.

In order to opt-out a website out of the FLoC network, add a custom HTTP response header to all websites to be served with each request. This comes in the form of a Permissions-Policy header, with the following syntax:

    Permissions-Policy: interest-cohort=()

## nginx

For nginx use the add_header directive (and then reload):

    server {
        location / {
          add_header Permissions-Policy interest-cohort=();
        ...
        }
    }

## OpenLiteSpeed
For the OpenLiteSpeed web server, add the FLoC header by editing `vhost.conf` located in `/usr/local/lsws/conf/vhosts/[some_application]/vhconf.conf`, for example

    context / {
        location                $DOC_ROOT
        allowBrowse             1
        note                    This header disables FLoC
        extraHeaders            set Permissions-Policy interest-cohort=()
    }

and do a graceful restart of OpenLiteSpeed.

## Wordpress
For WordPress there is an open-source plugin, [Disable FLoC](https://wordpress.org/plugins/disable-floc/), that will add the necessary Permissions-Policy headers to the WP. An alternative is the [Really Simple SSL pro plugin](https://really-simple-ssl.com/pro/) for 23 euro that will allow setting more Permission-Policy headers.