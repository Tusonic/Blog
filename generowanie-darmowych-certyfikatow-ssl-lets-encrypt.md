# Generowanie darmowych certyfikatów SSL Lets Encrypt
## Co będziemy potrzebować?
Linux – Debian 10 lub Debian 11
WinScp – darmowy klient FTP
Przed zainstalowaniem niezbędnych pakietów dobrze jest zaktualizować repozytorium naszego systemu Debian 10 do najnowszej wersji. Możesz to zrobić za pomocą następującego polecenia:

`apt-get update`
`apt-get upgrade`
Generowanie certyfikatu SSL Debian 10
Teraz możemy przejść do instalacji cerbota który jest niezbędny aby wygenerować nasz certyfikat. Aby zainstalować cerbot wystarczy wydać polecenie:

`apt-get install python-certbot-apache`
Generowanie darmowego certyfikatu SSL zaczynamy od wpisania następującej komendy:

`certbot certonly --manual --preferred-challenges dns --email admin[at]naszadomena.pl --domains naszadomena.pl`l
Teraz wystarczy połączyć się przy pomocy WinScp z naszym serwerem aby odczytać darmowe klucze SSL dla domeny Wszystkie klucze znajdują się w katalogu `/etc/letsencrypt/live` 


## Generowanie certyfikatu SSL Debian 11
Generowanie certyfikatu na Debian 11 odbywa się bardzo podobnie jak na Debianie 10. Instalacja Cerbota na nowym Debianie wygląda tak:

`apt -y install certbot`
Komenda aby wygenerować certyfikat SSL dla Debian 11 wygląda tak:

`certbot certonly --manual --preferred-challenges=dns -d domena.pl -m admin[at]domena.pl`