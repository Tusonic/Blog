
### Generowanie darmowych certyfikatów SSL Lets Encrypt
## Co będziemy potrzebować aby wygenerować darmowy certyfikat SSL?
- Linux – np. Debian 🙂
- WinScp – darmowy klient SFTP
- Aktualizacja repozytorium
- Aktualizowanie repozytorium Linux ma wiele kluczowych korzyści. Wystarczy że wpiszemy:
```
apt-get update
```

```
apt-get upgrade
```
### Aktualizowanie repozytorium Linux ma wiele kluczowych korzyści. Oto kilka powodów, dlaczego warto to robić:

- Zabezpieczenia i poprawki: Aktualizacje repozytorium zawierają poprawki bezpieczeństwa oraz aktualizacje programów. Ignorowanie tych aktualizacji może pozostawić system podatnym na znane luki i ataki.
- Nowe funkcje i ulepszenia: Aktualizacje nie tylko łatają błędy, ale także wprowadzają nowe funkcje i ulepszenia w oprogramowaniu. Dzięki nim możesz cieszyć się lepszą wydajnością, nowymi narzędziami i funkcjonalnościami.
- Stabilność systemu: Aktualizacje pomagają w utrzymaniu stabilności systemu. Usuwają błędy, które mogą powodować awarie lub niestabilność pracy systemu.
- Zgodność z nowymi standardami: W miarę jak technologia ewoluuje, aktualizacje repozytorium pomagają utrzymać system w zgodności z najnowszymi standardami. Dzięki temu można korzystać z nowoczesnych aplikacji i usług.
- Optymalizacja wydajności: Aktualizacje często zawierają optymalizacje, które poprawiają ogólną wydajność systemu, co przekłada się na szybsze działanie aplikacji.
- Wsparcie producenta: Aktualizacje repozytorium są często wynikiem pracy deweloperów i społeczności open-source, co oznacza, że otrzymujesz wsparcie i rozwiązania problemów od szerokiej grupy ekspertów.
- Zgodność z nowymi wersjami oprogramowania: Jeśli planujesz aktualizację lub instalację nowych aplikacji, to często będą one wymagały najnowszych wersji bibliotek i zależności, które można uzyskać tylko poprzez aktualizację repozytorium.

Dlatego warto regularnie aktualizować repozytorium Linux, aby cieszyć się bezpieczeństwem, stabilnością i nowymi funkcjonalnościami, jakie oferuje system operacyjny.

### Pamiętaj! Darmowy certyfikat SSL to nie tylko bezpieczeństwo, to również zaufanie!

## Generowanie certyfikatu SSL Debian 10
Teraz możemy przejść do instalacji cerbot-a który jest niezbędny aby wygenerować nasz darmowy certyfikat SSL. Aby zainstalować cerbot wystarczy wydać polecenie:
```
apt-get install python-certbot-apache
```
Generowanie darmowego certyfikatu SSL zaczynamy od wpisania następującej komendy:
```
certbot certonly --manual --preferred-challenges dns --email admin@naszadomena.pl --domains naszadomena.pl
```
Teraz wystarczy połączyć się przy pomocy WinScp z naszym serwerem aby odczytać darmowe klucze SSL dla domeny Wszystkie klucze znajdują się w katalogu
```
/etc/letsencrypt/live
```
## Generowanie certyfikatu SSL Debian 11

Generowanie certyfikatu na Debian 11 odbywa się bardzo podobnie jak na Debianie 10. Instalacja Cerbota na nowym Debianie wygląda tak:
```
apt -y install certbot
```
Komenda aby wygenerować darmowy certyfikat SSL dla Debian 11 wygląda tak:
```
certbot certonly --manual --preferred-challenges=dns -d domena.pl -m admin@domena.pl
```