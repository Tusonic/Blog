# Co to jest Apache, czy warto używać?
W tym artykule chciałbym krótko wytłumaczyć czym jest Apache i dlaczego jego posiadanie jest tak ważne jeżeli prowadzimy stronę internetową – tym bardziej kiedy korzystamy z popularnego systemu zarządzania treścią.

Każdy kto ma za sobą chociaż kilka lekcji Informatyki wie, że na komputerze stacjonarnym musimy mieć zainstalowany system operacyjny. Kiedy mówimy „system operacyjny” i chcemy wskazać konkretną technologię to na myśl od razu przychodzi Windows. Dlaczego? Pewnie dlatego, że jest najpopularniejszy i sami z niego korzystamy lub mieliśmy z nim styczność np. w pracy lub w szkole.

A pakiet biurowy? Pewnie Office. Przecież nawet takie wyrażenia jak „tabelki w Excelu” czy księgowość z Excela” przeszły do mainstreamu. Prace piszemy w Wordzie – tego nawet wymagają uczelnie. A czy znasz jakiś program do obróbki grafiki pewnie PhotoShop. Marka PhotoShop też przeszła do języka potocznego – często jej się używa kiedy w grę wchodzą zbyt dopieszczone fotografie naszych znajomych lub celebrytów 🙂

Pliki pakujemy kultowym WinRarem a popularny CMS? Oczywiście, że WordPress…

Przechodząc do sedna sprawy, takim Windowsem, Excelem, Photoshopem i WordPressem – tyle że w dziedzinie serwerów HTTP jest Apache.

### Co to jest Apache? – definicja
Apache to najpopularniejszy serwer czyli oprogramowanie umożliwiające komputerowi realizować funkcjonalność serwera.

Pojęcie „serwer” ma w potocznym języku kilka znaczeń:

serwer jako maszyna, która realizuje funkcjonalność serwera,
serwer jako oprogramowanie np. tytułowy Apache,
serwer jako usługa hostingowa.
Chcąc być w stu procentach ścisłym, w Informatyce pojęcie „serwer” oznacza element architektury klient-serwer, której zadaniem jest realizacja zleceń klientów.

Apache jest rozwijany przez Apache Software Foundation – zdecentralizowaną organizację non-profit. Logo Apache stanowi napis Apache ze znakiem piórka:

Jeżeli administrowanie serwerem byłoby powszechną umiejętnością Apache kojarzyłby nam się z serwerem tak jak WordPress kojarzy się nam z CMSem który posiada wtyczki, które również wykorzystują do działania Apache. Jest to tak popularne rozwiązanie, że stanowi niemal synonim własnej dziedziny. Jeżeli konfigurowanie serwera byłoby zjawiskiem powszechnym wybieralibyśmy Apache – ponieważ jest to coś w rodzaju standardu. Jego wybór nie będzie błędny, ponieważ takiego wyboru dokonuje większość osób.

### Zalety Apache
- popularność i powszechność – Apache jest obecnie najpopularniejszym serwerem WWW,
- darmowy (open-source) – brak opłaty licencyjnej obniża koszt lub za tę samą cenę hostingu mamy mocniejszy procesor i więcej pamięci,
- bardzo dobra dokumentacja,
- duża społeczność,
- dostępność licznych modułów i oprogramowania – Apache jest rozwijany przez ponad 30 lat,
- elastyczny i konfigurowalny,
- możliwość oddzielnej konfiguracji dla poszczególnych folderów,
- obsługa skryptów PHP, Perl, Lua.

### Wady Apache
- potencjalne problemy ze skalowaniem przy bardzo dużych projektach – każde połączenie uruchamia nowy wątek i w projektach dużej skali korzysta się zazwyczaj z akceleratorów.

Problem skalowalności w 99,9% nas nie będzie dotyczył, no chyba, że chcemy stworzyć serwisy konkurujące z WP.pl lub Allegro…

### Jak zainstalować Apache?
Apache jest domyślnym oprogramowaniem dostawców hostingu na całym świecie. Jeżeli dysponujemy własnym serwerem lub dzierżawimy serwer VPS z systemem Linux, wystarczy komenda:

```
sudo apt install apache2
```

