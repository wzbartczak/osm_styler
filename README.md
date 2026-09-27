# OSM Carto Downloader & Styler

OSM Carto Downloader & Styler jest wtyczką QGIS służącą do pobierania,
wczytywania i nadania stylu zgodnego z OSM Carto dla pobranych danych OpenStreetMap. Wtyczka zastała wytworzona z znaczącym i przytłaczającym wykorzystaniem AI.
Aktualna wersja wtyczki to 0.2
## Najważniejsze funkcje

### 1. Pobieranie danych dla wskazanego obszaru

Użytkownik rysuje prostokąt bezpośrednio na mapie. Wtyczka:

1. wybiera właściwy regionalny plik PBF Geofabrik;
2. pobiera go z możliwością wznowienia przerwanego transferu;
3. sprawdza integralność pliku za pomocą sumy MD5;
4. lokalnie wycina zaznaczony obszar do pliku GeoPackage;
5. automatycznie wczytuje, styluje i centruje dane w QGIS.

Regionalny PBF jest zapisywany w pamięci podręcznej, dlatego przygotowanie
kolejnych obszarów z tego samego regionu nie wymaga ponownego pobierania całego
pliku.

### 2. Wczytywanie danych lokalnych

Wtyczka obsługuje pliki:

- `.osm.pbf`;
- `.pbf`;
- `.osm`;
- `.gpkg`.

Po wskazaniu pliku automatycznie tworzy i porządkuje warstwy punktowe, liniowe,
relacje liniowe oraz poligony.

### 3. Automatyczne stylowanie

Do warstw przypisywany jest styl oparty na OpenStreetMap Carto. Obejmuje on
między innymi:

- drogi i mosty z szerokością zależną od skali;
- koleje, cieki i granice administracyjne;
- szlaki turystyczne wyświetlane nad drogami;
- pokrycie i użytkowanie terenu, budynki oraz wody;
- POI, transport publiczny, adresy i obiekty naturalne;
- lokalne ikony SVG;
- nazwy ulic prowadzone wzdłuż linii;
- widoczność obiektów i rozmiary symboli zależne od powiększenia.

## Organizacja widoku

Wtyczka:

- tworzy jedną grupę warstw dla każdego zbioru;
- zachowuje właściwą kolejność kartograficzną;
- ustawia jasne tło mapy;
- dopasowuje widok do łącznego zasięgu danych;
- centruje mapę na wczytanym obszarze;
- nadaje unikalną nazwę kolejnym grupom tego samego zbioru.

## Obsługa błędów

Wtyczka informuje o problemach z pobieraniem, zapisem, sumą MD5, lokalnym
wycinaniem, brakującymi warstwami, stylami lub ikonami. Pobieranie można
anulować, a pozostawiona część pliku może zostać wykorzystana przy wznowieniu.

## Elementy interfejsu

Wtyczka udostępnia dwie odrębne akcje:

- **Wczytaj lokalny PBF lub OSM ze stylem** — oznaczoną ikoną dokumentu;
- **Pobierz i wystylizuj OSM z prostokąta** — oznaczoną ikoną zaznaczonego
  obszaru i strzałki pobierania.

Obie ikony mają wspólną kolorystykę, ale różne symbole odpowiadające wykonywanej
czynności.

## Wymagania

- QGIS Desktop 3.22–3.99;
- połączenie z Internetem podczas pierwszego pobierania regionu;
- wolne miejsce na regionalny PBF i wynikowy GeoPackage;
- standardowa instalacja GDAL/OGR dostarczana z QGIS.
