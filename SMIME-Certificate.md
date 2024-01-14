## SMIME Certificate
openssl pkcs12 -in file.pfx -clcerts -nokeys -out file.crt
openssl x509 -inform pem -in file.crt -outform der -out file cer