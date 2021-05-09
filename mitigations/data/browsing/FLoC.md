# Federated Learning of Cohorts (FLoC)

Third-party cookies are going extinct now that many browsers block third-party cookies, but that doesn’t mean Google (and others) will respect our privacy. Google started an experiment called FLoC (Federated Learning of Cohorts). It runs in Google’s Chrome browser and tracks a user’s online behaviour.

## How it works

- It runs in Google’s Chrome browser. 
- SimHash is used to create user IDs and assign people to cohorts.
  - FloC assigns the browser history an anonymised ID 
  - The ID is added to a group of other browsers with similar behaviors called a cohort.  
- IDs are recalculated on a weekly basis, providing a new summary of their online behaviour every week.

## Opt out

* This all happens on the local computer, our data wouldn’t get stored on a server, but it lives and runs in the code. No opt-in or opt-out for users as long as one uses Google Chrome. Do not use Google Chrome. 
* If you do have to use Chrome, use [DuckDuckGo's Chrome Extension](https://chrome.google.com/webstore/detail/duckduckgo-privacy-essent/bkdgflcldnnnapblkhphbgpggdiikppg). It disables FLoC tracking within the browser. Whether Google will disable it in the future or the browser will ignore it remains to be seen.


