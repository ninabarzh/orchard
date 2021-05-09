# Ghost protocols

## A story

This old-fashioned horror anthology isn't terrifying or scream-inducing; instead, it's closer in spirit to the moody, clammy, atmospheric English movies of decades past, and parodies thereof. I am again reminded of Dr. Strangelove.

Beginning of 2018, the European Court of Justice ruled that the UK's Snooper’s Charter is unlawful. In 2018, Australia’s parliament passed legislation that allows intelligence and law enforcement agencies to demand access to encrypted communications data. And the GCHQ now wantsss that preciousss information too. Secure messaging platforms such as WhatsApp and iMessage can be forced to create backdoors or to operate a “ghost protocol” that “CC's” an encrypted message to a third-party when it is sent. A state run Man-in-the-Middle (MitM)?!?

The ghastly ghostly proposal from GCHQ was made late 2018 by its director Ian Levy, and involved “silently adding a law enforcement participant to a group chat or call”, according to the “Principles for a More Informed Exceptional Access Debate” article written by Ian Levy and Crispin Robinson.

A coalition of 47 organisations and individuals wrote to the GCHQ, raising objections to the proposal to insert privileged users in encrypted conversations, in order for the government to spy on such interactions without actually breaking encryption. The GCHQ “ghost protocol” would seriously undermine user security and trust. O Really?!? 

The by the GCHQ proposed ghastly ghost story would require:

* [Service providers](../adversaries/Service-provider.md) to inject a new public key into a conversation, in effect turning a two-way conversation into a group chat where an [E2EE adversary](../adversaries/E2EE-adversary.md) is the [additional participant](../adversaries/Malicious-group-member.md), or add an intelligence participant to an existing group chat.
* [Messaging apps](../../mitigations/data/e2ee/Choosing-E2EE-messaging.md) and service providers to change their software such that it would:
    * Change the encryption schemes used.
    * Mislead users by suppressing the notifications that routinely appear when a new communicant joins a chat.

resources/vulnerabilities/endpoints/E2EE-messaging-applications.md

The ghost story does almost as much damage as calling for backdoors by undermining trust in security altogether. 
