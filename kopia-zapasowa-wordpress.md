### Kopia zapasowa WordPress

Kopia zapasowa stanowi fundament bezpiecznej i stabilnej witryny opartej na WordPress. Często poleca się korzystanie z wtyczek, które ułatwiają ten proces, ale istnieje również możliwość stworzenia kopii zapasowej bezpośrednio, używając ręcznych metod. Czyli zrobimy kopię zapasową bez wtyczek! Jest to szczególnie przydatne w przypadku, gdy preferujesz pełną kontrolę nad procesem tworzenia kopii zapasowych oraz gdy chcesz uniknąć dodatkowych rozszerzeń. W tym artykule dowiemy się, jak stworzyć kopię zapasową swojej witryny WordPress krok po kroku, bez wtyczek, aby zadbać o jej bezpieczeństwo i integralność danych.

## Co będziemy potrzebować?
- Dostęp do FTP
- Dostęp do bazy danych
- Notatnik
- Mysqldump.exe
- WinSCP

## Tworzymy plik wsadowy

Nasz pilik backup.cmd będzie służył do tworzenia kopii zapasowej. Najlepiej sobie utworzyć katalog backup np. na dysku C.

Ścieżka do naszego pliku będzie wyglądać następująco.
```
C:\backup\backup.cmd
```

tak przygotowany plik wystarczy teraz edytować w notatnik.

## Tworzymy katalogi WWW oraz SQL

Tworzymy dwa katalogi dla naszej kopi bezpieczeństwa. Katalog WWW, będą tam pliki naszego WordPress oraz katalog SQL w którym będziemy przetrzymywać naszą Bazę Danych.

Dodatkowo jeżeli mamy kilka stron, dobrą praktyką jest stworzenie dodatkowych katalogów z nazwą stron. Najlepiej katalog nazwać tak samo jak adres naszej strony.

Przykładowe ścieżki:
```
C:\backup\tusonic_backup\tusonicdownload\www
C:\backup\tusonic_backup\tusonicdownload\sql
```

## Tworzenie kopii zapasowej bazy danych
Stworzenie kopi zapasowej bazy danych to nic innego jak podanie loginu, hasła oraz adresu serwera, na którym stoi nasza baza.

Na co zwrócić uwagę?

- -h = host – adres serwera 
- -u = user – login do bazy
- -p = password – hasło do bazy + nazwa bazy

Cały wpis powinien wyglądać tak:

```
@C:\backup\mysql\bin\mysqldump.exe -h nasz.serwer.pl –column-statistics=0 -u login -phasło nazwa_bazy > C:\backup\tusonic_backup\tusonicdownload\sql\database_sql.sql
```

## Tworzenie kopii zapasowej plików WordPress
Kopiowanie plików odbywa się przy pomocy protokołu FTP. Aby WinSCP połączył się z serwerem konieczne jest stworzenie pliku tekstowego z konfiguracją.

Tworzymy plik backup.txt – będzie wyglądać to następująco:

```
echo on
open ftp://login:hasło[at]nasz.serwer.pl
get ścieżka/na/serwerze C:\backup\tusonic_backup\tusonicdownload\www
exit
```

Teraz wystarczy, że w naszym skrypcie dopiszemy:

```
@”C:\Program Files (x86)\WinSCP\WinSCP.com” /int=nul /script=backup.txt
```
Zmiana katalogów i zakończenie procedury wykonania kopi zapasowej Dobrą praktyka jest, aby na końcu nasz katalog miał nazwę w postaci daty i godziny. Dzięki takiemu zapisowi unikniemy pomyłek z przywracaniem odpowiedniej kopii zapasowej. Warto trzymać kilka kopii zapasowych jeżeli często coś zmieniamy na stronie.

Aby zautomatyzować nazewnictwo katalogu, warto na koniec skryptu dodać taki wpis. Pozwoli on pobrać aktualna dane i zmienić nazwę katalogu tak, aby miał on format daty i godziny.
```
@set name1=%date:~-4,4%-%date:~-10,2%-%date:~7,2%g%TIME:~0,2%
@cd C:\backup\tusonic_backup\
@rename „tusonicdownload” „%name1%”
Skrypt backup.cmd
```
Oczywiście nic nie stoi na przeszkodzie, aby w skrypcie zaimplementować własne rozwiązania. W ten sam sposób możemy również zbudować skrypt, który wykona nam kopie zapasową klika stron WordPress. Bez wątpienia posiadanie kopii zapasowej jest jedną z ważnych, jak nie najważniejszych rzeczy.

Na koniec przykładowy skrypt do robienia kopii zapasowej strony WordPress bez konieczności instalowania wtyczek.

Kopia zapasowa WordPress – przykład:

#### backup.cmd
```
@set name1=%date:~-4,4%-%date:~-10,2%-%date:~7,2%g%TIME:~0,2%
@echo # TWORZENIE KATALOGU %name1% #
@mkdir C:\backup\tusonic_backup\tusonicdownload\www
@mkdir C:\backup\tusonic_backup\tusonicdownload\sql
@echo # KATALOGU %name1% UTWORZONY #
@C:\backup\mysql\bin\mysqldump.exe -h nasz.serwer.pl –column-statistics=0 -u login -phasło nazwa_bazy > C:\backup\tusonic_backup\tusonicdownload\sql\database_sql.sql
@”C:\Program Files (x86)\WinSCP\WinSCP.com” /int=nul /script=backup.txt
@cd C:\backup\tusonic_backup\
@rename „tusonicdownload” „%name1%”
@pause
```
#### backup.txt
```
echo on open ftp://login:hasło@nasz.serwer.pl get ścieżka/na/serwerze C:\backup\tusonic_backup\tusonicdownload\www exit
```