# Windows Removal Tool
Click [here](READMEen.md) for english translation.

Witam na stronie Windows Removal Tool! Ta strona to pomysł na program, który ma za zadanie:
- usunąć Windowsa
- zainstalować Linuxa
- przenieść dane użytkownika w nienarusszonym porządku,
- zainstalować wszystkie poprzednio zainstalowane programy
Ten program jest skierowany dla osób, które chcą rozpocząć swoją przygodę z Linuxem z kółkami treningowymi, albo chcą aby komputer ich babci działał na Linuxie, bo ma 6 lat i szkoda go jeszcze wyrzucać, albo chcą sprankować szkolnego informatyka.

#### Zastrzeżenie
Jestem polskim uczniem liceum. Nie umiem programować, ale używam Linuxa na co dzień. To mój pierwszy projekt w życiu, będę popełniał masę błędów, więc proszę nie oczekiwać, że wszystko będzie poprawne, o łatwości zrozumienia i estetyce nie wspominając.

## Metoda działania:

### Część pierwsza: przygotowanie w Windowsie

#### Plan ogólny:

Pierwsza część to przygotowanie do nadpisania Windowsowa. Sądzę, że powinna ona wykonywać następujące czynności:
1. zapytać o uprawnienia administratora,
2. pobrać .iso albo poprosić o wskazanie ścieżki wcześniej pobranego pliku,
3. stworzyć folder %systemdrive%\e (przecież to nie musi koniecznie być C:\),
4. zapytać o nazwy użytkownika i ich hasła oraz o to który jest administratorem,
5. sporządzic listę wszystkich zainstalowanych programów,
6. „przetłumaczyć” ją na coś co zrozumie linux (o tym więcej w szegółach),
7. sporządzić configi poszczególnych użytkowników (ułatwienia dostępu, tapety, kolory, układ ikon na pulpicie (jeśli o w ogóle możliwe), itp.)
8. zapisać to wszystko w %systemdrive%/e/cuś.cfg
9. zapytać o potwierdzenie,
10. sformatować partycję z plikami rozruchowymi,
11. zmniejszyć rozmiar %systemdrive% o około 20GB,
12. stworzyć uruchamialną partycję, na którą zostanie wypakowany obraz instalatora, przeniesiony skrypt autoinstalacji oraz configi,
13. reboot

#### Szczegóły i wątpliwości: 
ogólnie: .bat wystarczy, nie potrzeba nie wiem jakiego GUI. Użytkownik będzie się musiał zadowolić ramką z myślników i znaków równania.

punkt 2: .iso ma być seryjne, nie musi posiadać żadnych modyfikacji. Skrypt do autoinstalacji będzie sporządzał ten program na podstawie dostarczonego przez nas szablonu.

punkt 6: Przez „przetłumaczenie” mam na myśli stworzenie skryptu który będzie się w całości składał z sudo apt install nazwa-programu. Ponadto nie wszystko dostępne na Windowsie jest na Linuxie. W takiej sytuacji trzeba będzie wejść w %systemdrive%\Program Files albo Program Files (x86)\cokolwiek-to-ma-być, skopiować wszystkie pliki, zrobić co w naszej mocy i modlić się o to, że WINE lub Proton to odpali.  

punkt 8: Trzebaby to rozbić na dwa skrypty. Jeden z nich zawierałby wyłącznie informacje dotyczące instalatora, drugi całą resztę. 

punkt 10: Rozważam wykożystanie [trybu MS-DOS autorstwa Endermancha](https://dl.malwarewatch.org/multipurpose/) (Windows10DOS.zip)

punkt 12: Wiem, że Ubuntu tak może. Wiem również, że nie każda dystrybucja tak może.

### Część druga: Instalacja Linuxa

#### Plan ogólny:

1. poczekanie, aż skończy się diskcheck,
2. zamontowanie sformatowanej poprzednio partycji w /boot,
3. stworzenie partycji ext4 zamontowanej w /, na której dane będą zapisywane !od końca!,
4. zainstalowanie systemu z wykorzystaniem poprzednio zebranych danych,
5. skopiowanie odpowiedniego skryptu do odpowiedniego folderu,
6. reboot po raz wtóry

Szczegółów i uwag brak.

### Część trzecia: autorskie OOBE

#### Plan ogólny:

1. uruchomienie i zalogowanie się użytkownika,
2. autoegzekucja skryptu,
3. zamknięcie programu powitalnego dostarczonego przez dane distro,
4. stworzenie folderu /Dysk Właściwy jako zamiennika %systemdrive%,
5. rekreacja całej struktury folderów
6. rozpoczęcie przenoszenia plików,
7. czekanie na błąd: za mało miejsca,
8. zatrzymanie kopiowania,
9. zmniejszenie partycji Windowsa i zwiększenie partycji Linuxa,
10. powrót do punktu 5,
11. sudo apt install nazwa-programu, ale tylko natywne,
12. odczyt konfiguracji poszczególnych programów i ich przeniesienie (w miarę możliwości rzecz jasna),
13. instalacja WINE, Bottles, czy cokolwiek będzie na czasie i instalacja odpowiednich programów
14. usunięcie resztek Windowsa i zagospodarowanie pustej przestrzeni
15. załadowanie odpowiedniej konfiguracji użytkowników
16. sudo apt update && sudo apt upgrade && reboot

#### Szczegóły i uwagi:

punkt 4: Jest to łatwa idea do zrozumienia. 
punkty 5-10: Zwyczajne skopiowanie wyrzuciłony błąd, że za mało miejsca. 

Mam nadzieję, że to na razie tyle.
