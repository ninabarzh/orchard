Third-party cookies are going extinct now that many browsers block third-party cookies, but that doesn’t mean Google (and others) will respect our privacy. Google started an experiment called FLoC (Federated Learning of Cohorts). It runs in Google’s Chrome browser and tracks a user’s online behaviour.

## How it works

- It runs in Google’s Chrome browser. 
- SimHash is used to create user IDs and assign people to cohorts.
  - FloC assigns the browser history an anonymised ID 
  - The ID is added to a group of other browsers with similar behaviors called a cohort.  
- IDs are recalculated on a weekly basis, providing a new summary of their online behaviour every week.

## Opt out

### Users

* This all happens on the local computer, our data wouldn’t get stored on a server, but it lives and runs in the code. No opt-in or opt-out for users as long as one uses Google Chrome. Do not use Google Chrome. 
* If you do have to use Chrome, use [DuckDuckGo's Chrome Extension](https://chrome.google.com/webstore/detail/duckduckgo-privacy-essent/bkdgflcldnnnapblkhphbgpggdiikppg). It disables FLoC tracking within the browser. Whether Google will disable it in the future or the browser will ignore it remains to be seen.

### Webmasters and web server administrators 

FLoC requires that a website provide an explicit HTTP response header if it wants to opt out of the program. Google is counting on webmasters to not be bothered with this task.

In order to opt-out a website out of the FLoC network, add a custom HTTP response header to all websites to be served with each request. This comes in the form of a Permissions-Policy header, with the following syntax:

    Permissions-Policy: interest-cohort=()

#### nginx

For nginx use the add_header directive (and then reload):

    server {
        location / {
          add_header Permissions-Policy interest-cohort=();
        ...
        }
    }

#### OpenLiteSpeed
For the OpenLiteSpeed web server, add the FLoC header by editing `vhost.conf` located in `/usr/local/lsws/conf/vhosts/[some_application]/vhconf.conf`, for example

    context / {
        location                $DOC_ROOT
        allowBrowse             1
        note                    This header disables FLoC
        extraHeaders            set Permissions-Policy interest-cohort=()
    }

and do a graceful restart of OpenLiteSpeed.

#### Wordpress
For WordPress there is an open-source plugin, [Disable FLoC](https://wordpress.org/plugins/disable-floc/), that will add the necessary Permissions-Policy headers to the WP. An alternative is the [Really Simple SSL pro plugin](https://really-simple-ssl.com/pro/) for 23 euro that will allow setting more Permission-Policy headers.


