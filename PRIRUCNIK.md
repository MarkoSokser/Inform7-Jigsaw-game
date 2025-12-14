# Jigsaw Inform 7 - Priručnik

## Tema i priča

Ova igra je tekstualna avantura inspirirana filmovima "Saw". Igrač se budi zarobljen u nizu smrtonosnih soba, suočen s moralnim i fizičkim izazovima. Kroz igru, igrač donosi odluke koje utječu na preživljavanje, odnos s drugim zatvorenikom (Marcus), i konačni ishod (sloboda, osveta, smrt).

## Struktura igre

- **Sobe:**
  1. Cell (ćelija)
  2. Exit Hall
  3. Medical Chamber (medicinska soba)
  4. Observation Room (promatračnica)
  5. Dark Corridor (tamni hodnik)
  6. Jaw Breaker Chamber (čeljusna zamka)
  7. Final Corridor (završni hodnik)
  8. Control Room (kontrolna soba)
  9. Jigsaw's Chamber (Jigsawova soba)
  10. Exit Hallway (izlaz)

- **Ključni likovi:**
  - Igrač (Adam)
  - Marcus (drugi zatvorenik, može preživjeti ili umrijeti)
  - Jigsaw (glavni antagonist)

## Napredne funkcije i mehanike

- **Višestruki završeci:**
  - Sloboda (freedom): riješiš sve zagonetke, ne ubiješ Jigsawa, izađeš kroz sjeverna vrata
  - Osveta (revenge): ubiješ Jigsawa, svi umiru
  - Milost (mercy): uđeš kod Jigsawa, ali ga poštediš i izađeš
- **Zagonetke i zamke:**
  - Ploče s bojama (Medical Chamber)
  - Trivia kviz (Jaw Breaker Chamber)
  - Finalni kod (Control Room)
- **Zvukovi i slike:**
  - 35+ zvukova (npr. alarm, self_destruct, explosion, kill, keyboard...)
  - 9+ slika (za svaku ključnu sobu)
- **Pratnja NPC-a:**
  - Marcus može pratiti igrača, umrijeti ili preživjeti ovisno o odlukama
- **Brojanje pokušaja i pogrešaka:**
  - Ograničen broj pokušaja za zagonetke
  - Brojanje točnih i netočnih odgovora
- **Petlje zvuka:**
  - Alarm svira u petlji dok je aktivan
- **Specijalne akcije:**
  - Korištenje predmeta (saw, key, medical supplies)
  - Posebne komande za svaku sobu (npr. approach terminal, examine screen, kill jigsaw, leave)

## Popis dostupnih komandi

- Kretanje: `n`, `s`, `e`, `w`, `north`, `south`, `east`, `west`
- Interakcija s objektima: `take`, `use`, `examine`, `look at`, `read`, `open`, `unlock`, `bandage`, `cut`, `saw`
- Posebne komande:
  - `approach terminal` (približi se terminalu)
  - `examine screen` (prikaži finalnu zagonetku)
  - `code ...` / `type ...` / `enter ...` (upiši kod na terminalu)
  - `kill jigsaw` (ubij Jigsawa)
  - `leave` (napusti Jigsawovu sobu ili terminal)
  - `wait` ili `z` (čekaj rundu, koristi se za nastavak nakon eksplozije ili završetka)

## Kako radi logika igre

- **Ulazak u sobu:**
  - Prikazuje se slika sobe i/ili zvuk
  - Prikazuje se opis i mogući izbori
- **Zagonetke:**
  - Svaka zagonetka ima ograničen broj pokušaja
  - Trivia kviz broji točne i netočne odgovore, 3 točna su dovoljna za prolaz
  - Finalni kod zahtijeva unos 4 ključne riječi (SACRIFICE TRUST PAIN CHOICE)
- **Zvukovi:**
  - Svaka važna radnja ima zvučni efekt
  - Alarm i explosion su u petlji ili na kraju
- **Završeci:**
  - Ovisno o izborima, igrač može preživjeti, umrijeti, osvetiti se ili poštedjeti Jigsawa

## Primjeri igranja

- **Rješavanje finalnog koda:**
  - `approach terminal`
  - `examine screen`
  - `code sacrifice trust pain choice`
- **Odlazak na slobodu:**
  - `n` (nakon što su vrata otključana)
- **Osveta:**
  - `s` (u Control Room, nakon otključavanja)
  - `kill jigsaw`
- **Milost:**
  - `s` (u Control Room, nakon otključavanja)
  - `leave` (u Jigsaw's Chamber)
  - `n` (iz Control Room)

## Savjeti za proširenje

- Dodaj više zagonetki ili soba
- Dodaj više NPC interakcija
- Dodaj bodovni sustav ili statistiku
- Dodaj više zvučnih efekata ili slika

## Tehničke napomene

- Projekt je pisan u Inform 7
- Sve slike i zvukovi moraju biti u odgovarajućim mapama
- Kompatibilno s Inform 7 IDE-om i standardnim interpreterima
