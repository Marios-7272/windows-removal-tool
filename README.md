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
punkt 6: przez „przetłumaczenie” mam na myśli stworzenie skryptu który będzie się w całości składał z sudo apt install program. Nie wszystko dostępne na Windowsie jest na Linuxie. W takiej sytuacji trzeba będzie wejść w %systemdrive%\Program Files albo Program Files (x86)\cokolwiek-to-ma-być, skopiować wszystkie pliki, zrobić co w naszej mocy i modlić się o to, że WINE lub Proton to odpali.  
