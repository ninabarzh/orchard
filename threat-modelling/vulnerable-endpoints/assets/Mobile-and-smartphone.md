# Mobile and smartphone

The time of a call, who is called, how long the call lasted and which cell tower the phone contacted are all logged traditionally, for billing purposes. That information is metadata, and it can be used to track individuals, and when associated with publicly available content like twitter posts and images taken and uploaded to Flickr for example, can also be used to build a [behavioural profile](../../DA-threat-model/assistive-technologies/Behavioural-analysis.md).

With mobile applications, companies don’t have access to traditional browser cookies to track you over time. Instead, third party advertising and analytics companies use device identifiers — such as Apple iOS’s Identifiers for Advertisers (IDFA) and Google Android’s Advertising ID — to monitor the different applications used on a specific device.
 
## Mitigations

### Individuals

* Do not automatically connect and turn off WiFi on your phone when you don’t need it.
* Take your Bluetooth settings out of “discoverable” mode.
* Create pouches made of conductive fabric for your phone. These act as a Faraday cage and block all incoming and outgoing signals.
* Regularly reset the identifiers in the device - This is similar to deleting cookies in a browser. The device will be harder to associate with past activity, but tracking can start anew using a new advertising identifier.
    * For iOS: Settings > Privacy > Advertising > Reset Advertising Identifier.
    * For Android: Google settings > Ads > Reset advertising ID.

