# TASKS — Treści zadań i punktacja (50 pkt + 3 bonus)

## Zadanie 1 — Struktura i przekierowania (10 pkt)

1. Jednym poleceniem utwórz katalogi: `out/` oraz `work/notes/` (tworząc brakujących rodziców). **(3 pkt)**
2. Zapisz listę plików z katalogu domowego (ukryte + rozmiary czytelne) do `out/ls_home.txt`. **(3 pkt)**  
   **Wymagane:** `ls -lah ~ > out/ls_home.txt`
3. Z pliku `data/logs/system.log` wypisz linie zawierające `ERROR` lub `WARN` (case-insensitive) do `out/warn_err.txt`. **(4 pkt)**  
   **Wskazówka:** `grep -Ei 'error|warn' data/logs/system.log > out/warn_err.txt`


---

## Zadanie 2 — `find`/`xargs` i liczenie linii (10 pkt)

Policz łączną liczbę linii we wszystkich `*.csv` w `data/csv/` (rekurencyjnie), a wynik zapisz do `out/lines_csv.txt`. **(10 pkt)**

- Użyj `find ... -print0 | xargs -0 ...` **lub** pętli: `while IFS= read -r -d '' f; do ...; done`.
- Plik `out/lines_csv.txt` ma zawierać **wyłącznie jedną liczbę**.

---

## Zadanie 3 — Skrypt użytkowy (15 pkt)

**Plik:** `scripts/report.sh`

**Wywołanie:** `bash scripts/report.sh <KATALOG>`

**Wymagania:**
- Gdy `<KATALOG>` nie istnieje — czytelny komunikat na `stderr` i **kod wyjścia ≠ 0**. **(3 pkt)**
- Gdy istnieje:
  1) wypisz aktualną datę/czas w formacie ISO na `stdout`,  
  2) wypisz **TOP-5 największych podkatalogów** (rozmiary „human” + nazwa). **(8 pkt)**
- Cytowanie zmiennych, `du -sh`, `sort -h`, `head -5`. **(4 pkt)**

**Bonus (+3 pkt):** przełącznik `-n` (dry-run) — drukuj, co byś zrobił (oznacz „DRY-RUN”), bez wykonywania operacji „ciężkich”.

---

## Zadanie 4 — Git workflow (15 pkt)

1. Pracuj na gałęzi `kolokwium/<TwojLogin>`. **(3 pkt)**
2. Co najmniej **3 sensowne commity** (np. „zad1: ls + grep”, „zad2: find/xargs”, „zad3: skrypt report”). **(6 pkt)**
3. `git push` i **Pull Request do własnego forka** (nie upstream). **(3 pkt)**
4. W opisie PR dodaj krótką notkę (1–3 zdania): co poszło OK, co sprawiło trudność. **(3 pkt)**

---

## Uwagi końcowe

- Cytuj ścieżki i używaj `--` przed nazwami plików (np. `mv -- "$src" "$dst"`).
- Nie „parsuj `ls`”. Używaj `find`, globów i bezpiecznych pętli.
- Jeśli nie masz `sort -h`, użyj `du -s` (KB) + `sort -n`.
