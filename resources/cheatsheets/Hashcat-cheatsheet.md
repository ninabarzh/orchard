# Hashcat

[https://hashcat.net/hashcat/](Hashcat) is the self-proclaimed world's fastest password recovery tool and the World's first and only in-kernel rule engine. It had a proprietary code base until 2015, but is now released as free software (MIT License). Versions are available for Linux, OS X, and Windows and can come in CPU-based or GPU-based variants.

There are two main flavours of Hashcat:

* Hashcat (standard CPU-based cracking software)
* oclHashcat (accelerated GPU-based cracking software)

''oclHashcat'' can be orders of magnitude faster to use than standard ''hashcat''. Operationally, they are pretty much the same.

## Installation hashcat on Windows

* Install [hashcatGUI](https://hashkiller.co.uk/hashcat-gui.aspx)
* Download the [hashcat binaries](https://hashcat.net/hashcat/).
* Open hashcatGUI and load the binary.

## Installation hashcat on Linux

* Check version number or download from the [hashcat site](https://hashcat.net/hashcat/).
```
$ wget http://hashcat.net/files/hashcat-x.x.x.xz
```
* Unpack it.
* Go into the unpacked hashcat directory and start de ''.bin'' file with the ''help'' option.

```
$ ./hashcat64.bin --help
```

## Dictionary and hybrid attacks

Get the [CrackStation's Password Cracking Dictionary](https://crackstation.net/buy-crackstation-wordlist-password-cracking-dictionary.htm).

Straight Dictionary Attacks (running a standard wordlist against a set of hashes) will work with most of the common passwords:

    $ ./hashcat64.bin -m 1000 -a 0 hashlist.txt crackstation.txt

To crack passwords that users have chosen to append random characters to, a Hybrid Dictionary + Mask Attack (1 character):

    $ ./hashcat64.bin -m 1000 -a 6 hashlist.txt crackstation.txt ?a

Two characters:

    $ ./hashcat64.bin -m 1000 -a 6 hashlist.txt crackstation.txt ?a?a

The RockYou list is smaller. here was for the sake of time. As you start appending characters to wordlists  With more characters appended, he time it takes to completely cover all possible variations can grow exponentially. The RockYou and Cain wordlists are smaller. Those can be found on the [Skull Security wiki](https://wiki.skullsecurity.org/Passwords). 

    $ ./hashcat64.bin -m 1000 -a 6 hashlist.txt rockyou.txt ?a?a?a

To cover appended years, pin numbers, and special dates:

    $ ./hashcat64.bin -m 1000 -a 6 hashlist.txt crackstation.txt ?a?a

Prepending characters to wordlists:

    $ ./hashcat64.bin -m 1000 -a 7 hashlist.txt ?a rockyou.txt

The combinator attack combines two separate lists. Create a ''combinatorlist.txt'' containing key terms to append to the crackstation list (year, month, company name, whatever makes sense in the context, see [en:hacking:system:tools:pw-analysis:start|password analysis tools)):

    $ ./hashcat64.bin -m 1000 -a 1 hashlist.txt crackstation.txt combinatorlist.txt

## Rule-based attacks

A lot of people use [leetspeak](http://www.robertecker.com/hp/research/leet-converter.php), where an ''O'' is replaced by a ''0'', an ''E'' by ''3'', etc. and a [rule-based attack](https://www.4armed.com/blog/hashcat-rule-based-attack/) may deliver. Existing rules that can be used are the [d3ad0ne.rule](https://github.com/hashcat/hashcat/blob/master/rules/d3ad0ne.rule), [leetspeak rule](https://github.com/hashcat/hashcat/blob/master/rules/leetspeak.rule), [unix-ninja-leetspeak.rule](https://github.com/hashcat/hashcat/blob/master/rules/unix-ninja-leetspeak.rule) and [generated2.rule](https://github.com/hashcat/hashcat/blob/master/rules/generated2.rule). 

    $ ./hashcat64.bin -m 1000 -a 0 hashlist.txt crackstation.txt --rules=rules/generated2.rule

And there are [more existing rules](https://github.com/hashcat/hashcat/tree/master/rules).

## Rainbow Tables

Remove all hashes or passwords that were cracked with the above methods. Run what remains using [rainbow tables](http://project-rainbowcrack.com/). This can take a long time, and depending on system, [faster tables](http://project-rainbowcrack.com/table.htm) can be used.

## Targeted Brute Forcing

One of the most common passwords on the internet is the word ''Ford2008''. Probably also ''Ford2008@''. Take the latter. It exists of an uppercase character ''u'', then 4 lowercase characters, ''l,l,l,l'', 4 digits ''d,d,d,d'' and finally a special character ''s''. Patterns like these can be re-useful for targeted brute forcing:

    $ ./hashcat64.bin -m 1000 -a 3 hashlist.txt -1 ?a -2 ?u?l?d -3 ?l -4 ?d ?1?2?3?3?3?3?3?3?4

    $ ./hashcat64.bin -m 1000 -a 3 hashlist.txt -1 ?a -2 ?u?l?d -3 ?l -4 ?u ?4?2?3?3?3?3?3?2?1

    $ ./hashcat64.bin -m 1000 -a 3 hashlist.txt -1 ?s -2 ?l?d -3 ?l -4 ?u ?4?2?3?3?3?3?3?3?2?1

With the found passwords, one can try for some password analysis, which may reveal more patterns that may be re-useful for targeted brute forcing or creating combinator lists that are focused on the context.
