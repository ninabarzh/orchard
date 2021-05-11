# Authentication mechanisms

Carefully implement an authentication mechanism to control which users are allowed to access which data. The keyword here is the "carefully", so as to introduce as little new holes in the Emmental cheese as possible.

Authentication provides a way to collect credentials and determine the identity of a user. During authentication with a web application for example, //Web Agents// communicate with a //Policy Server// to determine the proper credentials that must be retrieved from the user who is requesting resources, potentially introducing a larger attack surface. IOW, the strength of the access control model to guard against unauthorised access depends on the robustness of the authentication scheme being used. 

* Always do the authentication process in a https session. 
* Make the token pseudo-random enough to make it computationally expensive for an attacker to guess. 
* Hash or encrypt it.
* For highly sensitive operations, add a user interaction based protection (re-authentication or a one-time token) along with token based mitigation.