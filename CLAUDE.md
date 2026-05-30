# Projekt: KupAuto — Motoryzacja Edukacyjna

## O projekcie
Konto Instagram o charakterze **edukacyjnym** — fakty, newsy, ciekawostki motoryzacyjne.
Cel długoterminowy: zbudować bazę obserwujących → sprzedawać **e-booki motoryzacyjne**.

Pełna strategia: `instagram-strategy.html`

---

## Filary contentu (proporcje)
- **30% Szokujące Fakty** — liczby, rekordy, zaskakujące dane. Główny driver zasięgu.
- **25% Edukacja Techniczna** — jak działa silnik/turbo/skrzynia itp. Fundament e-booków.
- **20% Newsy Branżowe** — nowe modele, recall'e, przepisy, technologie.
- **15% Historia & Legendy** — początki marek, kultowe modele, słynne wyścigi.
- **10% Mity vs Prawda** — obalanie mitów. Generuje debaty i komentarze.

---

## Formaty postów

| Format | Slajdy | Cel |
|--------|--------|-----|
| Fakt Dnia | 1 | Szybkie zasięgi, udostępnienia |
| Karuzela Edukacyjna | 5–8 | Zapisywalność, wartość |
| Mit vs Prawda | 2–6 par | Komentarze, debata |
| Ranking / Top X | 6–10 | Zapisywalność, viralowość |
| Historia / Timeline | 5–8 | Emocje, nostalgia |
| Porównanie A vs B | 1–4 | Decyzyjny content |
| Quiz / Zagadka | 1–2 | Komentarze, zaangażowanie |
| News Tygodnia | 1–3 | Aktualność, autorytet |

---

## Schemat karuzeli (zawsze stosuj)
- **Slajd 1** — mocny hook, obietnica wartości
- **Slajdy środkowe** — jeden punkt = jeden slajd, konkretnie i krótko
- **Ostatni slajd** — CTA: komentarz / zapisz / link w bio do e-booka

---

## Hooki — schematy pierwszego zdania
- „Twój mechanik nigdy Ci tego nie powie, ale…"
- „W 60 sekund tłumaczę jak działa [X]. Zapisz post."
- „[X] rzeczy, których żałuję że nie wiedziałem kupując pierwsze auto."
- „[Kontrowersyjna teza]. Zgadzasz się? Komentarz 👇"
- „Kupujesz używane auto? Najpierw przeczytaj to."

---

## Plan e-booków (do promowania w postach)
1. **Jak Kupić Dobre Używane Auto** — checklist, błędy, negocjacje (49–79 zł)
2. **Silniki bez Tajemnic** — jak działają, niezawodność, oleje (59–89 zł)
3. **Auto na Rok: Oszczędności** — paliwo, serwis, ubezpieczenie (39–59 zł)
4. **Elektryki: Prawda i Mity** — koszty, porównania, dla kogo (49–79 zł)

---

## Styl wizualny postów
- Tło: `#0A0A0A` (głęboka czerń)
- Akcent: `#00AAFF` (niebieski) — liczby, tytuły, ikony, podkreślenia
- Tekst główny: `#FFFFFF`
- Tekst wtórny: `#A0AEC0`
- Czcionka pogrubiona (bold/black) na duże tytuły, regularna na treść
- Minimalistycznie — jeden główny przekaz na slajd
- Nazwa konta: `@motoedukacja`
- **Rozmiar czcionki**: nagłówki/tytuły — domyślny z szablonu; tekst treści (body) — minimum **36px**, żeby był czytelny na telefonie

---

## Rytm publikacji
- **Poniedziałek 18:00** — Fakt Dnia
- **Środa 18:00** — Karuzela Edukacyjna
- **Piątek 08:00** — Mit vs Prawda lub Ranking
- **Sobota 12:00** — Quiz tygodnia

---

## Szablon Cover Slajdu (Slajd 1 — zawsze identyczny)
Każdy post zaczyna się od **tego samego szablonu wizualnego**, tylko tekst się zmienia.

**Wzór:** Canva design ID `DAHLJBwk0is` (canva.com/d/AlWHI1bsTz3thCf)

**Układ:**
- Tło: `#0A0A0A` pełna czerń
- Lewa połowa: zdjęcie auta/silnika (zmieniane pod temat posta)
- Prawa połowa: teksty
  - `◆ FAKT` / `◆ NEWS` / `◆ MIT` — niebieski `#00AAFF`, bold, góra
  - Główny tytuł hooka — bardzo duży, `#00AAFF`, bold, 5–8 słów
  - `@motoedukacja` — szary `#A0AEC0`, małe, dół

**Zasada:** Przy każdym nowym poście kopiuj ten szablon → zmień tylko: tag (FAKT/NEWS/MIT), tytuł hooka, zdjęcie.

---

## Instrukcja dla Claude
Kiedy tworzę post lub Reels — **zawsze**:
1. Podaj gotowy tekst każdego slajdu z osobna (Slajd 1, Slajd 2…)
2. Podaj hook na pierwsze zdanie
3. Podaj opis do posta (caption) z CTA i hashtagami
4. Zasugeruj styl wizualny (kolory, układ tekstu na slajdzie)
5. Ostatni slajd zawsze z CTA nawiązującym do e-booka lub obserwowania
6. Slajd 1 zawsze według szablonu cover z `content-topics.md`

### Tworzenie postów newsowych — OBOWIĄZKOWE:
Przed każdym postem newsowym **zawsze** użyj WebSearch:
- Szukaj: `motoryzacja polska [aktualny miesiąc rok]`
- Szukaj: `nowe przepisy drogowe Polska [rok]`
- Szukaj: `recall wycofanie [marka] [rok]`
- Szukaj: `nowe auto [marka] [rok] Polska`
Nie twórz postów newsowych na podstawie samej wiedzy — zawsze weryfikuj aktualność.

### Tematy postów:
Korzystaj z bazy tematów w `content-topics.md`. Po użyciu tematu zaznacz go jako `[x]`.

---

## System Tygodniowego Uczenia Się
Każdy tydzień → aktualizuj `content-topics.md` sekcja "Wyniki i uczenie się":
1. Użytkownik podaje wyniki postów (zasięg, komentarze, zapisy)
2. Claude dodaje wnioski do `content-topics.md`
3. Kolejne posty uwzględniają te wnioski

**Jak "szkolić" Claude:**
- Powiedz mi co zadziałało: "Post o X miał 500 wyświetleń, a Y tylko 50"
- Powiedz mi co nie zadziałało: "Za mało konkretów", "Za długi tekst"
- Powiedz co chcesz inaczej: "Chcę agresywniejsze hooki"
- Ja zaktualizuję CLAUDE.md i content-topics.md z tymi wnioskami
- Od następnego tygodnia stosuję nowe zasady automatycznie
