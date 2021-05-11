# Authentication mechanisms

Carefully implement an authentication mechanism to control which users are allowed to access which data. The keyword here is the "carefully", so as to introduce as little new holes in the Emmental cheese as possible.

Authentication provides a way to collect credentials and determine the identity of a user. During authentication with a web application for example, //Web Agents// communicate with a //Policy Server// to determine the proper credentials that must be retrieved from the user who is requesting resources, potentially introducing a larger attack surface. IOW, the strength of the access control model to guard against unauthorised access depends on the robustness of the authentication scheme being used. 
