# Choosing E2EE messaging

[Infosec goals]:

  * Confidentiality: Only  the  two  participants  of  pair-wise  messaging  or  legitimate group member of group messaging can see the message plaintext.
  * Integrity: If a message is received and successfully validated, then it was indeed sent by the given sender,  i.e., other users cannot plant messages into it and they can not modify it.

## iMessage
Apple first supported an E2EE scheme in iMessage, where a message that is compressed by gzip is encrypted by a sender’s secret key and distributed with a digital signature for the guarantee of the integrity to the recipient. 

The iMessage system is opaque and its inner workings have never been subjected to rigorous cryptanalysis, until in 2016 a team from John Hopkins danced around the lip of the volcano and discovered significant vulnerabilities. The company says it has fixed the issues, but has declined to share the details of the fixes.

## Wire
Wire is an encrypted communications program created by Wire Swiss offering messaging, voice calling, and video calling, all end-to-end encrypted. It is cross-platform, and can be used on multiple devices.

## Signal
Signal is a cross-platform encrypted messaging service developed by the Signal Foundation and Signal Messenger LLC, offering one-to-one and group messages, which can include files, voice notes, images and videos.

Whisper Systems, a startup company co-founded by security researcher Moxie Marlinspike and roboticist Stuart Anderson, created Signal as a successor to two separate apps dedicated to encrypted voice calling (RedPhone) and encrypted texting (TextSecure). Its encryption engine is open source, and all communication is encrypted end-to-end by default. Whisper Systems also produced a firewall and tools for encrypting other forms of data (proprietary enterprise mobile security software only available for Android).

The core of the Signal protocol has been adopted by WhatsApp, Facebook Messenger, and Google. //Ratcheting key update structure// enables advanced security properties such as forward secrecy and post-compromise security. Because Signal is an open-source application and its source code for Android and iOSare available on Github, its security has been studied well by the cryptographic community.

* Using phone numbers as identifiers may also create security risks if and when an attacker takes over a phone number. This can be mitigated by enabling an optional Registration Lock PIN in Signal's privacy settings.
* In February 2017, Signal's developers implemented WebSocket support into the client, making it possible for it to be used without Google Play Services.

Setting up Signal's desktop app requires that I first install Signal on an Android or iOS based smartphone with an Internet connection. Sadly I only have an old phone. Would have to get a newer phone. 

## Line
Line is operated by Line Corporation, a subsidiary of Korean internet search engine company, Naver Corporation, offering a freeware app for instant communications on electronic devices such as smartphones, tablet computers, and personal computers. Line users exchange texts, images, video and audio, and conduct free VoIP conversations and video conferences.

Line is one of the most widely-deployed messaging applications, especially in Japan, Taiwan, Thailand and Indonesia in governmental, banking, payment, shopping, and music service applications. Line uses //Letter Sealing//, for a pairwise secure communication between the end users. Its specification was initially not public, but some reverse engineering resulted in a whitepaper describing the high-level specification. 

It consists of key generation and registration, client-to-client key exchange (using the ECDH protocol), and message encryption phases. There seems to be a lack of forward secrecy and the feasibility of a [replay attack].

Line seems to also conform to censorship requirements by governments:
* In China, Line suppresses content to conform with government censorship. Accounts registered with Chinese phone numbers download a list of banned words that cannot be sent or received through Line.
* In Indonesia Line removes emojis and stickers it believes make reference to homosexuality, for example the emoji of "two men holding hands".

## Telegram
Telegram syncs messages seamlessly across any number of devices and offers users the ability to send messages, photos, videos and files of any type, as well as create groups for up to 200,000 people or channels for broadcasting to unlimited audiences. 

Telegram offers end-to-end encryption. //Secret Chats// can be turned on from the app’s advanced settings, in which case:

* All secret chats are device-specific and are not part of the Telegram cloud, meaning that if your device is safe, your secret chats are safe as well.
* When deleting messages on one side of the conversation, the app on the other side of the secret chat will be ordered to delete them as well.
* Users can order messages, photos, videos and files to self-destruct in a set amount of time after they have been read or opened by a recipient. The message will then disappear from both devices.

Telegram has faced censorship or outright bans in some countries over declining demands to facilitate government access to user data and communications. It was banned in Russia in 2018 after it refused to give the Federal Security Service (FSB) access to its decryption keys. A few months later, Telegram was banned by Iranian government for being used for "secretly encouraging armed uprisings".

And some **potential** problems:

* It does not use the end-to-end encryption by default and when it is not used, insecurely stores all messages, media and * It has rolled its own MTProto encryption scheme. Deploying home-brewed and unproven cryptography **may** render the encryption vulnerable to bugs that potentially undermine its security, due to a lack of scrutiny. Some controversies over its encryption protocol arose. Jacobson wrote a paper. Refutation and a security analysis followed.


