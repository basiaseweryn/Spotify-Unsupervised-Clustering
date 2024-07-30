# Projekt Klasteryzacja Piosenek Spotify

## Opis Projektu
Projekt koncentruje się na klasteryzacji utworów muzycznych z Spotify na podstawie ich cech charakterystycznych. Celem było zidentyfikowanie grup utworów o podobnych właściwościach oraz analiza tych grup w celu znalezienia podobieństw i różnic między nimi.

## Dane
- **Źródło**: Dane pochodzą z [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023) i zawierają 943 rekordy z 24 cechami.
- **Cechy**: Zbiór danych zawiera:
  - Twarde dane dotyczące twórców i dat wydania.
  - Metryki popularności i obecności na listach przebojów.
  - Parametry muzyczne, takie jak taneczność, energetyczność, akustyczność itp.

## Przygotowanie Danych
1. **Konwersja Typów Danych**: Zmieniono wartości typu object na string lub int64 dla spójności danych.
2. **Uzupełnianie Braków Danych**: Brakujące wartości w niektórych kolumnach zastąpiono zerami lub losowymi wartościami zgodnie z rozkładem kolumny.
3. **Usuwanie Duplikatów**: Usunięto duplikaty rekordów.
4. **Transformacja**: Zastosowano transformację logarytmiczną na skośnych cechach, jednak wycofano ją ze względu na gorsze wyniki klasteryzacji.
5. **Skalowanie**: Znormalizowano dane za pomocą MinMaxScaler.

## Proces Klasteryzacji
- **Wybrane Cechy**: Wybrano konkretne parametry muzyczne (np. bpm, taneczność, energetyczność) do klasteryzacji.
- **Rozważane Modele**: Przeanalizowano KMeans, DBSCAN i Spectral Clustering.
  - **KMeans**: Testowano różne liczby klastrów przy użyciu wielu metryk.
  - **DBSCAN**: Okazał się nieskuteczny, ponieważ większość utworów trafiła do jednego klastra.
  - **Spectral Clustering**: Wybrano do dalszej analizy ze względu na obiecujące początkowe wyniki.

## Wybór Modelu i Ewaluacja
- **Wybrany Model**: Spectral Clustering z 3 klastrami, określonymi za pomocą Silhouette Score, Calinski-Harabasz Index i Davies-Bouldin Index.
- **Wizualizacja**: Zredukowano wymiary danych za pomocą PCA, aby lepiej zobrazować struktury klastrów.

## Analiza Statystyczna
- Przeprowadzono testy ANOVA w celu porównania średnich wartości cech w różnych klastrach.
- Istotne różnice znaleziono w większości cech, z wyjątkiem liveness.

## Analiza Piosenek w Klastrach
- **Charakterystyka Klastrów**:
  - **Klaster 0**: Wysoka energetyczność, taneczność, gatunki pop/hip-hop.
  - **Klaster 1**: Szybkie tempo, mniej pozytywne, gatunki trap/rap/techno.
  - **Klaster 2**: Akustyczne, instrumentalne, gatunki indie/klasyczne.
- **Wpływ Klastra na Zmienne**: Przeanalizowano zależności między klastrami a zmiennymi takimi jak liczba odtworzeń, obecność na playlistach, rok wydania i liczba artystów.

## Autorzy
- [@basiaseweryn](https://github.com/basiaseweryn)
- [@ulaszczesna](https://github.com/ulaszczesna)

README stanowi podsumowanie celów projektu, przetwarzania danych, metodologii i kluczowych wyników. Szczegółowe informacje znajdują się w pełnym raporcie projektu.

