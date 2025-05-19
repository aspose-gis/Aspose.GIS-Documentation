---
title: "Aplikacja Konsolowa Generatora Warstw"
type: docs
url: /pl/net/layer-generator-console
weight: 50
---

## Podsumowanie

Ta aplikacja konsolowa została zaprojektowana do generowania obiektów geometrycznych różnych typów i zapisywania ich w wybranym formacie. Umożliwia tworzenie punktów, wielokątów i polilinii, określanie liczby obiektów do wygenerowania oraz wybór formatu wyjściowego dla zapisu.

## Użycie

Składnia polecenia:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumenty:

```
-t, --type: Typ geometrii. Jeden z następujących: Punkt, Wielokąt, Polilinia.

-c, --count: Wymagane. Liczba obiektów do wygenerowania. Na przykład: 15.

-f, --fileName: Wymagane. Nazwa pliku do zapisania. Określ nazwę pliku i rozszerzenie. Na przykład: test.json.

-o, --outputFormat: Format wyjściowy. Zobacz obsługiwane formaty plików tutaj.

--help: Wyświetl informacje pomocnicze dla polecenia.

--version: Wyświetl informacje o wersji aplikacji.
```

Przykład polecenia do utworzenia 15 losowych punktów i zapisania ich do pliku w formacie "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Instalacja i Licencjonowanie

Jeśli chcesz używać aplikacji, musisz pobrać archiwum i je rozpakować. Proszę postępuj zgodnie z poniższym linkiem.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Chociaż Aplikacja Konsolowa Generatora Warstw Aspose.GIS jest bezpłatna, Aspose.GIS .NET jest licencjonowany w zwykły sposób, więc możesz ponownie wykorzystać swoją licencję za pośrednictwem aplikacji lub ocenić aplikację używając Aspose.GIS .NET w trybie próbnym lub poprosić o Tymczasową licencję.

## Podsumowanie

Generator Obiektów Geometrycznych to wygodna aplikacja konsolowa, która pomaga tworzyć próbki geometrii różnych typów i zapisywać je w pożądanym formacie. Jest to przydatne narzędzie do pracy z danymi geoprzestrzennymi i opracowywania systemów geoinformacyjnych.
