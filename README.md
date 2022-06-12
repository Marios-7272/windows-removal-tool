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
2. przeskanować dysk w poszukiwaniu danych do przegrania,
3. poprosić o wybór dysku do przegrania oraz oznaczyć go,
4. sprawdzić, czy wystarczy miejsca,
5. pobrać .iso albo poprosić o wskazanie ścieżki wcześniej pobranego pliku,
6. stworzyć folder %systemdrive%\e (przecież to nie musi koniecznie być C:\),
7. zapytać o nazwy użytkownika i ich hasła oraz o to który jest administratorem,
8. sporządzic listę wszystkich zainstalowanych programów,
9. „przetłumaczyć” ją na coś co zrozumie linux (o tym więcej w szegółach),
10. sporządzić configi poszczególnych użytkowników (ułatwienia dostępu, tapety, kolory, układ ikon na pulpicie, itp.),
11. zapisać to wszystko w %systemdrive%\e\cuś.cfg,
12. zapytać o potwierdzenie,
13. zmniejszyć rozmiar %systemdrive% o około 20GB,
14. stworzyć uruchamialną partycję, na którą zostanie wypakowany obraz instalatora, przeniesiony skrypt autoinstalacji oraz configi,
15. sformatować partycję rozruchową,
16. reboot.

#### Szczegóły i uwagi: 

ogólnie: Batch wystarczy, ewentualnie coś prekompilowanego. Nie potrzeba nie wiem jakiego GUI. Użytkownik będzie się musiał zadowolić ramką z myślników i znaków równania. Dobrze byłoby zapakować to i podpisać to jako instalator.

punkt 2: Trzeba wiedzieć ile danych trzeba przegrać. Można do tego dodać 100MB na nasze skrypty.

punkt 5: .iso ma być seryjne, nie musi posiadać żadnych modyfikacji. Skrypt do autoinstalacji będzie sporządzał ten program na podstawie dostarczonego szablonu.

punkt 9: Przez „przetłumaczenie” mam na myśli stworzenie skryptu który będzie się w całości składał z sudo apt install nazwa-programu. Ponadto nie wszystko dostępne na Windowsie jest na Linuxie. W takiej sytuacji trzeba będzie wejść w %systemdrive%\Program Files albo Program Files (x86)\cokolwiek-to-ma-być, skopiować wszystkie pliki, zrobić co w naszej mocy i modlić się o to, że WINE lub Proton to odpali. W ostateczności można chamsko przenieść folder z programem i danymi. 

punkt 11: Trzebaby to rozbić na kilka skryptów. Jeden z nich zawierałby wyłącznie informacje dotyczące instalatora, inne całą resztę. 

punkt 14: Wiem, że Ubuntu tak może. Wiem również, że nie każda dystrybucja tak może.

punkt 15: Rozważam wykożystanie [trybu MS-DOS autorstwa Endermancha](https://dl.malwarewatch.org/multipurpose/) (Windows10DOS.zip); dzięki temu komputer nie uruchomi Windowsa po reboocie.

### Część druga: Instalacja Linuxa i kopiowanie

#### Plan ogólny:

1. poczekać, aż skończy się diskcheck,
2. zamontować sformatowaną poprzednio partycję w /boot,
3. skopiować dane na wcześniej wybrany dysk,
4. usunąć partycję Windowsa,
5. stworzyć partycję ext4 zamontowaną w /,
6. zainstalować system z wykorzystaniem poprzednio zebranych danych,
7. stworzyć folder /Dysk Właściwy jako zamiennik %systemdrive%,
8. skopiować dane,
9. reboot.

#### Szczegóły i uwagi:

punkty 3, 8: Kopiowanie z poziomu instalatora zmniejszy obciążenie dysku. Instalator Linuxa obciąży dysk mniej niż Windows (jeśli w ogóle). To przyspieszy najbardziej czasochłonny proces. 

punkt 7: Jest to łatwa idea do zrozumienia, która uniezależnia od NTFS.

### Część trzecia: autorskie OOBE

#### Plan ogólny:

1. autoegzekwować skrypt,
2. zamknąć program powitalny dostarczony przez dane distro,
3. sudo apt install nazwa-programu, ale tylko natywne,
4. odczytać konfigurację poszczególnych programów i przenieść ją (w miarę możliwości rzecz jasna),
5. zainstalować WINE, Bottles, czy cokolwiek będzie na czasie i zainstalować odpowiednie programy,
6. przetłumaczyć .lnk na .desktop,
7. załadować odpowiednią konfigurację użytkowników, 
8. sudo apt update && sudo apt upgrade && reboot po raz wtóry.

#### Szczegóły i uwagi:

Póki co brak.

Mam nadzieję, że to na razie tyle.
