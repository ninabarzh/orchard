# Cipher Suite Cheatsheet

|Cipher|Vulnerabilities|Examples|
| :---------------- | :---------------- | :---------------- |
|RC2 |Offer only a low amount of security. Low strength ciphers are considered to be those with a key length <= 64-bits.|EXP-RC2-CBC-MD5|
|RC4 alias ARC4 or ARCFOUR (for Alleged RC4)| Vulnerable to a number of issues such as the Invariance Weakness (2001), Bar Mitzvah attack (2015) and NOMORE.| ECDHE-RSA-RC4-SHA, ECDHE-ECDSA-RC4-SHA, AECDH-RC4-SHA, ADH-RC4-MD5, ECDH-RSA-RC4-SHA, ECDH-ECDSA-RC4-SHA, PSK-RC4-SHA, KRB5-RC4-SHA, KRB5-RC4-MD5, ECDHE-RSA-RC4-SHA, ECDHE-ECDSA-RC4-SHA, AECDH-RC4-SHA, ADH-RC4-MD5, ECDH-RSA-RC4-SHA, ECDH-ECDSA-RC4-SHA, PSK-RC4-SHA, KRB5-RC4-SHA, KRB5-RC4-MD5, ECDHE-RSA-RC4-SHA, ECDHE-ECDSA-RC4-SHA, AECDH-RC4-SHA, ADH-RC4-MD5, ECDH-RSA-RC4-SHA, ECDH-ECDSA-RC4-SHA, PSK-RC4-SHA, KRB5-RC4-SHA, KRB5-RC4-MD5, ECDHE-RSA-RC4-SHA, ECDHE-ECDSA-RC4-SHA, AECDH-RC4-SHA, ADH-RC4-MD5, ECDH-RSA-RC4-SHA, ECDH-ECDSA-RC4-SHA, PSK-RC4-SHA, KRB5-RC4-SHA, KRB5-RC4-MD5, EXP-RC4-MD5, RC4-64-MD5, RC4-MD5, RC4-SHA |
|DES |a 64-bit block cipher and vulnerable to SWEET32 (CVE-2016-2183). Marked as a “Medium” strength cipher (key length between 56 bits and 112 bits) below the accepatble level. |ECDHE-RSA-DES-CBC3-SHA, ECDHE-ECDSA-DES-CBC3-SHA, EDH-RSA-DES-CBC3-SHA, EDH-DSS-DES-CBC3-SHA, DH-RSA-DES-CBC3-SHA, DH-DSS-DES-CBC3-SHA, AECDH-DES-CBC3-SHA, ADH-DES-CBC3-SHA, ECDH-RSA-DES-CBC3-SHA, ECDH-ECDSA-DES-CBC3-SHA, KRB5-DES-CBC3-SHA, KRB5-DES-CBC3-MD5, ECDHE-RSA-DES-CBC3-SHA, ECDHE-ECDSA-DES-CBC3-SHA, EDH-RSA-DES-CBC3-SHA, EDH-DSS-DES-CBC3-SHA, DH-RSA-DES-CBC3-SHA, DH-DSS-DES-CBC3-SHA, AECDH-DES-CBC3-SHA, ADH-DES-CBC3-SHA, ECDH-RSA-DES-CBC3-SHA, ECDH-ECDSA-DES-CBC3-SHA, KRB5-DES-CBC3-SHA, KRB5-DES-CBC3-MD5, ECDHE-RSA-DES-CBC3-SHA, ECDHE-ECDSA-DES-CBC3-SHA, EDH-RSA-DES-CBC3-SHA, EDH-DSS-DES-CBC3-SHA, DH-RSA-DES-CBC3-SHA, DH-DSS-DES-CBC3-SHA, AECDH-DES-CBC3-SHA, ADH-DES-CBC3-SHA, ECDH-RSA-DES-CBC3-SHA, ECDH-ECDSA-DES-CBC3-SHA, KRB5-DES-CBC3-SHA, KRB5-DES-CBC3-MD5, ECDHE-RSA-DES-CBC3-SHA, ECDHE-ECDSA-DES-CBC3-SHA, EDH-RSA-DES-CBC3-SHA, EDH-DSS-DES-CBC3-SHA, DH-RSA-DES-CBC3-SHA, DH-DSS-DES-CBC3-SHA, AECDH-DES-CBC3-SHA, ADH-DES-CBC3-SHA, ECDH-RSA-DES-CBC3-SHA, ECDH-ECDSA-DES-CBC3-SHA, KRB5-DES-CBC3-SHA, KRB5-DES-CBC3-MD5|
|3DES |A 64-bit block cipher vulnerable to SWEET32|PSK-3DES-EDE-CBC-SHA, PSK-3DES-EDE-CBC-SHA, PSK-3DES-EDE-CBC-SHA, PSK-3DES-EDE-CBC-SHA|
|Null |Informs the browser not to encrypt data, nullifying any protection given through the use of SSL/TLS|ECDHE-RSA-NULL-SHA, ECDHE-ECDSA-NULL-SHA, AECDH-NULL-SHA, ECDH-RSA-NULL-SHA, ECDH-ECDSA-NULL-SHA, NULL-SHA256, NULL-SHA, NULL-MD5, ECDHE-RSA-NULL-SHA, ECDHE-ECDSA-NULL-SHA, AECDH-NULL-SHA, ECDH-RSA-NULL-SHA, ECDH-ECDSA-NULL-SHA, NULL-SHA256, NULL-SHA, NULL-MD5, ECDHE-RSA-NULL-SHA, ECDHE-ECDSA-NULL-SHA, AECDH-NULL-SHA, ECDH-RSA-NULL-SHA, ECDH-ECDSA-NULL-SHA, NULL-SHA256, NULL-SHA, NULL-MD5, ECDHE-RSA-NULL-SHA, ECDHE-ECDSA-NULL-SHA, AECDH-NULL-SHA, ECDH-RSA-NULL-SHA, ECDH-ECDSA-NULL-SHA, NULL-SHA256, NULL-SHA, NULL-MD5, RSA-NULL-SHA256|
