# Jigsaw Inform 7 - Super Detaljni Priručnik

## 1. Tema i inspiracija

Ova igra je tekstualna avantura inspirirana filmovima "Saw". Igrač preuzima ulogu žrtve zarobljene u nizu smrtonosnih soba, gdje mora donositi teške moralne i logičke odluke kako bi preživio. Kroz igru se istražuju teme žrtve, povjerenja, boli, izbora i osvete.

## 2. Priča i struktura

Igrač (Adam) budi se u ćeliji i prolazi kroz niz soba:
- **Cell**: Početna ćelija, buđenje i prvi izbori.
- **Exit Hall**: Prijelazna zona.
- **Medical Chamber**: Prva velika zagonetka s pločama u boji i mogućnostima samopovređivanja.
- **Observation Room**: Promatranje, rješavanje zamki, test povjerenja.
- **Dark Corridor**: Prijelazna zona.
- **Jaw Breaker Chamber**: Trivia kviz s ograničenim brojem pokušaja, brutalna kazna za neuspjeh.
- **Final Corridor**: Priprema za završni test.
- **Control Room**: Glavna završna zagonetka (četiri ključne riječi), dvije izlazne opcije.
- **Jigsaw's Chamber**: Suočavanje s glavnim antagonistom, moralni izbor (ubiti ili poštedjeti).
- **Exit Hallway**: Završni izlaz i epilog.

## 3. Funkcionalnosti i mehanike

### Osnovne funkcije
- Kretanje po sobama (n, s, e, w)
- Pregledavanje i korištenje predmeta (examine, take, use, bandage, saw, cut, unlock, open)
- Interakcija s NPC-jem (Marcus)
- Rješavanje zagonetki i kvizova
- Prikaz slika i zvukova za atmosferu

### Napredne funkcije
- Višestruki završeci (sloboda, osveta, milost)
- Brojanje pokušaja i pogrešaka u zagonetkama
- Petlje zvuka (alarm, explosion)
- Pratnja NPC-a (Marcus može preživjeti ili umrijeti)
- Dinamičko otključavanje vrata i soba
- Posebne akcije: approach terminal, examine screen, kill jigsaw, leave
- Korištenje zvukova i slika za svaki ključni trenutak
- Prikaz animiranih sekvenci (odbrojavanje, eksplozija)
- Ograničeni resursi (medicinski materijal, ključevi)

## 4. Logika i tijek igre

- Svaka soba ima svoj ulazni efekt (slika, zvuk, tekst)
- Zagonetke imaju ograničen broj pokušaja, pogreške vode do smrti ili težih posljedica
- Trivia kviz: 3 točna odgovora su dovoljna za prolaz, 3 pogrešna vode do smrti
- Finalni kod: igrač mora unijeti četiri ključne riječi (SACRIFICE TRUST PAIN CHOICE)
- Svaka važna radnja ima zvučni efekt (npr. self_destruct, alarm, explosion, kill, keyboard)
- Alarm svira u petlji dok je aktivan, explosion se pokreće na kraju
- NPC Marcus može biti spasen ili umrijeti, što utječe na završetak
- U Jigsaw's Chamber igrač bira: kill (smrt oboje), leave (povratak u Control Room, mogućnost izlaska)
- Izlazak kroz freedom door vodi u Exit Hallway i završava igru s epilogom

## 5. Popis svih komandi

### Osnovne komande
- `n`, `s`, `e`, `w` (kretanje)
- `look`, `examine`, `read`, `take`, `use`, `open`, `unlock`, `bandage`, `cut`, `saw`
- `inventory` (popis predmeta)

### Napredne komande
- `approach terminal` (približi se terminalu)
- `examine screen` (prikaži finalnu zagonetku)
- `code ...` / `type ...` / `enter ...` (upiši kod na terminalu)
- `kill jigsaw` (ubij Jigsawa)
- `leave` (napusti Jigsawovu sobu ili terminal)
- `wait` ili `z` (čekaj rundu, koristi se za nastavak nakon eksplozije ili završetka)

## 6. Sobe i specifične mehanike

- **Medical Chamber**: Ploče u boji, rezanje noge, Marcus može krvariti
- **Observation Room**: Povjerenje, zamka za ruku, Marcus može pomoći ili odustati
- **Jaw Breaker Chamber**: Trivia kviz, 3 točna odgovora za prolaz, 3 pogrešna = smrt
- **Control Room**: Pristup terminalu, unos koda, alarm u petlji, eksplozija na 3 pogrešna pokušaja
- **Jigsaw's Chamber**: Ubij ili poštedi Jigsawa, povratak u Control Room ako ga poštediš
- **Exit Hallway**: Završni izlaz, epilog

## 7. Zvukovi i slike

- 35+ zvukova: alarm, self_destruct, explosion, kill, keyboard, jaw_breaker, puppetlaugh, itd.
- 9+ slika: za svaku ključnu sobu (cell, medical_chamber, observation_room, jawbraker, coridor, final_test, jigsaw_man...)

## 8. Primjeri igranja

- Rješavanje finalnog koda:
  - `approach terminal`
  - `examine screen`
  - `code sacrifice trust pain choice`
- Odlazak na slobodu:
  - `n` (nakon što su vrata otključana)
- Osveta:
  - `s` (u Control Room, nakon otključavanja)
  - `kill jigsaw`
- Milost:
  - `s` (u Control Room, nakon otključavanja)
  - `leave` (u Jigsaw's Chamber)
  - `n` (iz Control Room)

## 9. Tehničke napomene

- Projekt je pisan u Inform 7
- Sve slike i zvukovi moraju biti u odgovarajućim mapama
- Kompatibilno s Inform 7 IDE-om i standardnim interpreterima
- Svi napredni efekti (petlje zvuka, animacije, brojači) su implementirani kroz Inform 7 pravila

## 10. Savjeti za proširenje

- Dodaj više zagonetki ili soba
- Dodaj više NPC interakcija
- Dodaj bodovni sustav ili statistiku
- Dodaj više zvučnih efekata ili slika
- Implementiraj naprednije AI ponašanje NPC-a

## 11. Povijest razvoja i odluka

- Svi problemi, bugovi i prijedlozi rješavani su kroz iterativni razgovor
- Svaka funkcionalnost je testirana i podešena prema povratnim informacijama
- Posebna pažnja posvećena je atmosferi (zvuk, slike, tekst)
- Svi završeci su balansirani da igrač ima osjećaj izbora i posljedica

## 12. Zaključak

Ovaj priručnik objedinjuje sve što je dogovoreno, implementirano i testirano kroz razvoj igre. Služi kao vodič za igrače, developere i buduće proširenje projekta.


