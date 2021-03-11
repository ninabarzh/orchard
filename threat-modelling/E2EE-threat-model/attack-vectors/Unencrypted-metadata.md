# Unencrypted metadata

When communicating, metadata is always involved, if only because devices, routers and bridges need to know how they have to handle data packets. Things like sender, receiver, protocol used, headers … if all would be encrypted then a device would not be able to get to a local modem, let alone the internet. That said, some protocols generate more metadata than others and some protocols encrypt some of the metadata while other protocols do it in cleartext.

And using end-to-end encryption does not prevent messaging services from collecting personal metadata, while some services store most such personal data on servers in cleartext:

* Service-related, diagnostic, and performance information: activity, log files, and diagnostic, crash, website, and performance logs and reports.
* Device-specific information when installing, accessing, or using a service: the model of a phone, its operating system, and information from its browser, IP address, and mobile network — including phone numbers.

And what can not be collected from a particular phone directly, can be inferred from friends’ activity data.

