Terminy takie jak „Pamięć podręczna” czy „Cache” mogą brzmieć skomplikowanie i odstraszać swoją technicznością. Może się wydawać, że ręczne wdrażanie takich mechanizmów optymalizacyjnych jest zadaniem trudnym i czasochłonnym. Zwłaszcza że na rynku dostępnych jest wiele płatnych wtyczek zapewniających te funkcje dla różnych systemów.

Warto zauważyć, że ceny rozszerzeń cache dla systemów open-source mogą osiągać nawet kilkaset złotych. Dodatkowo, dostawcy usług hostingowych często konkurują ze sobą, polecając wtyczki, które najlepiej współpracują z ich infrastrukturą. Jednak cała ta sytuacja nabiera innej perspektywy, kiedy zrozumiesz, na czym polega prosta pamięć podręczna oparta na systemie plików. Jest ona często stosowana zarówno na stronach internetowych, jak i w sklepach online, i może przynieść znaczące korzyści w zakresie wydajności, nie wymagając przy tym dużych inwestycji.

Zasady działania pamięci podręcznej
Pamięć podręczna, znana także jako Cache, działa poprzez przechowywanie wyników złożonych procesów w miejscu o szybkim dostępie. Taki „złożony mechanizm” to na przykład CMS (System Zarządzania Treścią), który tworzy strony internetowe poprzez liczne zapytania do bazy danych i wykonuje różnorodne funkcje, takie jak obliczenia czy operacje na tekście. Dzięki wykorzystaniu pamięci podręcznej, wszystkie te operacje nie muszą być powtarzane za każdym razem, co znacząco przyspiesza ładowanie się stron i poprawia ogólną wydajność serwisu.

Przykład wykorzystania pamięci podręcznej
Napiszemy algorytm wyszukiwania liczb pierwszych. Wygenerowane wyniki będą symulacją strony internetowej ze złożoną logiką. Napiszemy własny system cache, który spowoduje, że przy kolejnych wizytach serwer nie będzie musiał wykonywać kolejny raz tego samego wysiłku.

Dla przykładu tutaj mamy cache.php – wykonanie tej strony trwa około 3 sekund.

<?php
$t_start = microtime(true);
function pierwsze($n){
   for($i=1;$i<=$n;$i++){
      $l = 0;
      for($j=1;$j<=$i;$j++){
         if($i % $j==0){
            $l++;
         }
      }
      if($l==2){
         echo $i.", ";
      }
   }
}
?>
<h1>Witamy na naszej stronie, oto pierwsze liczby pierwsze:</h1>
<div style="width:100%; height:300px; overflow:auto;">
<?php pierwsze(20000); ?>
</div>
<?php 

$t_koniec = microtime(true);
$t_calkowite = $t_koniec - $t_start;
$t_calkowite_sformatowane = number_format($t_calkowite, 2); 

echo "<h3>Czas: " . $t_calkowite_sformatowane . " sekund</h3>";
?>
Tutaj mamy zmodyfikowany cache2.php – wykonanie niemal natychmiastowe

<?php
$t_start = microtime(true);

$cache_file = "cache.html";
$czas_wygasniecia_cache = 3600; // 1 godzina

// Funkcja do generowania liczb pierwszych
function pierwsze($n){
    for($i = 1; $i <= $n; $i++){
        $l = 0;
        for($j = 1; $j <= $i; $j++){
            if($i % $j == 0){
                $l++;
            }
        }
        if($l == 2){
            echo $i . ", ";
        }
    }
}

// Sprawdzamy, czy cache jest aktualny
if(file_exists($cache_file) && (time() - filemtime($cache_file)) < $czas_wygasniecia_cache) {
    // Cache jest aktualny, więc go wyświetlamy
    echo file_get_contents($cache_file);
} else {

    ob_start(); // Rozpoczynamy buforowanie

    ?>
    <h1>Witamy na naszej stronie, oto pierwsze liczby pierwsze:</h1>
    <div style="width:100%; height:300px; overflow:auto;">
    <?php pierwsze(20000); ?>
    </div>
    <?php

    $content = ob_get_contents(); // Pobieramy zawartość bufora
    ob_end_clean(); // Kończymy buforowanie i czyścimy bufor

    file_put_contents($cache_file, $content); // Zapisujemy zawartość do pliku cache

    echo $content; // Wyświetlamy zawartość
}

$t_koniec = microtime(true);
$t_calkowite = $t_koniec - $t_start;
$t_calkowite_sformatowane = number_format($t_calkowite, 2); 

echo "<h3>Czas: " . $t_calkowite_sformatowane . " sekund</h3>";
?>
Jak łatwo zauważyć, wykorzystanie cache w tym kontekście jest niezwykle korzystne. Dzięki niemu można znacząco zwiększyć wydajność serwisu, jednocześnie redukując obciążenie serwera. W efekcie, strony ładują się szybciej. Przy okazji cały system działa płynniej, co przekłada się na lepsze doświadczenia użytkowników i potencjalnie niższe koszty utrzymania infrastruktury.

Stworzenie prostego systemu cache opartego na plikach statycznych jest zadaniem w zasięgu nawet dla początkujących programistów. Zrozumienie zasad działania pamięci podręcznej stron internetowych jest kluczowe bardzo kluczowe. Posiadanie tej wiedzy pozwala na skuteczne zwiększanie wydajności witryn oraz lepsze zrozumienie ich interakcji z różnorodnymi technologiami.