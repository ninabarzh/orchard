# HTTPS spoofing

In HTTPS spoofing a forged certificate is sent to the target’s browser after the initial connection request to a secure site is made. It contains a digital thumbprint associated with the compromised application, which the browser verifies according to an existing list of trusted sites and because most browsers support the display of punycode hostnames in their address bar, it allows the adversary to access data entered by the victim before it is passed to the application. The browser shows that the website’s certificate is legitimate and secure, and users will not notice that it is a bogus version of the site they expect to visit.

## Attack

    1 Register a domain name that is similar (using punycode) to the target website (AND)

    2 Register its SSL certificate to make it look legitimate and secure

## Resources

* [Phishing with Unicode Domains](https://www.xudongz.com/blog/2017/idn-phishing/), Xudong Zheng, April 14, 2017
