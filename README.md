# Windows Removal Tool
Click [here](READMEen.md) for english translation.

Witam na stronie Windows Removal Tool! Ta strona to pomysł na program, który ma za zadanie:
- usunąć Windowsa,
- zainstalować Linuxa,
- przenieść dane użytkownika w nienaruszonym stanie,
- zainstalować wszystkie poprzednio zainstalowane programy.
Jest on skierowany dla osób, które chcą rozpocząć swoją przygodę z Linuxem z kółkami treningowymi, albo chcą aby komputer ich babci działał na Linuxie, bo ma 6 lat i szkoda go jeszcze wyrzucać, albo chcą sprankować szkolnego informatyka.

#### Zastrzeżenie
Jestem polskim uczniem liceum. Nie umiem programować, ale używam Linuxa na co dzień. To mój pierwszy projekt w życiu, będę popełniał masę błędów, więc proszę nie oczekiwać, że wszystko będzie poprawne, o łatwości zrozumienia i estetyce nie wspominając.

## Metoda działania:

### Część pierwsza: przygotowanie w Windowsie

#### Plan ogólny:

Pierwsza część to przygotowanie do nadpisania Windowsowa. Sądzę, że powinna ona wyglądać mniej więcej tak:
1. zapytać o uprawnienia administratora,
2. pobrać .iso albo poprosić o wskazanie ścieżki wcześniej pobranego pliku,
3. stworzyć folder %systemdrive%\e (przecież to nie musi koniecznie być C:\),
4. zapytać o nazwy użytkownika i ich hasła oraz o to który jest administratorem,
5. sporządzic listę wszystkich zainstalowanych programów,
6. „przetłumaczyć” ją na coś co zrozumie linux (o tym więcej w szegółach),
7. sporządzić configi poszczególnych użytkowników (ułatwienia dostępu, tapety, kolory, układ ikon na pulpicie (jeśli o w ogóle możliwe), itp.),
8. zapisać to wszystko w %systemdrive%\e\cuś.cfg,
9. zapytać o potwierdzenie,
10. sformatować partycję rozruchową,
11. zmniejszyć rozmiar %systemdrive% o około 20GB,
12. stworzyć uruchamialną partycję, na którą zostanie wypakowany obraz instalatora, przeniesiony skrypt autoinstalacji oraz configi,
13. reboot.

#### Szczegóły i uwagi: 

ogólnie: batch wystarczy ewentualnie coś innego. Nie potrzeba nie wiem jakiego GUI. Użytkownik będzie się musiał zadowolić ramką z myślników i znaków równania.

punkt 2: .iso ma być seryjne, nie musi posiadać żadnych modyfikacji. Skrypt do autoinstalacji będzie sporządzał ten program na podstawie dostarczonego szablonu.

punkt 6: Przez „przetłumaczenie” mam na myśli stworzenie skryptu który będzie się w całości składał z sudo apt install nazwa-programu. Ponadto nie wszystko dostępne na Windowsie jest na Linuxie. W takiej sytuacji trzeba będzie wejść w %systemdrive%\Program Files albo Program Files (x86)\cokolwiek-to-ma-być, skopiować wszystkie pliki, zrobić co w naszej mocy i modlić się o to, że WINE lub Proton to odpali. W ostateczności można chamsko przenieść folder z programem i danymi. 

punkt 8: Trzebaby to rozbić na kilka skryptów. Jeden z nich zawierałby wyłącznie informacje dotyczące instalatora, inne całą resztę. 

punkt 10: Rozważam wykożystanie [trybu MS-DOS autorstwa Endermancha](https://dl.malwarewatch.org/multipurpose/) (Windows10DOS.zip); dzięki temu komputer nie uruchomi Windowsa po reboocie.

punkt 12: Wiem, że Ubuntu tak może. Wiem również, że nie każda dystrybucja tak może.

### Część druga: Instalacja Linuxa

#### Plan ogólny:

1. poczekać, aż skończy się diskcheck,
2. zamontować sformatowaną poprzednio partycję w /boot,
3. stworzyć partycję ext4 zamontowaną w /, na której dane będą zapisywane !od końca!,
4. zainstalować system z wykorzystaniem poprzednio zebranych danych,
5. skopiować odpowiedni skrypt do odpowiedniego folderu,
6. reboot.

Szczegółów i uwag brak.

### Część trzecia: autorskie OOBE

#### Plan ogólny:

1. autoegzekwować skrypt,
2. zamknąć program powitalny dostarczony przez dane distro,
3. stworzyć folder /Dysk Właściwy jako zamiennik %systemdrive%,
4. rekreować całą strukturę folderów,
5. rozpocząć przenoszenie plików,
6. czekać na błąd „za mało miejsca”,
7. zatrzymać kopiowanie,
8. zmniejszyć partycję Windowsa i zwiększyć partycję Linuxa,
9. powrót do punktu 5,
10. sudo apt install nazwa-programu, ale tylko natywne,
11. odczytać konfigurację poszczególnych programów i przenieść ją (w miarę możliwości rzecz jasna),
12. zainstalować WINE, Bottles, czy cokolwiek będzie na czasie i zainstalować odpowiednie programy,
13. usunąć resztki Windowsa i zagospodarować pustą przestrzeń,
14. załadować odpowiednią konfigurację użytkowników, 
15. sudo apt update && sudo apt upgrade && reboot po raz wtóry.

#### Szczegóły i uwagi:

punkt 4: Jest to łatwa idea do zrozumienia, która uniezależnia od NTFS.

punkty 5-10: Zwyczajne skopiowanie wyrzuciłony błąd, że za mało miejsca. 

Mam nadzieję, że to na razie tyle.
