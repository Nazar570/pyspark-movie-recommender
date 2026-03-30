# PySpark Big Data Movie Recommender

Zaawansowany system rekomendacji filmów zbudowany w oparciu o przetwarzanie rozproszone (**Apache Spark / PySpark**). Projekt rozwiązuje problem rekomendacji w skali Big Data, wykorzystując architekturę hybrydową oraz zaawansowane techniki inżynierii danych.

---

## Główne założenia i funkcjonalności

Projekt wykracza poza standardowe modelowanie, skupiając się na wyzwaniach związanych z ogromnymi zbiorami danych. Z oryginalnego zbioru MovieLens 25M wyekstrahowano i przetworzono próbkę 6 milionów rekordów, co pozwoliło na optymalizację czasu obliczeń przy jednoczesnym zachowaniu skali Big Data:
* **Przetwarzanie Rozproszone:** Wykorzystanie klastra Spark (RDD/DataFrame) do efektywnego przetwarzania milionów rekordów.
* **Optymalizacja Pamięci:** Zastosowanie *Schema Enforcement* oraz mechanizmów *Caching* w celu drastycznego przyspieszenia obliczeń.
* **Architektura Hybrydowa:**
  * **Collaborative Filtering (ALS):** Główny silnik rekomendacji bazujący na ukrytych cechach.
  * **Content-Based Filtering (TF-IDF):** System rozwiązujący problem "Zimnego Startu" oparty na analizie wektorowej gatunków filmowych.

---

## Wyniki Modelu ALS

Model został przetestowany i wyewaluowany z zachowaniem optymalizacji czasu trenowania (czas treningu: ~17.37s). Osiągnięto następujące wyniki:
* **RMSE (Błąd Średniokwadratowy): 0.8450**
* **MAE (Średni Błąd Absolutny): 0.6607**

Interpretacja: System myli się średnio o zaledwie ~0.66 gwiazdki podczas przewidywania gustu użytkownika.

---

## Wykorzystane Technologie
* **Apache Spark / PySpark** (DataFrames, MLlib)
* **Python 3.10+**
* **Pandas & Plotly** (Wizualizacja danych i EDA)

---

## Struktura Repozytorium
* `main.ipynb` - Główny kod projektu (EDA, Pipeline, Trenowanie modeli).
* `requirements.txt` - Środowisko projektowe.
* Oryginalne pliki z danymi (MovieLens 25M) ważące kilkaset megabajtów zostały zignorowane w pliku `.gitignore` ze względu na limity platformy GitHub (100 MB). Kod w notatniku automatycznie pobiera z nich próbkę 6 milionów interakcji do treningu.

---

## Jak uruchomić projekt lokalnie

1. Sklonuj repozytorium na swój dysk:
   ```bash
   git clone https://github.com/Nazar570/pyspark-movie-recommender.git
   ```
2. Przejdź do folderu z projektem i zainstaluj wymagane zależności:
   ```bash
   cd pyspark-movie-recommender
   pip install -r requirements.txt
   ```
3. Uruchom notatnik `main.ipynb` w środowisku obsługującym notatniki Jupyter (np. PyCharm, VS Code lub klasyczny Jupyter Notebook).
   * **Uwaga:** Nie musisz ręcznie pobierać żadnych plików CSV. Kod w notatniku jest skonfigurowany tak, aby automatycznie pobrać z sieci potrzebny zbiór danych poprzez protokół HTTP, a następnie samodzielnie go przetworzyć.