# Viewing email headers

According to [rfc821](https://tools.ietf.org/html/rfc821), an email client is to send its domain name in the Helo/EHLO command which includes IP address. Email messages may also contain other information that get attached to the header along the way, such as spam ratings that anti-spam software running on your e-mail server may apply to the message and other information added by the server. Email clients use this information to help identify spam messages.

## Thunderbird
To view the header information of an email message in thunderbird, select the message, then click on the //View// menu and select //Headers -> All//. 
* The `Return-path` is allegedly the e-mail address of the sender, although that is not a reliable method for identifying the sender because most adversaries use any return e-mail address that they can find on for the purpose created lists.
* The `Received` line is a bit more reliable, because that contains the IP address of the location from where the message was sent. That is, of course, unless an adversary hacked into an e-mail server or is using a relay server to disguise the true source of the message.

