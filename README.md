# kafka-ssl-p12

Create kafka.p12 file for connect the kafka

We have tls.crt ca.crt tls.key


Concatenate tls.crt and ca.crt into a single file:

```
cat tls.crt ca.crt > bundle.crt
```

Create the .p12 file using the certificate bundle and the private key:

Note: Remember the export password

```
openssl pkcs12 -export -in bundle.crt -inkey tls.key -out kafka.p12 -name kafka-cert
```

Verify the .p12 file (optional):

```
openssl pkcs12 -info -in kafka.p12
```
