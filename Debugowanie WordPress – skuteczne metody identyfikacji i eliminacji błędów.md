Debugowanie kodu to tak naprawdę usuwanie błędów. Błędy mogą być syntaktyczne, semantyczne i logiczne. Pierwsze błędy wykrywane są przez interpreter PHP i to te będą tematem dzisiejszego artykułu. Debugowanie kodu to naturalna cześć każdego projektu i nie inaczej jest z projektami WordPress, które są aplikacją PHP.

Opcje debugowania w WordPressie
Plik wp-config.php zawiera podstawowe dane o środowisku i konfiguracje dzięki czemu strona WordPress może w ogóle działać. Nic dziwnego, że to w tym pliku możemy sterować różnymi opcjami, które pozwalają kontrolować reagowanie WordPressa na błędy.

Tryb debugowania WP_DEBUG
WP_DEBUG to stała PHP (stała zmienna globalna), której można użyć do uruchomienia trybu debugowania w całym WordPressie. Domyślnie jest to wartość false i to taka wartość znajduje się na świeżo zainstalowanej stronie WordPress. Wartość true ustawiamy w kopiach deweloperskich i w stagingu.

define ( 'WP_DEBUG', true )
Jeżeli musimy koniecznie ustawić taką wartość na produkcji to tylko tymczasowo aby  naprawić krytyczne błąd lub wtedy kiedy nie dysponujemy aktualnie deweloperską wersją strony.

Logi WP_DEBUG_LOG
WP_DEBUG_LOG jest uzupełnieniem WP_DEBUG, który powoduje, że wszystkie błędy są również zapisywane w pliku dziennika debug.log. Jest to przydatne, jeśli chcesz przejrzeć wszystkie powiadomienia później, chcesz ukryć błędy przed odwiedzającymi bądź chcesz wyświetlić powiadomienia wygenerowane poza ekranem. Wartość domyślna to false, dlatego jeżeli chcemy użyć pliku debug.log to musimy dodać do wp-config.php następującą linię:

define( 'WP_DEBUG_LOG', true );
WP_DEBUG_LOG pozwala zapisać do pliku debug.log ostrzeżenia z natywnej w PHP funkcji error_log() co jest przydatne w przypadku zdarzeń AJAX. Po ustawieniu wartości na true, dziennik jest zapisywany domyślnie w debug.log w katalogu wp-content (lub jego odpowiedniku). Alternatywnie, możemy ustawić własną ścieżkę pliku, aby plik został zapisany w innym miejscu.

define( 'WP_DEBUG_LOG', '/tmp/wp-errors.log' );
Aby funkcja WP_DEBUG_LOG mogła cokolwiek wygenerować w dzienniku debug.log tryb WP_DEBUG musi być włączony.

Tryb debugowania WP_DEBUG_DISPLAY
Stała WP_DEBUG_DISPLAY to kolejne uzupełnienie WP_DEBUG. Za pomocą WP_DEBUG kontrolujemy, czy błędy, ostrzeżenia i inne komunikaty debugowania mają być umieszczane w generowanym przez szablony kodzie HTML czy nie. Wartość domyślna to true, co pokazuje błędy i ostrzeżenia w miarę ich generowania. Miejsce wygenerowania się błędu lub miejsce „ucinania się” poprawnego kodu HTML strony może być wskazówką co jest nie tak z daną wtyczką bądź szablonem. Ustawienie zmiennej WP_DEBUG_DISPLAY na false spowoduje ukrycie wszystkich błędów z front-endu.

define( 'WP_DEBUG_DISPLAY', false );
Oczywiście, WP_DEBUG_DISPLAY ma wpływ na działanie WordPressa tylko wtedy kiedy aktywny jest tryb WP_DEBUG. WP_DEBUG_DISPLAY i WP_DEBUG_LOG można używać niezależnie od siebie.

Debugowanie WordPress oficjalna strona: https://developer.wordpress.org/advanced-administration/debug/debug-wordpress/