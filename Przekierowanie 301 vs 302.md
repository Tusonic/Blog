## Przekierowanie 301 (stałe)
Przekierowanie 301 oznacza, że strona została trwale przeniesiona do nowej lokalizacji. Jest to najczęściej używane przekierowanie, ponieważ informuje wyszukiwarki, że stara strona powinna być usunięta z indeksu, a jej miejsce powinna zająć nowa strona.
```
Redirect 301 /stara-strona.html https://www.nowastrona.pl/nowa-strona.html
```
## Przekierowanie 302 (tymczasowe)
Przekierowanie 302 oznacza, że strona została tymczasowo przeniesiona do nowej lokalizacji. Jest to używane, gdy zmiana jest tylko tymczasowa i w przyszłości strona wróci do pierwotnej lokalizacji.
```
Redirect 302 /stara-strona.html https://www.nowastrona.pl/nowa-strona.html
```
### Podsumowanie
Powyższe przykłady pokazują, jak skonfigurować przekierowania 301 i 302 w pliku .htaccess. Przekierowania 301 są używane do trwałych przeniesień, natomiast 302 do tymczasowych. Pamiętaj, aby dostosować ścieżki i adresy URL do własnych potrzeb.