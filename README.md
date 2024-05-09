# related-certs-ca

This README describes the steps necessary to generate the CA key material and self-signed certificates from the rootca config file using OQS-openssl.

## RSA

### Generate private key and self-signed root certificate

```
apps/openssl req -x509 -new -newkey rsa:4096 -keyout rsa4096_root.priv -out rsa4096_root.crt -nodes -days 3650 -config ./rootca.cnf
```

### Derive public key from private key

```
apps/openssl pkey -in rsa4096_root.priv -pubout -out rsa4096_root.pub
```

## EC secp521r1

### Generate private key and self-signed root certificate

```
apps/openssl req -x509 -new -newkey ec:<(oqs ecparam -name secp521r1) -keyout secp521r1_root.priv -out secp521r1_root.crt -nodes -days 3650 -config ./rootca.cnf
```

### Derive public key from private key

```
apps/openssl pkey -in secp521r1_root.priv -pubout -out secp521r1_root.pub
```

## dilithium lvl 5

### Generate private key and self-signed root certificate

```
apps/openssl req -x509 -new -newkey dilithium5 -keyout dilithium5_root.priv -out dilithium5_root.crt -nodes -days 3650 -config ./rootca.cnf
```

### Derive public key from private key

```
apps/openssl pkey -in dilithium5_root.priv -pubout -out dilithium5_root.pub
```



