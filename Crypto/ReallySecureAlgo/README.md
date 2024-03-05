# Cryptography: ReallySecureAlgo
Author: [some1hing](https://github.com/SOME-1HING)
<br>

**Points**: 150
**Hint:** : `man openssl` 😭

**Challenge description:**
```
My good friend, Shamir, sent me these files.
```

#### Attachments:
secret.zip

## Solve
Unzip the secret.zip, and you get a .pem file and flag.enc file.

### What are PEM files:
Privacy Enhanced Mail (PEM) files are a type of Public Key Infrastructure 	(PKI) file used for keys and certificates. PEM, initially invented to make e-mail secure, is now an Internet security standard. HPE Service Manager uses OpenSSL libraries to encrypt and decrypt SOAP messages over HTTP and requires certificates and keys in PEM format. The typical PEM files are:

-   key.pem contains the private encryption key
-   cert.pem contains certificate information

It means PEM files are private keys. and flag.enc seems like a binary file but .enc signifies its encrypted and a private key means asymmetric encryption and possibly RSA.

Since we have the private key, all we have to do is decrypt the encrypted file.
Use a online decryptor or openssl tool.

```bash
openssl pkeyutl -decrypt -inkey challenge.pem -in flag.enc  -out flag.txt
```

You get the flag.txt.

#### Flag:
```plaintext
GLITCH{pResS_X_t0_pAy_ReSpeCt}
```
