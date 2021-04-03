# Internal PKI

* Generate the keys in their locations, submit a Certificate Signing Request (CSR) to the key-signing machine or transfer the CSR to the offline CA, the key-signing machine could have processed the request and returned a signed certificate which could have been transferred back to the clients. That way, the secret `.key` files stay on the machine on which they were generated. 
