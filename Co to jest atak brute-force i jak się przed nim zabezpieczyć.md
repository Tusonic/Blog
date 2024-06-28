Atak siłowy (ang. brute-force) na formularz logowania to nic innego jak zgadywanie hasła. To częsty problem z jakim borykają się twórcy stron i skryptów logowania. Atak brute-force polega na tym, że atakujący próbuje odkryć hasło poprzez systematyczne sprawdzanie kolejnych możliwych ciągów znaków (liter, liczb i symboli).

Każda strona, która zawiera jakiekolwiek pole do wpisania hasła lub formularz logowania może być celem takiego ataku. Jeżeli strona lub aplikacja nie posiada zabezpieczeń przed atakami brute-force, to złamanie hasła jest matematycznie pewne i moment w, którym dojdzie do włamania przy jego pomocy jest już tylko kwestią czasu.

W świecie aplikacji internetowych znalezienie hasła może zając od kilku dni do kilku a nawet kilkuset lat. Czas jaki jest potrzebny do odgadnięcia hasła zależy od jego długości i czasu odpowiedzi systemu logowania. Aby skrócić ten czas i uczynić proces łamania hasła bardziej efektywnym, haker przed właściwym atakiem siłowym stosuje metodę słownikową lub hybrydową. techniki te wykorzystują fakt, że hasło zawiera naturalne słowa typu Kowalski123 a nie tylko „wymieszany” ciąg liter.

Ryzyka i koszty braku zabezpieczeń przed atakami brute-force
Możliwość włamania się na konto lub ekspozycja danych, które miały być niejawne to jedno ale z perspektywy osoby, która posiada taki formularz na stronie, uciążliwym i realnym problemem jest już sam proces ciągłego testowania haseł. Taki proces obciąża serwer przez co usługa działa wolniej, generuje sztuczny ruch i może zwiększać koszty związane z hostingiem a w skrajnych przypadkach może pogarszać SEO.

Z czym tak naprawdę mamy do czynienia?
Ataki brute-force najczęściej są przeprowadzone przez automatyczne skrypty a narzędzia do przeprowadzania takich ataków są ogólnodostępne. Kiedy wykryjesz atak brute-force nie oznacza to, że jakaś konkretna osoba chce zaszkodzić Twojemu serwisowi, po prostu automatyczne skrypty, które na celownik biorą strony z jakimkolwiek ruchem skanują stronę w poszukiwaniu formularza do ataku i zaczynają działanie.

Atak brute-force, choć jest bardzo łatwy do wykrycia, ciężko całkowicie wyeliminować jego próbę przeprowadzenia na naszej stronie czy aplikacji. Wspomniane narzędzia do ataków brute-force potrafią routować żądania przez serwery pośredniczące. Wówczas każde żądanie wydaje się pochodzić z innego adresu IP i nie można zablokować tych ataków banując konkretne adresy IP. Aby jeszcze bardziej skomplikować sprawę, niektóre narzędzia próbują przy każdej próbie innej nazwy użytkownika i hasła, więc nie można zablokować jednego konta w przypadku nieudanych prób podania hasła.

Jak wykryć atak brute-force?
Atak siłowy jest bardzo łatwy do wykrycia w logach serwera:

wiele błędnych prób logowania z pojedynczego adresu IP,
wiele prób logowania przy użyciu wielu różnych loginów z pojedynczego adresu IP,
wiele prób łamania hasła konkretnego konta z wielu różnych adresów IP,
duże zużycie transferu przez pojedynczy host,
próby wejścia na adresy w formacie: http://user:password@www.example.com/login.htm
Metody radzenia sobie z atakami brute-force
Przyjrzyjmy się metodom jakie często mają zapobiec lub znacznie utrudnić przeprowadzanie ataków brute-force. Każda metoda ma swoje zalety i wady.

Metoda 1: Blokowanie atakowanych kont
Najbardziej oczywistym sposobem blokowania ataków brute-force jest po prostu zablokowanie konkretnych kont po określonej liczbie prób błędnego logowania np. po 5 w określonej jednostce czasu. Blokady kont mogą trwać przez określony czas lub mogą wymagać zmiany hasła bądź kliknięcia w link autoryzujący. Pozostaje jeszcze ręczne odblokowanie konta przez administratora.

Metoda ma wady, między innymi takie, że w przypadku braku zastosowania innych metod skrypt atakujący może zablokować bardzo wiele takich kont. Ciągłe informacje o tym, że konto użytkownika jest blokowane wprowadza zbędny chaos, pogarsza user experience i niepotrzebnie angażuje administratora w wykonywanie dodatkowej pracy.

Wdrożenie takiej blokady może spowodować kolejne problemy. Kiedy metoda zostanie wykryta, atakujący może celowo przeprowadzać ataki DoS aby pogorszyć doświadczenia użytkowników i utrudnić działanie administracji. Przy ciągłym atakowaniu konkretnego konta, będzie ono tak jakby zawsze zablokowane, bo użytkownik zwyczajnie nie zdąży się zalogować swoim poprawnym loginem i hasłem. To prowadzi do kolejnego problemu, w którym blokada jest wyłączona na kontach administratora – bo takie są częściej celem ataku.

Popularność metody brute-force
Mimo, że jest to metoda bardzo popularna, może ona być nieefektywna w wielu scenariuszach. W przypadku „powolnych” ataków, które nie wykorzystują dopuszczalnej liczby błędnych logowań blokada nigdy nie zadziała. Mechanizm zakłada, że atakujący próbuje zhakować konkretne konto dlatego nie blokuje on efektywnie ataków, w których testuje się konkretne hasło na wielu różnych kontach. Nawet jeżeli blokada w końcu zadziała nie mamy pewności, że żądania HTTP przestaną być wysyłane do naszego serwera. Taka blokada nie chroni serwera przed zalewem prób logowania.

Blokada konta jest czasami skuteczna, ale tylko w kontrolowanych środowiskach lub w przypadkach, w których ryzyko jest tak duże, że nawet ciągłe ataki DoS są lepsze niż włamanie do konta. Jednak w większości przypadków blokada konta jest niewystarczająca do powstrzymania ataków siłowych.

Rozważmy na przykład serwis Allegro, w którym kilku licytujących walczy o ten sam przedmiot. Jeśli w takim serwisie działałaby blokada kont, jeden z licytujących może po prostu zablokować konta innych w ostatniej chwili aukcji, uniemożliwiając im składanie kolejnych ofert 🙂

Metoda 2: Znane i nieznane przeglądarki
Zamiast blokowania kont można rozważyć zapamiętywanie urządzeń (a właściwie przeglądarek) za pomocą których użytkownicy dokonują logowania. Mechanizm w uproszczeniu działa tak, że przed przystąpieniem do logowania następuje instalacja pliku cookie. Plik cookie może zawierać ID użytkownika, wygenerowany losowy hash i podpis. Podpis generujemy za pomocą jakiegoś klucza publicznego w połączeniu z wygenerowaną liczbą losową i ID. Plik cookie jest instalowany po kliknięciu w link autoryzujący dane urządzenie / przeglądarkę. Przy logowaniu sprawdza się czy plik istnieje a jeżeli nie to użytkownik może dodać kolejne urządzenie.

Mechanizm taki jest skuteczny i praktycznie uniemożliwia zalogowanie się z nieznanego urządzenia bez dostępu do skrzynki e-mail powiązanej z kontem. Klikanie w link nie jest tak uciążliwe, bo mamy z tym do czynienia przy pierwszym logowaniu z wykorzystaniem danej przeglądarki. Po wyczyszczeniu plików cookie w przeglądarce trzeba będzie dokonać ponownej autoryzacji.

Metoda 3: Opóźnienie mechanizmu logowania
Szansa na skuteczne łamanie hasła metodą brute-force jest tym większa im szybciej działa skrypt weryfikujący poprawność loginu i hasła. Z tego powodu dość prostą sztuczką na utrudnienie ataków brute-force jest… opóźnianie działania skryptów weryfikujących login i hasło. Metoda ta świetnie działa jedynie w środowiskach jednowątkowych.

W świecie aplikacji internetowych i PHP należy zwrócić uwagę na fakt, że żądania HTTP są bezstanowe i wielowątkowe. Do serwera może być wysłanych wiele połączeń, które otrzymają wiele odpowiedzi powiedzmy po 5 sekundach. Aby opóźnianie miało jakikolwiek sens trzeba określić limit jednoczesnych połączeń wykonywanych z tego samego hosta lub zabezpieczyć możliwość wysyłania wielu konkurencyjnych zapytań o weryfikację hasła za pomocą prostego podpisu lub statusów logowania przechowywanych np. w bazie danych.

Piękno tej metody polega na tym, że zabezpieczenie działa transparentnie. Klient usługi nie zauważy tego 5 sekundowego opóźnienia weryfikacji a dla hakera może to być przeszkoda, która spowoduje, że atak brute-force przestaje mieć jakikolwiek sens i szansę na powodzenie.

Metoda 4: Blokowanie adresów IP
Blokowanie adresu IP, z którego pochodzą żądania HTTP kończące się nieudanym logowaniem to najbardziej radykalne rozwiązanie, które znacząco utrudnia przeprowadzenie udanego ataku brute-force. Zaletą tego rozwiązania jest to, że odciąża serwer i blokuje kolejne próby testowania kolejnych haseł.

Metoda ta ma także swoje słabości. Mechanizm taki może zablokować duże grupy użytkowników, blokując serwer proxy używany przez dostawcę usług internetowych lub dużą firmę. Hakerzy próbują obejść nawet takie mechanizmy zabezpieczeń za pomocą otwartych list serwerów proxy i wysyłanych jest wtedy tylko kilka żądań z każdego adresu IP.

Mimo tego jest to moja ulubiona metoda na radzenie sobie z atakami brute-force i wierzę, że w końcu atakującym wyczerpie się pula niezablokowanych adresów IP. Administratorzy, którzy doświadczają dużej liczby ataków decydują się na blokowanie adresów IP. W sieci istnieje wiele list adresów IP, które należy zbanować. Są to adresy hostów, które wyjątkowo często były raportowane we wszelkiego rodzaju bazach danych. W tym projekcie można znaleźć linki do takich list: https://github.com/hslatman/awesome-threat-intelligence

W przypadku kont administratora dobrym rozwiązaniem jest dopuszczenie do logowania z hostów o określonym adresie IP.

Metoda 5: Security through obscurity
Metody security through obscurity mogą zniechęcać hakerów na samym początku projektowania ataku. Jedną z nich może być nieprzewidywalna odpowiedź na logowanie. Polega to na tym, że programujemy aplikację w taki sposób aby ta odpowiadała na próbę zalogowania/błędnego hasła na różne i losowe sposoby. W artykule OWASP na temat ataków brute-force określono tę metodę jako zaskakująco skuteczną. Zazwyczaj jest tak, że wpisanie błędnego hasła zwraca nagłówek 401 a w przypadku poprawnego zwracany jest nagłówek 200. W jednym z artykułów pokazywałem przykład wykorzystania programu Hydra, w którym atak siłowy był w ten sposób konfigurowany. Popularne narzędzia do przeprowadzania ataków brute-force umożliwiają atakującemu ustawienie określonych fraz w celu detekcji nieudanej próby złamania hasła. Np. „Hasło nieprawidłowe” lub „Niepoprawna nazwa użytkownika lub hasło”. Banalnym sposobem na oszukanie takich narzędzi może być wyświetlenie tych fraz jako komentarzy HTML lub jako biały tekst na białym tle.

Niejawny adres URL z formularzem logowania to kolejna metoda na utrudnienie ataków brute-force. Jest to częsta praktyka właścicieli stron internetowych opartych o popularne systemy CMS.

Metoda 6: CAPTCHA
CAPTCHA to całkowicie zautomatyzowany publiczny test Turinga, aby odróżnić komputery od ludzi (ang. Completely Automated Public Turing test to tell Computers and Humans Apart). Jest to skuteczna praktyka utrudnienia ataków brute-force na formularze logowania.

Efektywne rozwiązania CAPTCHA charakteryzuję się tym, że ludzie rozwiązują zadanie szybko w prawie 100% przypadków a komputery zawsze taki test, mówiąc kolokwialnie: oblewają. W praktyce, już nawet bardzo proste „autorskie” testy CAPTCHA. W których trzeba odpowiedzieć na jakieś pytanie lub wykonać prostą operację matematyczną są w stanie odeprzeć automatyczne ataki brute-force. Dla większej pewności i oszczędności czasu zaleca się skorzystać z wielu gotowych rozwiązań jak na przykład: reCAPTCHA, która w większości przypadków działa niewidocznie dla normalnego użytkownika.

Metoda 7: Wymuszanie używania trudnego hasła
Zmuszanie użytkowników do wykorzystania długiego hasła to najprostsza i dość efektywna metoda na uniemożliwienie ataków siłowych. Wymóg aby hasło składało się z co najmniej jednej dużej litery, jednej cyfry, jednego znaku specjalnego i było minimum długie na 8 znaków uniemożliwia odgadnięcie hasła, ponieważ trzeba sprawdzić prawie 100 miliardów kombinacji aby znaleźć to właściwe hasło.

W warunkach internetowych atak brute-force przy takiej polityce ustalania haseł nie ma sensu a w połączeniu z innymi technikami ograniczenia odgadywania hasła, które są wymienione w tym artykule można założyć, że ryzyko niemal nie istnieje.

Metoda 8: Uwierzytelnianie dwuskładnikowe
Zabezpieczenie 2FA zakłada wykorzystanie dodatkowego potwierdzenia tożsamości. Nie jestem zwolennikiem 2FA bo utrudnia sam proces logowania i utrudnia współdzielenie kont do czego użytkownicy powinni mieć prawo. Mechanizm uzależnia sukces zalogowania od innych niepowiązanych usług jak sieć komórkowa czy poczta e-mail. Dużo lepszym rozwiązaniem wydaje się być Metoda 2. z zaufanymi urządzeniami, bo mamy drugą warstwę zabezpieczenia bez obciążania użytkownika dodatkową akcją przy każdym logowaniu. Niemniej, w przypadku logowania można 2FA traktować jako dodatkowe zabezpieczenie.

Podsumowanie
Jak widać jest wiele technik na odpieranie ataków brute-force. Ataki siłowe dzięki swojej prostocie działania są zaskakująco trudne do całkowitego powstrzymania. Dzięki stosowaniu najskuteczniejszych metod zaradczych lub nawet ich kombinacji można znacznie ograniczyć ryzyko złamania hasła w ten sposób.

Warto upewnić się, że użytkownicy i klienci naszych witryn przestrzegają podstawowych zasad dotyczących tzw. silnych haseł. W drugiej kolejności warto banować adresy IP, które wysyłając nadmiarowe zapytania HTTP niepotrzebnie obciążają hosting aplikacji i marnują jego transfer.