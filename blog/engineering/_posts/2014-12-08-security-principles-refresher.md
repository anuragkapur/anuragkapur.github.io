---
layout: post
title:  "Security Principles Refresher"
date:   2014-12-08 12:00:00 +0000   
categories: highlight engineering
tags: engineering
teaser: Refresher on information security principles for developers
permalink: /blog/security-principles-refresher
img-url: /assets/blog/engineering/security-principles-refresher/spr1.png
---

<iframe allowfullscreen="true" frameborder="0" height="299" mozallowfullscreen="true" src="https://docs.google.com/presentation/d/1kDD1mq6SJOlhz72Hzkyyl3TbliIFlWVVUdOOR7puNic/embed?start=true&amp;loop=true&amp;delayms=5000" webkitallowfullscreen="true" width="480"></iframe>

# Agenda

* This refresher starts with a definition of Information Security along with certain security properties we expect out 
of systems in the context of system security
* Next, we will look at Cryptography and the role it plays in Information Security. We will try and assess which 
security properties different cryptographic algorithm types exhibit.
* This will be followed by a look at Security Protocols that make use of cryptography

![](/assets/blog/engineering/security-principles-refresher/spr1.png)

* The definition of Information Security talks about certain properties we tend to associate with a system in the 
context of security
* Keeping these properties in mind, helps us substantiate what we mean when we make a statement like - “System A is 
secure!”. With these properties, we can be clear and say “secure” because it exhibits all or a subset of the security 
properties
* Next, we take a closer look at what some of these properties mean. Understanding the definition and differences 
between these properties help in evaluating appropriateness of a cryptographic algorithm, given a use-case and also help
in evaluation secure communication protocols.

![](/assets/blog/engineering/security-principles-refresher/spr2.png)

* Confidentiality property ensures that only the designated entities have access to a given set of information
* If an information set S is designated for entities X,Y,Z then only these entities will be able to decipher the 
information
* Worthwhile noting that with this property, the entities can make no additional claims like
    - the information set S has not been tampered with in transition
    - as claimed, the information set was created by X
    - etc

![](/assets/blog/engineering/security-principles-refresher/spr3.png)

* Integrity is the property that ensures that the data has __not been tampered with__ during transmission. An evil entity, 
though unable to read a confidential information set, may introduce additional bits of previously obtained information 
sets or chop off a portion of the information set in transition, such that by the time it reaches the intended entity, 
it’s meaning has been changed.
* Imagine the transmission of a command to transfer £20 from your to someone else’s account, and a hacker replaces 
certain bits of the information sets such that by the time it reaches the bank, the meaning of the command has changed 
from transfer “£20” to transfer “£200”.

![](/assets/blog/engineering/security-principles-refresher/spr4.png)

Think of DOS attacks!

![](/assets/blog/engineering/security-principles-refresher/spr5.png)

* Authenticity is assurance that a message, transaction, or other exchange of information is from the source it claims to be from
* There are no claims made around the confidentiality or secrecy of the information. Only claim made is that it is authentic, i.e. is coming from the source claiming to be its originator.
* A good example is a webpage claiming be the login page for your personal bank account. You need the page to exhibit the authenticity property (in addition to the confidentiality of the data in transmission), that it is owned by your bank.
* Authenticity is closely related to Integrity.

![](/assets/blog/engineering/security-principles-refresher/spr6.png)

* Serves a purpose similar to signatures in our physical world. It is a way to prove that a message from from A such that A cannot repudiate it.

![](/assets/blog/engineering/security-principles-refresher/spr7.png)

* Next, armed with an understanding of what “information security” means, lets look at what Cryptography is and how it can be used to achieve some of the security properties in a system.

![](/assets/blog/engineering/security-principles-refresher/spr8.png)

* A way to start thinking about Cryptography is to think about transformations.
    - Transformation of plain text into cipher text is referred to as __Encryption__.
    - While the transformation of cipher text back into a plain text is referred to as __Decryption__.
* The transformations always use a key and in some cases the same key is used for both encryption and decryption, while in other cases, a different key is used in the two transformations.
* Based on these differences, cryptographic algorithms are categorised as:
    - symmetric key also known as secret key
    - asymmetric key also know as public key
    
![](/assets/blog/engineering/security-principles-refresher/spr9.png)
    
* Also referred to as secret key cryptography.
* The same key is used to both transform the plaintext into ciphertext and vice versa.
* A secret key is established between the entities and only the entities that have the secret key can carry out any of the transformations.
* So which security property can Symmetric Key Cryptography offer?
    
![](/assets/blog/engineering/security-principles-refresher/spr10.png)
    
* Confidentiality? Yes. Only the parties that have the secret key can decipher a given ciphertext.
* Integrity and Authenticity? Yes. Alice can use the secret key to compute what is known as a Message Authentication Code (MAC) for a given plaintext and send that with the plaintext. If Evil tries to tamper with the message, without knowing the secret key, he will not be able to produce a matching MAC and hence when the message reaches Bob, and Bob computes the MAC he will figure the anomaly and will know the message has been tampered.
* Non repudiation? No. Since the key is know to more than one entity, symmetric key crypto does not provice non repudiation
* Integrity vs Authenticity - A message may be authentic (i.e. as claimed, coming from Alice) but may have lost it’s integrity. Alice -> Bob : {“Send money to Charlie, send him £1000”}k . E may chop off some part of the ciphertext resulting in the deciphered message to be “Send money to Charlie, send him £10”
* You receive a message encrypted with a secret key you share with Alice:
    - not only do you trust it has not been seen in transit
    - but also you have reason to trust that it really came from Alice
    - and could not have been changed in transit.      
* Are these statements true?        
    - Alice’s key may have been compromised.
    - Alice may have been tricked into encrypting that message.
    - Alice may not have said it recently — the message may have been delayed, or duplicated.
    - Parts of the message may be missing
    
![](/assets/blog/engineering/security-principles-refresher/spr11.png)
    
* What happens when a client application goes rogue and decides to use k not just for session validation, but also for session creation?
* Man in the middle attack between other client applications and session api are possible
* Greater the number of client apps, greater the number of places where k is stored and hence greater the threat radius
* Takeaway
    - Though symmetric key crypto can provide C, I and A, it may not be the right choice in all use cases.
    - So what is the right choice in these cases? Enter - Asymmetric Cryptography
    
![](/assets/blog/engineering/security-principles-refresher/spr12.png)
    
* Also referred to has public key cryptography.
* These type of crypto algorithms use a key pair.
* One key is kept secret and the other is publicly available.

![](/assets/blog/engineering/security-principles-refresher/spr13.png)

* Confidentiality? Yes - Lets say Alice wants to send a confidential message to Bob. Alice encrypts the message with Bob’s public key. Since only, Bob, the holder of the corresponding private key can decrypt the message Confidentiality is maintainer
* Authenticity and Integrity? Yes - Alice wants to send a message to Bob such that Bob can verify its integrity and authenticity. Alice sign’s is with her private key. Bob decrypts cipher text using Alice’s public key and compares with message. If it matches, he can be sure it was from Alice. Message is from Alice and has not been tampered with in transition.
    - Unlike symmetric key, to add confidentiality along with integrity and authenticity, 2 public private key pairs are needed. More keys! One pair for confidentiality and the other for integrity and authenticity.
* Non Repudiation? Yes: Alice cannot deny that message was sent by her as it is signed with her private key and only she know the private key.
    - Unlike symmetric key crypto, the private key is not shared with anyone, not even with the entity on the other side you want to communicate with. (In symmetric key crypto, secret key is known to atleast 2 entities)

![](/assets/blog/engineering/security-principles-refresher/spr14.png)
    
* Asymmetric key crypto is known to be __performance intensive__ compared to symmetric key crypto. Thus, typically for encryption (i.e. to maintain confidentiality) symmetric key algorithms are used.
    - Example DES, 3DES, AES etc
* Asymmetric key crypto is usually used to sign a message digest, by first hashing the message to a fixed length message digest or to encrypt other symmetric keys
    - Key distribution problem - how to share secret keys among required parties?
        * Use asymmetric to encrypt session / secret keys and distribute
        * Public key used in asymmetric key can be published openly. Authenticity provided by PKI infrastructure, usually Certificate Authorities
                            
![](/assets/blog/engineering/security-principles-refresher/spr15.png)
                            
* Next, lets look at some authentication and data transmission protocols that use cryptography.
* It is important to note, that simply using encryption does not mean a system is secure.

![](/assets/blog/engineering/security-principles-refresher/spr16.png)

* We deal with security protocols all the time as messages are exchanged between communicating entities. Unless we pay close attention to the design of these protocols, the security relevant goals may not be achieved.
    - An example of a security protocol is SSL/TLS, which we all interact with everyday!
* Security protocols are designed to work in a particularly hostile environment, where the network is under the control of some hostile intruder who can:
    - overhear messages
    - intercept messages
    - decrypt or encrypt messages with keys he knows
    - fake messages
* They normally use cryptography to achieve their goals.

![](/assets/blog/engineering/security-principles-refresher/spr17.png)

* What is the obvious vulnerability here?
    - Key is transmitted in plain text!
    
![](/assets/blog/engineering/security-principles-refresher/spr18.png)
    
* This keeps the session key secret from eavesdroppers.
* The fact that the key delivery message is encrypted with k(a, s) tells a that it was created by s.
* Is this enough?

![](/assets/blog/engineering/security-principles-refresher/spr19.png)

* B thinks he shares the key with A, but actually he shares the key with E, the evil user “Eve”.
* This is a failure of both secrecy and authentication.

![](/assets/blog/engineering/security-principles-refresher/spr20.png)

* Here we rectify the vulnerability by using encryption to bind objects together.
* Objective of these quick examples was to show that just using encryption doesn’t mean the transmission is secure. Threat models may still be possible. Hence, when possible, just an established and proven protocol instead of designing your own. When designing your own, be sure to do thorough analysis of possible attack vectors.
* Scyther - open source tool for automated verification of security protocols.
* On the note of using established protocols, lets have a quick look at SSL/TLS before we wrap up.

![](/assets/blog/engineering/security-principles-refresher/spr21.png)

* Here, we are only looking at Server side SSL - where the client can authenticate the server it is talking to. The server does not authenticate.
* Variations of SSL/TLS with mutual authentication are also available, but not as commonly used.
* At a high level, message are as follows:
    - ClientHello: version, random number, session ID, supported cipher suites, compression methods
    - ServerHello: similar
    - ServerCertificate: Certificate containing server’s public key
    - ClientKeyExchange: session key chosen by the client, encrypted with server’s public key from the certificate
    
![](/assets/blog/engineering/security-principles-refresher/spr22.png)    



    
    
    
    
    
        


                            
    
    
    
    
        
        
    
    




 
 
