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

### Post 6 — Fakt: Silnik F1 — Szokujące Liczby
- **Temat:** Silnik F1 kręci 18 000 RPM / spala 75L/100km / opony 120°C
- **Typ:** Karuzela Faktów (5 slajdów)
- **Status:** ✅ Gotowy, styl viral (żółte liczby + białe ALL CAPS) + cover @autoswir1 split layout
- **Design ID:** `DAHLyvb-d6I`
- **URL:** https://www.canva.com/d/bUlg7CYQ4mVRfI8
- **Pages:**
  - Cover (Slajd 1): `PBQq6QRhypv3NmDk` — **@autoswir1 split layout** (zdjęcie top 60%, czarny panel bottom 40%)
  - Slajd 2 (18 000 RPM): `PBbHZp6PVcsRYxmV`
  - Slajd 3 (120°C opony): `PBW7sFKp0JV2M9lR`
  - Slajd 4 (75L/100KM): `PBmD5DgT6cDJg4vY`
  - Slajd 5 (CTA): `PBbssXKWKX5TbGHp`
- **Zmiany stylistyczne vs poprzednie posty:**
  - TITLE: kolor `#FFD700` (żółty/złoty), font_size:260, bold — główna liczba zajmuje cały góry slajd
  - BODY: kolor `#FFFFFF` (biały), font_size:80, bold, ALL CAPS
  - @motoedukacja watermark: top:1010 (naprawione — było poza ekranem na top:1159)
  - **Cover: @autoswir1 split layout** — zdjęcie F1 top 620px (57%), czarny canvas bottom, tekst centered

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

## Cover — Styl @autoswir1 (SPLIT LAYOUT — obowiązujący od POST 6)

Zamiast full-bleed, cover ma dwa wyraźne obszary:

```
[0–620px]    ZDJĘCIE AUTA (full width, przycinane do 620px wysokości)
             → resize_element(img_element, width:1080, height:620)
             
[620–1080px] CZARNY PANEL (canvas background = #0A0A0A)
             → TAG: "SILNIK F1" / "MARKA MODEL" — biały, centered, font_size:90
             → TITLE: "18 000 RPM" / "SZOKUJĄCA LICZBA" — żółty #FFD700, centered, font_size:160
             → @motoedukacja — szary #A0AEC0, centered, font_size:38, top:1037
```

**Pozycje elementów w czarnym panelu:**
| Element | top | left | width | font_size | kolor | align |
|---------|-----|------|-------|-----------|-------|-------|
| TAG (label) | 720 | 0 | 1080 | 90 | #FFFFFF | center |
| TITLE (liczba/fakt) | 800 | 0 | 1080 | 160 | #FFD700 | center |
| @motoedukacja | 1037 | 0 | 1080 | 38 | #A0AEC0 | center |

**Procedura (3 kroki):**

**Krok 1:** update_fill + resize_element + replace/format/resize tekstu + position @moto
```python
update_fill(img_id, new_asset_id, "image")
resize_element(img_id, width=1080, height=620)        # kluczowe: przytnij do 57%
replace_text(TAG, "ETYKIETA")
format_text(TAG, color="#FFFFFF", font_size=90, bold, center)
resize_element(TAG, width=1080)
replace_text(TITLE, "LICZBA/FAKT")
format_text(TITLE, color="#FFD700", font_size=160, bold, center)
resize_element(TITLE, width=1080)
format_text(@moto, color="#A0AEC0", font_size=38, center)
resize_element(@moto, width=1080)
position_element(@moto, top=1037, left=0)
```

**Krok 2:** Napraw auto-pozycje TAG i TITLE (Canva przesuwa po font_size change)
```python
position_element(TAG, top=720, left=0)
position_element(TITLE, top=800, left=0)
```

**Krok 3:** Commit

**IDs elementów cover (page 1 szablonu):**
```
TAG   = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBXCQWWKSqslS01y
TITLE = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBkp3wC1Sj4GtV1x
@moto = PBQq6QRhypv3NmDk-LBzZ1zssl73QJXfF-LBGyx4b4TXDYWbd9
img   = PBQq6QRhypv3NmDk-LB11DsMLbKwwRtqx
```

**Uwagi:**
- Zdjęcie z jasnym tłem (studio) wygląda OK ale mniej dramatycznie niż ciemne
- Dla lepszego efektu użyj zdjęć F1 z ciemnym tłem (noc, tor, dramatyczne oświetlenie)
- Pexels URL: `https://images.pexels.com/photos/{ID}/pexels-photo-{ID}.jpeg?auto=compress&cs=tinysrgb&w=1920`
- Użyj `upload-asset-from-url` żeby załadować zdjęcie do Canva przed `update_fill`

---

## Layout slajdów treści — VIRAL STYLE (obowiązujący od POST 6)

Każdy slajd treści musi mieć układ dominującej liczby + kontekst:

```
[top:88]  DUŻA LICZBA           ← TITLE: żółty #FFD700, bold, font_size:260
          NA 2 LINIE            ← split newline \n dla liczb > 6 znaków
                                ← szerokość: 920px

[top:480] KRÓTKIE ZDANIA.       ← BODY: biały #FFFFFF, bold, font_size:90
          MAKS. 22 ZNAKI/LINIĘ. ← line_height:1.25, szerokość:920px
          3 LINIE MAX.
          
[top:1010] @motoedukacja        ← watermark: szary, mały, bottom
```

**Pozycje elementów (px od góry) — viral style:**
| Element | top | left | font_size | kolor |
|---------|-----|------|-----------|-------|
| TITLE (liczba) | 88 | 80 | 260 | #FFD700 |
| BODY | 480 (po 1-linii) / 480+ (po 2-linii) | 80 | 90 | #FFFFFF |
| @motoedukacja | 1010 | 50 | auto | #A0AEC0 |

**KLUCZOWE ZASADY VIRAL STYLE:**
- Liczba ZAWSZE żółta (#FFD700), bold, font_size:260 — dominuje slajd
- Liczby > 6 znaków → split na 2 linie (`\n`) → zajmuje ~35% slajdu
- Body text: biały, bold, ALL CAPS, krótkie linie (max 22 znaki at font_size:90)
- Nigdy szary tekst (#A0AEC0) na content slajdach — TYLKO biały!
- Po split tytułu na 2 linie → BODY przesuwa się do top:480+

**Reguła body:** maksymalnie 3 krótkie linie, max 22 znaki/linię przy font_size:90. Nigdy więcej.

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
| BODY nakrywa tytuł | font_size za mały, height za mały | Użyj font_size:90 i top:480 |
| Tekst ściśnięty | Za długie linie | Max 22 znaki/linię przy font_size:90 |
| Transaction wygasła | Przerwa w sesji | Zacznij nową przez start-editing-transaction |
| @motoedukacja poza slajdem | Split TITLE na 2 linie przesuwa watermark | position_element @moto top:1010 left:50 |
| Liczba za mała wizualnie | 1 linia przy font_size:260 = ~16% slajdu | Split na 2 linie (\n) = ~35% slajdu |
| Tekst "centered" ale wcięty | left:50 zamiast left:0 przy width:1080 | Zawsze left:0 gdy text_align:center i width:1080 |
| Foto zajmuje cały slajd, brak czarnego panelu | height:1080 | resize_element(img, width:1080, height:620) → panel pojawia się poniżej |
