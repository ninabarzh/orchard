# Plaintext leaks

Users might disclose plaintext of messages, for example by composing them inside web applications, or by composing messages on a compromised device.

* People regularly compose drafts of a message in a webmail application.
* E-mail message replies contain quoted contents of the original message. The reply message can be encrypted to a different set of keys (including the key an adversary has control of), or might not even be encrypted at all.
* Plaintext of messages can be leaked via the OS clipboard of a compromised device.
* An adversary may use social engineering to entice a user to paste into a textarea (“Press CTRL, and press V”) and browser extensions that have clipboardRead permission can read any plaintext messages copy/pasted to or from that compose window. Extensions can also take a screenshot of the current tab in any browser window, thereby leaking the message plaintext.
* When encrypting files, the plaintext version of the file is stored on the filesystem.

## Mitigation

* Mitigations for compromised devices and goofs by users are outside the scope of this threat model. That said, yet another workshop/individual mentoring might raise awareness of some of these threats and their mitigations.

