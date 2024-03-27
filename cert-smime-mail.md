## Certyfikat S/MIME


Klucz prywatny jest używany do szyfrowania i podpisywania cyfrowego, jest to klucz, który musi pozostać tajny i tylko Ty jako właściciel powinieneś mieć do niego dostęp.

Klucz publiczny jest zawarty w certyfikacie i jest używany przez inne strony do weryfikacji Twojego podpisu cyfrowego lub do szyfrowania danych w taki sposób, aby tylko Ty mógł je odszyfrować za pomocą swojego klucza prywatnego.

openssl pkcs12 -in certfile.pfx -clcerts -nokeys -out certfile.crt

certfile.pfx - zawiera klucz prywatny, klucz publiczny oraz możliwośc podpisywania cyfrowo wiadomości
certfile.crt - klucz publiczny