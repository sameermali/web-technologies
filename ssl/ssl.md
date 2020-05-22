# HTTPS (HTTPS over TLS/SSL)
- [How SSL certificate works ?](https://www.youtube.com/watch?v=33VYnE7Bzpk)

# TLS (transport layer security)/SSL (secure sockets layer)

## TLS/SSL
- SSL and TLS are cryptographic protocols designed to provide communication security over a computer network
- SSL and TLS protocols provide communications security over the internet, and allow client/server applications to communicate in a way that is confidential and reliable. 
- protocols have two layers: a Record Protocol and a Handshake Protocol, and these are layered above a transport protocol such as TCP/IP. 
- both use asymmetric and symmetric cryptography techniques.
- versions
  - SSL 1.0/2.0/3.0
  - TLS 1.0/1.1/1.2

# SSL/TLS handshake
- [overview of SSL or TLS handshake](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10660_.htm)

# client certificate authentication
- [client certificate auth 1](https://techcommunity.microsoft.com/t5/IIS-Support-Blog/Client-Certificate-Authentication-Part-1/ba-p/324623)
- [client certificate auth 2](https://techcommunity.microsoft.com/t5/IIS-Support-Blog/Client-Certificate-Authentication-Part-2/ba-p/324626)
- curl -vk --cert /path/to/cert.pem --key /path/to/key.pem --pass "password" https://foo.com/user

# TLS components
- digital certificates
  - digital certificates protect against impersonation, certifying that a public key belongs to a specified entity. issued by a Certificate Authority.
  - [contains specific information](https://www.ibm.com/support/knowledgecenter/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10540_.htm) as determined by the X.509 standard.
  - types
    - personal/user certificate
    - CA/signer certificate
  - [root and intermediary certificates](https://www.thesslstore.com/blog/root-certificates-intermediate/)
    [certificate chain](https://www.ibm.com/support/knowledgecenter/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10600_.htm)
  - Certificate Authority (CA) is a trusted third party that issues digital certificates to provide you with an assurance that the public key of an entity truly belongs to that entity.
  - [obtaining personal certificate from certificate authroity](https://www.ibm.com/support/knowledgecenter/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10590_.htm)
- [cipherspecs and ciphersuites](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_7.1.0/com.ibm.mq.doc/sy10700_.htm)
  - CipherSpec identifies a combination of encryption algorithm and MAC algorithm.
  - CipherSuite is a suite of cryptographic algorithms used by an SSL or TLS connection. A suite comprises three distinct algorithms:
     - key exchange and authentication algorithm, used during the handshake
     - encryption algorithm, used to encipher the data
     - MAC (Message Authentication Code) algorithm, used to generate the message digest
     - ex: SSL_RSA_WITH_RC4_128_MD5 specifies RSA key exchange and authentication algorith, RC4 encryption algorithm using 128-bit key and MD5 MAC algorithm

## faqs
- types of cryptosystems
  - symmetric cryptosystem
    - uses same key to encrypt and decrypt
    - most widely used symmetric algorithm is AES-128, AES-192, and AES-256.
  - asymmetric cryptosystem
    - uses one key to encrypt and different key to decrypt
    - most popular form of assymetric cryptography is **public key cryptography**
    - popular asymmetric key encryption algorithm includes EIGamal, RSA, DSA, Elliptic curve techniques, **PKCS (public key cryptography standards)**
  - stream cryptosystems
    - encrypts and decrypts single character at a time
  - block cryptosystems  
    - encrypts and decrypts several characters at a time
  - [What are the major differences between cryptography and encryption?](https://www.quora.com/What-are-the-major-differences-of-cryptography-and-encryption)
    [Symmetric vs. Asymmetric Encryption – What are differences?](https://www.ssl2buy.com/wiki/symmetric-vs-asymmetric-encryption-what-are-differences)
- terms
  - cipher (or cypher) is a pair of algorithms that create the encryption and the reversing decryption.
  - key is a secret (ideally known only to the communicants), usually a short string of characters, which is needed to decrypt the ciphertext.
- PKCS PKI
  - Public-Key Cryptography Standards (PKCS) are a set of intervendor standard protocols for making possible secure information exchange on the Internet using a public key infrastructure (PKI).
- truststore vs keystore
  - truststore and keystore are used in context of setting up SSL connection in Java application between client and server.
  - In a SSL handshake the purpose of trustStore is to verify credentials and the purpose of keyStore is to provide credential.
  - truststore 
    - contains CA certificates to trust (certificate authorities like Verisign, Thawte, Geotrust or GoDaddy)
  - keystore
    - contains private keys and certificates with their corresponding public keys.
    - only needed if yor are a server or if the server requires client authentication
  - [JSSE ref guide](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jsse/JSSERefGuide.html#Stores)  
    [truststore and keystore](https://stackoverflow.com/questions/318441/truststore-and-keystore-definitions)  
- [different kinds of files](https://serverfault.com/questions/9708/what-is-a-pem-file-and-how-does-it-differ-from-other-openssl-generated-key-file)
  - [conversion between file types](https://www.cloudera.com/documentation/enterprise/5-10-x/topics/cm_sg_openssl_jks.html)
  
  
  
  
  
  
  
