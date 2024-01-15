## SMIME Certificate
```
openssl pkcs12 -in file.pfx -clcerts -nokeys -out file.crt
```
```
openssl x509 -inform pem -in file.crt -outform der -out file cer
```

#### INFO 

[PL]
- openssl pkcs12 => wywołuje narzędzie OpenSSL do pracy z plikami .pfx (PKCS#12).
- in file.pfx => określa plik wejściowy, którym jest Twój plik .pfx.
- clcerts => wyciąga tylko certyfikaty klienta (bez łańcucha certyfikatów CA).
- nokeys => oznacza, że nie chcesz wyciągać kluczy prywatnych, tylko same certyfikaty.
- out file.crt => określa nazwę pliku wyjściowego dla wyodrębnionego certyfikatu (klucza publicznego).

[EN]
- openssl pkcs12 => calls the OpenSSL tool for working with .pfx files (PKCS#12).
- in file.pfx => specifies the input file, which is your .pfx file.
- clcerts => extracts only client certificates (without the CA certificate chain).
- nokeys => means that you do not want to extract private keys, only certificates.
- out file.crt => specifies the name of the output file for the extracted certificate (public key).

