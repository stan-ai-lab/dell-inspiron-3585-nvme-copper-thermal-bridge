# Dell Inspiron 3585 — miedziany mostek termiczny NVMe

Opis odwracalnej, pasywnej modyfikacji rozpraszającej ciepło z dysku NVMe w laptopie Dell Inspiron 3585.

**Status projektu:** udokumentowany eksperyment w rzeczywistych warunkach użytkowania. Wyniki mają charakter obserwacyjny, a nie laboratoryjny.

[English documentation](README.md)

## Cel modyfikacji

Projekt opisuje zastosowanie miedzianej płytki nad fabryczną etykietą dysku NVMe. Płytka tworzy dodatkową drogę rozpraszania ciepła w kierunku dolnej pokrywy laptopa.

Modyfikacja została zaprojektowana jako odwracalna: nie zastosowano kleju, kleju termoprzewodzącego, wiercenia ani trwałych zmian konstrukcyjnych laptopa.

## Sprzęt i materiały

- Laptop: Dell Inspiron 3585
- Dysk SSD: SK hynix BC501, 512 GB (model HFM512GDJTNG-8310A)
- Płytka miedziana: 20 × 65 × 0,5 mm
- Materiał termoprzewodzący: pasta Arctic MX-2

## Konstrukcja

1. Płytka miedziana została umieszczona nad fabryczną etykietą dysku SSD.
2. Na styku etykiety dysku i miedzi zastosowano pastę termoprzewodzącą Arctic MX-2.
3. Druga strona płytki jest dociskana w kierunku dolnej pokrywy laptopa po jej założeniu.
4. Nie zastosowano kleju ani trwałych przeróbek mechanicznych.

Siła docisku i opór cieplny styków nie były mierzone. Rozwiązanie wykorzystuje dopasowanie oryginalnej obudowy laptopa.

## Obserwacje temperatury

### Krótkie testy porównawcze

Krótkie testy porównawcze przed modyfikacją i po niej wskazały około **14°C różnicy na czujniku temperatury NVMe nr 2** na korzyść konfiguracji z mostkiem miedzianym. Były to krótkie obserwacje; dokładne wartości bezwzględne i w pełni ustandaryzowany protokół testowy nie są tutaj dostępne.

Nazewnictwo czujników może różnić się między programami monitorującymi. Nie należy zakładać, że numeracja czujników HWiNFO, SMART i Linux hwmon jest bezpośrednio równoważna.

### Odtwarzanie wideo w praktycznym użytkowaniu

Zarejestrowano również osobne porównanie podczas odtwarzania materiału YouTube/VOD w rozdzielczości 1080p na tym samym zewnętrznym monitorze 28-calowym:

| Konfiguracja | Czas obserwacji | Zarejestrowana maksymalna temperatura SSD |
|---|---:|---:|
| Przed modyfikacją | Osiągnięta w ciągu 15 minut | 69,8°C |
| Po modyfikacji | Ponad 7 godzin ciągłego odtwarzania | 57,9°C |

Różnica między zarejestrowanymi wartościami maksymalnymi wynosi **11,9°C (około 12°C)**.

Obie sesje odbywały się w tym samym pomieszczeniu, w zwykłych warunkach otoczenia, bez celowego dodatkowego chłodzenia ani wymuszonej wentylacji pomieszczenia. Rozdzielczość odtwarzania i monitor zewnętrzny były takie same.

**Ważne ograniczenie:** czasy obserwacji nie były jednakowe. Nie był to test laboratoryjny z identycznym obciążeniem, ustaloną temperaturą początkową i ciągłym, zsynchronizowanym rejestrowaniem danych. Dlatego porównanie należy traktować jako obserwację z praktycznego użytkowania, a nie dowód uniwersalnego obniżenia temperatury przy każdym obciążeniu.

### Dodatkowy monitoring po modyfikacji

W dniach 1–3 listopada 2026 r. zebrano punktowe odczyty czujników Linux hwmon. W dziesięciu zapisanych pomiarach:

- Odczyty NVMe temp1/temp2 mieściły się w zakresie 46,9–52,9°C.
- Odczyty NVMe temp3 mieściły się w zakresie 52,9–58,9°C.
- temp3 był konsekwentnie o około 6°C wyższy od temp1/temp2.

Są to osobne pomiary punktowe, a nie ciągły zapis temperatury z siedmiu godzin. Nie zweryfikowano niezależnie przyporządkowania indeksów czujników Linux hwmon do oznaczeń czujników SMART dysku.

### Stan dysku przed modyfikacją

Raport SMART sprzed modyfikacji, z 31 października 2026 r., wykazał:

- Ogólny stan: PASSED
- Critical Warning: 0
- Percentage Used: 1%
- Media and Data Integrity Errors: 0
- Error Information Log Entries: 0

Jest to punkt odniesienia dotyczący stanu technicznego dysku, a nie dowód skuteczności mostka termicznego. Numer seryjny dysku został celowo pominięty.

## Interpretacja wyników

Obserwacje są zgodne z założeniem, że miedziana płytka działa w tej konkretnej konfiguracji laptopa jako pasywny element rozpraszający ciepło. Najbardziej wymowna obserwacja praktyczna: maksymalna temperatura zarejestrowana podczas dłuższej sesji odtwarzania wideo po modyfikacji była niższa niż temperatura osiągnięta podczas krótszej sesji przed modyfikacją.

Dane nie pozwalają określić dokładnej drogi przepływu ciepła, udziału poszczególnych powierzchni styku ani skuteczności rozwiązania przy każdym obciążeniu i w każdych warunkach otoczenia.

## Bezpieczeństwo i ograniczenia

- Prace przy laptopie należy wykonywać po jego wyłączeniu i odłączeniu zasilania zewnętrznego.
- Należy unikać zwarć i nie dopuścić do kontaktu miedzi z odsłoniętymi elementami elektrycznymi.
- Dolna pokrywa powinna zamykać się normalnie; nie wolno dociskać jej na siłę do dysku ani innych podzespołów.
- Trzeba sprawdzić, czy płytka nie koliduje z akumulatorem, przewodami ani innymi elementami.
- Pasta termoprzewodząca służy jako materiał poprawiający styk cieplny, a nie jako klej konstrukcyjny.
- Autor nie ponosi odpowiedzialności za uszkodzenia powstałe podczas odtwarzania tej modyfikacji.
- W różnych rewizjach laptopa rozmieszczenie elementów może się różnić. Przed próbą należy sprawdzić konkretny egzemplarz.

## Zawartość repozytorium

Dokumentacja fotograficzna projektu jest dostępna w katalogach:

- [Zdjęcia sprzętu i montażu](images/hardware/)
- [Zdjęcia pomiarów temperatury](images/temperature/)
- [Zanonimizowany zrzut terminala z pomiarem](images/results/terminal_pomiar_zanonimizowany.png)

## Autorstwo

Modyfikacja fizyczna, prace sprzętowe i pomiary: właściciel repozytorium.

Repozytorium dokumentuje eksperyment dotyczący jednego egzemplarza urządzenia. Nie jest to oficjalna procedura serwisowa firmy Dell ani gwarantowane ulepszenie.
