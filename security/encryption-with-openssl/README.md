## Lab - Create/inspect key pair, encrypt/decrypt and sign/verify using openssl

Generate a 2048-bit RSA private key
```
# openssl genrsa -out private_key.pem 2048
```
Create a public key based on the private key
```
# openssl genrsa -in private_key.pem -outform PEM -pubout -out public_key.pem
```
Encrypt a file using the public key 
```
# openssl rsautl -encrypt -pubin -inkey public_key.pem -in secret.txt -out secret.enc
```
Decrypt a file using private key
```
# openssl rsautl -decrypt -inkey private_key.pem -in secret.enc
```
Create a hash digest of a message in a file
```
# openssl dgst -sha256 -sign private_key.pem -out secret.txt.sha256 secret.txt
```
Verify the hash digest with original file
```
# openssl dgst -sha256 -verify public_key.pem -signature secret.txt.sha256 secret.txt
```
