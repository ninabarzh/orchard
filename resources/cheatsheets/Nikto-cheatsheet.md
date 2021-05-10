# Nikto cheatsheet

It may be necessary to apt install `libnet-ssleay-perl`. Without SSL/TLS support testing sites over HTTPS is not possible.

To trigger all of the alarms of the IDS:

    $ perl nikto.pl -host [domain]

Otherwise:

* [Github Nikto Wiki](https://github.com/sullo/nikto/wiki)
* [CIRT net](https://cirt.net/)
* [Nikto](https://cirt.net/nikto2)
* [Wikto](https://github.com/sensepost/wikto) (nikto for windows) 
