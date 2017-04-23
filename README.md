# SSL/TLS Reference Guide

## Overview

- https://www.sslshopper.com/what-is-ssl.html

### What is SSL?
SSL stands for Secure Sockets Layer, an encryption technology that was originally created by Netscape in the 1990s. SSL creates an encrypted connection between your web server and your visitors' web browser allowing for private information to be transmitted without the problems of eavesdropping, data tampering, and message forgery.


To enable SSL on a website, you will need to get an SSL Certificate that identifies you and install it on your web server. 


If SSL is properly deployed, the information transmitted between the web browser and the web server (whether it is contact or credit card information), is encrypted and only seen by the organization that owns the website.


### SSL vs. TLS
SSL and TLS generally mean the same thing. TLS 1.0 was created by RFC 2246 in January 1999 as the next version of SSL 3.0.


Most people are familiar with the term SSL so that is usually the term that is used when the system is using the newer TLS protocol.

### Secure Socket Layer (SSL)
- https://gist.github.com/leommoore/da79ce0931a5471304d9

Secure Socket Layer (SSL) is a mechanism to allow information to be securely communicated. Specifically, it is a cryptographic protocol that enables two parties such as a web server and a browser to exchange information securely by encrypting it before sending and decrypting it upon receipt. It is based on the X.509 standards.


Symmetric and Asymmetric Encryption Encrypting and decrypting requires a secret like a password, which is known as a key. There are two types of key, symmetric and asymmetric. If a symmetric key is used it means that the same key is used to encrypt and decrypt the message. Asymmetric keys consist of a private and public key. The message sender encrypts the message using their private (secret) key and the message receiver can decrypt the message using the senders public key.


Asymmetric keys require more processing resources than symmetric keys. The problem is that to communicate using symmetric keys both parties have to have the symmetric keys first and the question is how to transfer the symmetric key securely. SSL resolves this problem by using a asymmetric key to transfer the symmetric key and then use the symmetric key for the rest of the session.

### Connection Flow
A typically flow would be the following:

- The client (web browser) connects to the https website
- The server sends its SSL Certificate (public key) to the client
- The client validates the certificate
- The client generates a random symmetric key and encrypts it using the public key in the Certificate
- The client sends the encrypted symmetric key to the server
- The server uses its private key to decrypt the symmetric key
- The server and client encrypt all further traffic using the symmetric key
- At the end of the session the symmetric key is discarded


## What is a certificate authority (CA)?
A certificate authority is an entity which issues digital certificates to organizations or people after validating them. 


Certification authorities have to keep detailed records of what has been issued and the information used to issue it, and are audited regularly to make sure that they are following defined procedures. Every certification authority provides a Certification Practice Statement (CPS) that defines the procedures that will be used to verify applications. There are many commercial CAs that charge for their services (VeriSign). Institutions and governments may have their own CAs, and there are also free Certificate Authorities.


Every certificate authority has different products, prices, SSL certificate features, and levels of customer satisfaction. Learn more about choosing a certificate provider or read our SSL Certificate reviews to find the best provider to purchase from.

## Root Certificate Store

- https://certsimple.com/blog/control-the-ssl-cas-your-browser-trusts

The browser you're using right now trusts a bunch of certificate authorities. Which bunch of certificate authorities - properly called a 'root certificate store' - is determined by your OS and browser

The major root certificate stores are Apple, Microsoft, Mozilla, and Android. When you visit a website, the website presents a certificate that's signed by another certificate, which is signed by another certificate, until you reach one of the certificates in the store you're using.


Each certificate store has its own requirements for a certificate authority to get added. However they all require certificate authorities to pass WebTrust for Certification Authorities, an audited assurance process for the policies and procedures for verifying identity, issuing certificates, handling keys, and more.


Occasionally CAs violate the WebTrust requirements: the Chinese government (CNNIC) and Symantec both recently issued fake certificates for google.com. In CNNIC's case, they gave their private key to a third party that issued the fake certificate. CNNIC was removed from the Android and Mozilla root stores, but the Microsoft root store - used by Chrome on Windows and Edge on Windows - only revoked the misissued certificates. Symantec's case was less severe: an accidental, but still troubling, misissuance: in this case the root stores kept their certificates and the employees responsible were fired.


## Google's Certificate Transparency project

- https://www.certificate-transparency.org/

Certificate Transparency aims to remedy these certificate-based threats by making the issuance and existence of SSL certificates open to scrutiny by domain owners, CAs, and domain users. Specifically, Certificate Transparency has three main goals:
- Make it impossible (or at least very difficult) for a CA to issue a SSL certificate for a domain without the certificate being visible to the owner of that domain.
- Provide an open auditing and monitoring system that lets any domain owner or CA determine whether certificates have been mistakenly or maliciously issued.
- Protect users (as much as possible) from being duped by certificates that were mistakenly or maliciously issued.

## Wildcard Certificate

A wildcard certificate allows for unlimited subdomains to be protected with a single certificate. For example, you could use a wildcard certificate for the domain name example.com and that cert would also work for mail.example.com, ftp.example.com and any other subdomain. The wildcard refers to the fact that the cert is provisioned for *.example.com.

### Multi-level Wildcard Certificate

Although a few CAs will issue certificates for multi-level subdomains (ex *.*.example.com) no modern browser supports them.

## Subject Alternative Name (SAN) Certificate

- https://support.dnsimple.com/articles/what-is-ssl-san/

The Subject Alternative Name (SAN) is an extension to the X.509 specification that allows to specify additional host names for a single SSL certificate.

### What is a SAN Certificate

In practice, when using the term SAN certificates, we are referring to an SSL certificate that has the ability to cover multiple host names (domains), also called multi-domain SSL certificate.


There is no specific limitation on the host names you can cover by a SAN extension, besides the requirement to be syntactically valid host names (further details are available in the RFC). However, certificate authorities may impose further limitations on number or formats based on internal rules or business decisions.


For example, it’s common practice to disallow arbitrary wildcard names as SAN host names. This means SAN certificates generally support only an enumeration of names.


It’s also quite common to encounter a limit on the number of names per certificate. The common practice is to set a limit of up to 100 names per certificate.


A SAN certificate may also be called a Unified Communication Certificate (or UCC),a multi-domain certificates or an Exchange certificate.


## HTTP Strict-Transport-Security (HSTS)
- https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security
- https://www.owasp.org/index.php/HTTP_Strict_Transport_Security_Cheat_Sheet
- https://www.chromium.org/hsts

If a web site accepts a connection through HTTP and redirects to HTTPS, the user in this case may initially talk to the non-encrypted version of the site before being redirected, if, for example, the user types http://www.foo.com/ or even just foo.com.


This opens up the potential for a man-in-the-middle attack, where the redirect could be exploited to direct a user to a malicious site instead of the secure version of the original page.


The HTTP Strict Transport Security header lets a web site inform the browser that it should never load the site using HTTP and should automatically convert all attempts to access the site using HTTP to HTTPS requests instead.


The first time your site is accessed using HTTPS and it returns the Strict-Transport-Security header, the browser records this information, so that future attempts to load the site using HTTP will automatically use HTTPS instead.


When the expiration time specified by the Strict-Transport-Security header elapses, the next attempt to load the site via HTTP will proceed as normal instead of automatically using HTTPS.

```
Strict-Transport-Security: max-age=<expire-time>
Strict-Transport-Security: max-age=<expire-time>; includeSubDomains
Strict-Transport-Security: max-age=<expire-time>; preload
```

### HSTS Preloading
- https://hstspreload.org/
- https://cs.chromium.org/chromium/src/net/http/transport_security_state_static.json
- https://scotthelme.co.uk/hsts-preloading/

Google maintains an HSTS preload service. By following the guidelines and successfully submitting your domain, browsers will never connect to your domain using an insecure connection. While the service is hosted by Google, all browsers have stated an intent to use (or actually started using) the preload list.


#### Removal
- https://hstspreload.org/#removal

Be aware that inclusion in the preload list cannot easily be undone. Domains can be removed, but it takes months for a change to reach users with a Chrome update and we cannot make guarantees about other browsers. Don't request inclusion unless you're sure that you can support HTTPS for your **entire site and all its subdomains** the long term.

## Online Certificate Status Protocol (OCSP Stapling)
- https://www.digicert.com/enabling-ocsp-stapling.htm
- https://www.digitalocean.com/community/tutorials/how-to-configure-ocsp-stapling-on-apache-and-nginx
- https://scotthelme.co.uk/ocsp-stapling-speeding-up-ssl/

### Certificate Revocation List (CRL) 
ToDo

##


##


## [Reference URLs](./ReferenceURLs)

## [Let's Encrypt](./LetsEncrypt)


## Auxiliar 
- https://cloud-images.ubuntu.com/locator/ec2/
- https://brew.sh/

## ToDo
- Revoking


## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D


## License

[The Unlicense](LICENSE)
