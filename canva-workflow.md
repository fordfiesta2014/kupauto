# Canva Workflow — @motoedukacja

> Pełna dokumentacja techniczna do tworzenia slajdów w Canva przez Claude.
> Czytaj ten plik przed każdą sesją pracy z Canva MCP.

---

## Stworzone posty (historia)

### Post 1 — Fakt: Elektryki vs Benzynowe
- **Temat:** Auto elektryczne ~20 ruchomych części, benzynowe ~2000
- **Typ:** Fakt Dnia / Karuzela
- **Status:** ✅ Gotowy, 3-zone layout zastosowany

### Post 2 — Edukacja: Turbosprężarka
- **Temat:** Jak działa turbosprężarka i czym różni się od kompresora
- **Typ:** Karuzela Edukacyjna
- **Status:** ✅ Gotowy, 3-zone layout zastosowany

### Post 3 — Mit: Ocieplanie silnika zimą
- **Temat:** MIT: Trzeba ocieplać silnik zimą przed ruszeniem
- **Typ:** Mit vs Prawda
- **Status:** ✅ Gotowy, 3-zone layout zastosowany
- **Slajdy content:** DAHLP-l82Jc, DAHLPy-gTIg, DAHLPxkzKSk

### Post 4 — Historia: Lamborghini vs Ferrari
- **Temat:** Lamborghini — jak kłótnia z Ferrari zrodziła legendę (1963)
- **Typ:** Historia / Timeline
- **Status:** ✅ Gotowy, 3-zone layout zastosowany
- **Slajdy content:** DAHLP3PORvY, DAHLPwGLpdI, DAHLP05zvms, DAHLP9jDbcg

### Post 5 — News: Normy Euro 7
- **Temat:** Normy Euro 7 — od listopada 2026 dla nowych homologacji
- **Typ:** News Tygodnia
- **Status:** ✅ Gotowy, 3-zone layout zastosowany
- **Slajdy content:** DAHLPw-bUa0, DAHLP_cXQlo, DAHLPxDJtgE, DAHLP_yvmXU

---

## Szablon Cover Slajdu (Slajd 1)

**Canva Design ID:** `DAHLPg874ao`
**URL:** canva.com/d/iRZkcODgtb1kqmT

**Zasada:** Przed każdym nowym postem → **skopiuj** ten design (nie edytuj oryginału).
Użyj `mcp__28b4b0bd__copy-design` lub ręcznie w Canva.

**Styl cover slajdu (full-bleed):**
- Zdjęcie auta pokrywa cały slajd 1080×1080
- TAG nad tytułem: `◆ FAKT` / `◆ MIT` / `◆ NEWS` / `◆ EDUKACJA` — kolor `#00AAFF`, bold, 26px
- Tytuł hooka: biały `#FFFFFF`, bold, 88px, 4–7 słów MAX
- `@motoedukacja` na dole, szary `#A0AEC0`, 22px

---

## Layout slajdów treści (3-zone) — OBOWIĄZUJĄCY STANDARD

Każdy slajd treści (nie-cover) musi mieć ten układ:

```
[80px]  ◆  KATEGORIA           ← TAG: niebieski #00AAFF, bold, font_size: 30
[160px] DUŻY TYTUŁ             ← TITLE: biały #FFFFFF, bold, font_size: 150
        DWUWIERSZOWY           ← szerokość 920px
        
        
[480px] Pierwsza linia treści.  ← BODY: szary #A0AEC0, normal, font_size: 80
        Druga linia treści.     ← line_height: 1.5, szerokość 920px
        Trzecia linia treści.
```

**Pozycje elementów (px od góry):**
| Element | top | left | font_size | kolor |
|---------|-----|------|-----------|-------|
| TAG | 80 | 80 | 30 | #00AAFF |
| TITLE | 160 | 80 | 150 | #FFFFFF |
| BODY | 480 | 80 | 80 | #A0AEC0 |

**Reguła body:** maksymalnie 3 krótkie linie, każda ~1 zdanie. Nigdy więcej.

---

## Element IDs — szablony slajdów treści

Wszystkie slajdy treści skopiowane z tego samego szablonu mają **identyczne element IDs**:

```
TAG   = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBXCQWWKSqslS01y
TITLE = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBkp3wC1Sj4GtV1x
BODY  = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBGyx4b4TXDYWbd9
```

**Page ID szablonu:** `PBQq6QRhypv3NmDk`

> Uwaga: Page ID jest wspólna dla wszystkich slajdów treści skopiowanych z tego samego szablonu. Jeśli slajd ma inne page_id, elementy mogą mieć inne IDs — sprawdź przez `start-editing-transaction`.

---

## Procedura edycji slajdu treści — ZAWSZE 2 KROKI

### Krok 1: Ustaw treść + formatowanie + pozycja BODY

```python
perform-editing-operations([
  # TAG
  replace_text(TAG_ID, "◆  KATEGORIA"),
  format_text(TAG_ID, color="#00AAFF", font_size=30, font_weight="bold"),
  
  # TITLE
  replace_text(TITLE_ID, "TYTUŁ W CAPS"),
  format_text(TITLE_ID, color="#FFFFFF", font_size=150, font_weight="bold"),
  resize_element(TITLE_ID, width=920),
  
  # BODY
  replace_text(BODY_ID, "Linia 1.\nLinia 2.\nLinia 3."),
  format_text(BODY_ID, color="#A0AEC0", font_size=80, font_weight="normal", line_height=1.5),
  resize_element(BODY_ID, width=920),
  position_element(BODY_ID, top=480, left=80),
])
```

### Krok 2: Napraw pozycje TAG i TITLE (ZAWSZE wymagane!)

Po zmianie font_size Canva **automatycznie przesuwa** TAG i TITLE — trzeba je ręcznie naprawić:

```python
perform-editing-operations([
  position_element(TAG_ID, top=80, left=80),
  position_element(TITLE_ID, top=160, left=80),
])
```

### Krok 3: Commit

```python
commit-editing-transaction(transaction_id)
```

---

## Dlaczego 2 kroki? (ważne!)

Canva przy zmianie `font_size` na dużą wartość (np. 150) **automatycznie przesuwa** wszystkie elementy żeby unikać nakładania. TAG ląduje na ujemnych wartościach top (np. -16, -100). Dlatego:
- Krok 1 ustawi treść i spozycjonuje BODY (bo BODY nie przesuwa innych)
- Krok 2 musi przyjść PO kroku 1 i ręcznie naprawić pozycje TAG i TITLE

Bez kroku 2 TAG będzie poza ekranem.

---

## Kalibracja font_size w Canva MCP

Canva używa własnych jednostek. Przelicznik:
- `font_size: 150` → ~97px wizualnie per linia (tytuł)
- `font_size: 80` → ~50px wizualnie per linia (treść)
- `font_size: 30` → ~19px wizualnie (tag)

Tytuł 1-liniowy ma height ~101px, 2-liniowy ~186px, 3-liniowy ~270px.

---

## Dostępne narzędzia Canva MCP

```
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__start-editing-transaction
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__perform-editing-operations
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__commit-editing-transaction
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__cancel-editing-transaction
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__get-design-thumbnail
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__copy-design
mcp__28b4b0bd-0190-4d50-a0a6-fc59aa317893__search-designs
```

**Przed użyciem:** Zawsze ładuj schematy przez `ToolSearch` z `select:` prefix.

---

## Pełna procedura tworzenia nowego posta

### 1. Wybierz temat
→ `content-topics.md`, zaznacz `[x]` po użyciu

### 2. Stwórz treść
Claude generuje tekst każdego slajdu według schematu z CLAUDE.md

### 3. Cover (Slajd 1)
→ Skopiuj szablon `DAHLPg874ao` → edytuj: TAG, tytuł hooka, zdjęcie tła

### 4. Slajdy treści (Slajdy 2–N)
→ Skopiuj szablon slajdu treści → zastosuj 3-zone layout (2-krokowa procedura)
→ Jeden punkt = jeden slajd, 3 linie BODY max

### 5. CTA (ostatni slajd)
→ Slajd treści z TAG `◆  ZAPISZ` lub `◆  OBSERWUJ`
→ BODY: "Obserwuj @motoedukacja.\nLink w bio → e-book."

### 6. Caption do posta
- Hook = pierwsze zdanie (ten sam co na cover)
- 3–5 zdań rozwinięcia
- CTA: "Zapisz żeby nie zapomnieć 📌"
- 10–15 hashtagów: #motoryzacja #motoedukacja #autofakty #samochody itp.

---

## Przykłady gotowych slajdów treści

### Fakt (1 linia tytuł)
```
TAG:   ◆  FAKT
TITLE: AUTO ELEKTRYCZNE MA 20 CZĘŚCI
BODY:  Benzynowe ma ich ~2000.
       Mniej części = mniej awarii.
       Dlatego elektryki mają niższe koszty serwisu.
```

### Mit (2 linie tytuł)
```
TAG:   ◆  MIT
TITLE: SILNIK TRZEBA OCIEPLAĆ
       PRZED RUSZENIEM
BODY:  To prawda dla aut sprzed lat 90.
       Nowoczesne silniki nie potrzebują rozgrzewania.
       Wystarczy 20–30 sekund i ruszaj spokojnie.
```

### CTA
```
TAG:   ◆  ZAPISZ
TITLE: TWÓJ MECHANIK CI TEGO
       NIE POWIE
BODY:  Takie fakty znajdziesz co tydzień.
       Obserwuj @motoedukacja.
       Link w bio → pełny e-book motoryzacyjny.
```

---

## Typowe błędy i rozwiązania

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| TAG poza ekranem (top: -100) | font_size 150 przesuwa elementy | Zawsze Krok 2: position_element TAG top:80 |
| TITLE nakrywa TAG | Auto-pozycjonowanie Canva | Krok 2: position_element TITLE top:160 |
| BODY nakrywa tytuł | font_size za mały, height za mały | Użyj font_size:80 i top:480 |
| Tekst ściśnięty | Za długie linie | Skróć tekst lub podziel na więcej slajdów |
| Transaction wygasła | Przerwa w sesji | Zacznij nową przez start-editing-transaction |
