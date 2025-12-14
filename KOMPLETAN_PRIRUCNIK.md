# JIGSAW INFORM 7 - KOMPLETAN RAZVOJNI PRIRUČNIK

**Verzija:** 1.0 (Finalna)  
**Datum:** 14. decembar 2025  
**Autor:** Razvojni tim

---

## SADRŽAJ

1. [Uvod i tema](#1-uvod-i-tema)
2. [Priča i narativ](#2-priča-i-narativ)
3. [Struktura igre](#3-struktura-igre)
4. [Kompletna lista funkcionalnosti](#4-kompletna-lista-funkcionalnosti)
5. [Detaljne mehanike po sobama](#5-detaljne-mehanike-po-sobama)
6. [Popis svih komandi](#6-popis-svih-komandi)
7. [Zvučni i vizuelni efekti](#7-zvučni-i-vizuelni-efekti)
8. [Logika i algoritmi](#8-logika-i-algoritmi)
9. [Završeci igre](#9-završeci-igre)
10. [Razvojne odluke i izmjene](#10-razvojne-odluke-i-izmjene)
11. [Bugfixevi i optimizacije](#11-bugfixevi-i-optimizacije)
12. [Walkthrough primjeri](#12-walkthrough-primjeri)
13. [Tehnička implementacija](#13-tehnička-implementacija)

---

## 1. UVOD I TEMA

### Koncept
Ova igra je tekstualna avantura u stilu "Saw" filmova, gdje igrač preuzima ulogu žrtve zarobljene u nizu smrtonosnih soba. Igra istražuje teme:
- **Žrtve i samopožrtvovanja**
- **Povjerenja i izdaje**
- **Boli i izdržljivosti**
- **Izbora i posljedica**
- **Osvete i praštanja**

### Ciljevi igre
- Preživjeti kroz niz smrtonosnih testova
- Donijeti moralne odluke koje utječu na kraj
- Rješavati logičke i etičke zagonetke
- Odlučiti sudbinu svoju i drugih likova

---

## 2. PRIČA I NARATIV

### Početak
Igrač (Adam) se budi zarobljen u ćeliji. Ne zna kako je dospeo tu. Čuje distorzirani glas (Jigsaw Killer) koji objašnjava da mora proći kroz niz testova kako bi zaslužio život.

### Razvoj
Kroz sobe, igrač se suočava s:
- **Cell (Ćelija)**: Spuštajući se strop pokušava ga smrskati, mora odlučiti - prerezati nogu ili ne
- **Medical Chamber**: Zagonetka s bojama i mogućnost prebandažiranja rane
- **Observation Room**: Test povjerenja - može li vjerovati Marcusu ili odlučiti samostalno
- **Jaw Breaker Chamber**: Brutalni trivia kviz s death device na glavi
- **Control Room**: Finalni test - unos ključnih riječi
- **Jigsaw's Chamber**: Moralni izbor - ubiti ili poštedjeti Jigsawa

### Likovi
- **Adam** (igrač): Žrtva zarobljena u testovima
- **Marcus** (NPC): Drugi zatvorenik, može preživjeti ili umrijeti ovisno o odlukama
- **Jigsaw Killer**: Antagonist, umirući od raka, testira žrtve

### Završetak
Tri moguća završetka:
1. **Freedom (Sloboda)**: Igrač riješava sve testove i izlazi slobodan
2. **Revenge (Osveta)**: Igrač ubija Jigsawa, ali umiru oboje u eksploziji
3. **Mercy (Milost)**: Igrač poštedi Jigsawa i izlazi slobodan s moralnom prednosti

---

## 3. STRUKTURA IGRE

### Sobe (Redoslijed)
1. **Cell** - Početna ćelija
2. **Exit Hall** - Prijelazna zona
3. **Medical Chamber** - Medicinska soba s pločama
4. **Observation Room** - Promatračnica s testom povjerenja
5. **Dark Corridor** - Tamni hodnik (prijelaz)
6. **Jaw Breaker Chamber** - Soba s jaw breaker uređajem
7. **Final Corridor** - Završni hodnik prije finala
8. **Control Room** - Kontrolna soba s terminalom
9. **Jigsaw's Chamber** - Jigsawova soba
10. **Exit Hallway** - Finalni izlaz

### Mapa (Veze)
```
Cell → Exit Hall → Medical Chamber → Observation Room → Dark Corridor 
→ Jaw Breaker Chamber → Final Corridor → Control Room
                                              ↓ (north)
                                         Exit Hallway
                                              
                                       Control Room
                                              ↓ (south)
                                      Jigsaw's Chamber
```

---

## 4. KOMPLETNA LISTA FUNKCIONALNOSTI

### Osnovne funkcionalnosti
- ✅ Kretanje po sobama (n, s, e, w)
- ✅ Pregledavanje objekata (examine, look at, read)
- ✅ Uzimanje i korištenje predmeta (take, use, drop)
- ✅ Otvaranje i otključavanje vrata (open, unlock)
- ✅ Interakcija s NPC-em (Marcus)
- ✅ Prikaz inventara (inventory, i)

### Napredne funkcionalnosti
- ✅ Višestruki završeci (3 različita kraja)
- ✅ Dinamičko otključavanje vrata
- ✅ Brojanje pokušaja u zagonetkama
- ✅ Petlje zvuka (alarm loop)
- ✅ Animirane sekvence (odbrojavanje, eksplozija)
- ✅ Pratnja NPC-a kroz sobe
- ✅ Kondicionale rute (Marcus živ/mrtav)
- ✅ Posebne akcije (approach, examine screen, kill, leave)
- ✅ Prikaz slika za svaku sobu
- ✅ Reprodukcija zvukova za svaki događaj

### Mehaničke funkcionalnosti
- ✅ Rezanje noge ili ankla (saw leg/ankle)
- ✅ Bandažiranje (bandage myself/marcus)
- ✅ Trivia kviz s brojanjem točnih/netočnih odgovora
- ✅ Unos koda na terminalu (code/type/enter)
- ✅ Pristupanje terminalu (approach terminal)
- ✅ Pregled ekrana (examine screen)
- ✅ Ubijanje Jigsawa (kill jigsaw)
- ✅ Napuštanje scene (leave)

---

## 5. DETALJNE MEHANIKE PO SOBAMA

### CELL (Ćelija)

**Što se događa:**
- Igrač se budi prikovan za pod
- Strop se počinje spuštati (smrskat će igrača)
- Glas (Jigsaw) objašnjava situaciju
- Na podu je ručna pila

**Odluke:**
- Rezati nogu (SAW LEG) - igrač ostaje bez noge ali preživljava
- Rezati ruku/ankle (SAW ANKLE) - alternativa
- Čekati (WAIT) - smrt

**Zvukovi:**
- tape.ogg (Jigsaw govor)
- ceiling_move.ogg (strop se spušta)
- self_cut.ogg (rezanje)
- death_crush.ogg (smrt)

**Slika:**
- cell.png

**Ishodi:**
- Rezanje → preživljavanje, krvarenje, prolaz u Exit Hall
- Čekanje → instant smrt

---

### MEDICAL CHAMBER (Medicinska soba)

**Što se događa:**
- Soba s 4 ploče u bojama (crvena, plava, žuta, zelena)
- Na podu bilješka s redoslijedom: BLUE → RED → YELLOW → GREEN
- Igrač krvari (ako je prerezao nogu)
- Marcus također krvari (ako je živ)

**Zagonetka:**
- Stani na ploče u točnom redoslijedu
- Komande: STEP ON BLUE PLATE, STEP ON RED PLATE, etc.
- Točan redoslijed otključava vrata

**Krvarenje:**
- Svaki turn, krvarenje se povećava
- Nakon određenog broja turnova → smrt
- Rješenje: BANDAGE MYSELF ili BANDAGE MARCUS

**Zvukovi:**
- puzzle_activate.ogg (aktivacija zagonetke)
- plate_blue/red/yellow/green.ogg (svaka ploča)
- bleeding.ogg (krvarenje)
- wound_close.ogg (bandažiranje)

**Slike:**
- medical_chamber.png
- pressure_plates.png
- cut_leg.png
- marcus_bleeding.png

**Ishodi:**
- Točan redoslijed → otključavanje vrata
- Krivi redoslijed → alarm, pokušaj ponovo
- Prekasno bandažiranje → smrt od krvarenja

---

### OBSERVATION ROOM (Promatračnica)

**Što se događa:**
- Soba s monitorima, stolom, ormaricem
- Na zidu ventilacija (izlaz)
- Treba se popeti slaganjem namještaja
- Ako se igrač popne, zamka hvata ruku

**Test povjerenja:**
- Zamka hvata ruku/ruke
- Jigsaw postavlja pitanje: "Što može biti dano, ali nikad uzeto natrag?"
- Odgovor: TRUST
- Ako Marcus nije tu, igrač može žrtvovati ruku (SAW ARM)

**Zvukovi:**
- saw.ogg (zamka za ruku)
- screaming.ogg (bol)

**Slike:**
- observation_room.png
- arm-bandage.png

**Ishodi:**
- Točan odgovor (TRUST) → oslobađanje, otključavanje vrata
- Krivi odgovor → smrt od pile
- SAW ARM (solo) → oslobađanje, ali gubljena ruka

---

### JAW BREAKER CHAMBER (Soba s čeljusnom zamkom)

**Što se događa:**
- Ako igrač ide solo: stavlja se jaw breaker na glavu, trivia kviz
- Ako je Marcus prisutan: Marcus i igrač moraju odlučiti tko igra

**Trivia kviz:**
- 5 pitanja (Paris, Pacific, Four, Oxygen, Shakespeare)
- 3 točna odgovora → prolaz
- 3 pogrešna odgovora → jaw breaker se aktivira, smrt

**Pitanja:**
1. "Glavni grad Francuske?" → paris
2. "Najveći ocean?" → pacific
3. "Broj strana kvadrata?" → four / 4
4. "Element Au?" → oxygen
5. "Autor Romeo i Juliet?" → shakespeare

**Marcus scenario:**
- Igrač može izabrati Marcusa (LET MARCUS PLAY)
- Igrač može izabrati sebe (I PLAY)
- Ako Marcus igra i pogriješi 3 puta → Marcus umire brutalno

**Zvukovi:**
- jaw_breaker.ogg (aktivacija uređaja)
- beartrap.ogg (smrt)
- screaming.ogg (bol)

**Slike:**
- jawbraker.png (soba)
- beartrap.png (Marcusova smrt)

**Ishodi:**
- 3 točna → ključ u zidu, otključavanje jaw breakera, prolaz dalje
- 3 pogrešna → smrt (glava smrskana)
- Marcus smrt → igrač nastavlja sam

---

### FINAL CORRIDOR (Završni hodnik)

**Što se događa:**
- Prijelazna zona prije Control Room
- Refleksija o pređenom putu
- Ako je Marcus mrtav, igrač tuguje

**Zvukovi:**
- Nema specifičnih

**Slike:**
- coridor.png

**Ishodi:**
- Nastavak u Control Room

---

### CONTROL ROOM (Kontrolna soba)

**Što se događa:**
- Glavna kontrolna soba s monitorima
- Prikazuje sve prošle sobe na kamerama
- Terminal s finalom zagonetkom
- Dvoja vrata: NORTH (freedom), SOUTH (revenge)

**Sekvenca:**
1. Ulazak u sobu → slika, alive.ogg zvuk
2. APPROACH TERMINAL → self_destruct.ogg, Jigsaw monolog
3. EXAMINE SCREEN → alarm.ogg (loop), prikazuje zagonetku
4. TYPE CODE → keyboard.ogg, provjera odgovora

**Finalna zagonetka:**
- Pitanje: "Unesite četiri ključne riječi koje predstavljaju lekcije"
- Odgovor: **SACRIFICE TRUST PAIN CHOICE**
- Format: CODE SACRIFICE TRUST PAIN CHOICE

**Pokušaji:**
- 3 pokušaja za unos
- Svaki pogrešan unos → trap_fail.ogg
- 3 pogrešna → self_destruct.ogg, eksplozija, smrt

**Zvukovi:**
- alive.ogg (ulazak)
- self_destruct.ogg (pristup terminalu)
- alarm.ogg (loop nakon examine screen)
- keyboard.ogg (svaki unos)
- explosion.ogg (smrt)
- gameover.ogg (kraj)

**Slike:**
- final_test.png

**Ishodi:**
- Točan kod → otključavanje obje vrata
- 3 pogrešna pokušaja → eksplozija i smrt

---

### JIGSAW'S CHAMBER (Jigsawova soba)

**Što se događa:**
- Igrač ulazi u malu sobu
- Jigsaw leži na krevetu, umirući od raka
- Objašnjava da je postavio failsafe: ako mu srce prestane, sve eksplodira

**Izbor:**
- KILL JIGSAW → ubijanje, puppet izlazi iz zida, eksplozija, smrt
- LEAVE → povratak u Control Room, mogućnost izlaska

**Sekvenca ubijanja:**
1. KILL JIGSAW → kill.ogg, gušenje
2. Jigsaw umire
3. Puppet izlazi iz zida → puppetlaugh.ogg
4. Jigsaw govor o zamci
5. self_destruct.ogg, alarm.ogg
6. Odbrojavanje 10-1
7. explosion.ogg, smrt

**Sekvenca napuštanja:**
- LEAVE → povratak u Control Room
- Igrač može izabrati NORTH (freedom door) → Exit Hallway

**Zvukovi:**
- kill.ogg (ubijanje)
- puppetlaugh.ogg (lutka)
- self_destruct.ogg (aktivacija)
- alarm.ogg (eksplozija)
- explosion.ogg (eksplozija)

**Slike:**
- jigsaw_man.png

**Ishodi:**
- Ubijanje → smrt oboje
- Napuštanje → povratak, mogućnost izlaska

---

### EXIT HALLWAY (Izlaz)

**Što se događa:**
- Dugačak hodnik sa sunčevom svjetlošću na kraju
- Igrač je slobodan
- Igra završava s epilogom

**Zvukovi:**
- door.ogg (otvaranje vrata)

**Slike:**
- Nema (samo tekst)

**Ishodi:**
- Igra se završava s porukom: "You escaped. You survived. But the scars remain."

---

## 6. POPIS SVIH KOMANDI

### Opće komande
- `n`, `north` - Idi na sjever
- `s`, `south` - Idi na jug
- `e`, `east` - Idi na istok
- `w`, `west` - Idi na zapad
- `look`, `l` - Pogledaj oko sebe
- `inventory`, `i` - Prikaz inventara
- `examine [objekt]`, `x [objekt]` - Pregledaj objekt
- `take [objekt]`, `get [objekt]` - Uzmi objekt
- `drop [objekt]` - Ispusti objekt
- `wait`, `z` - Čekaj jednu rundu

### Specifične komande po sobama

**Cell:**
- `saw leg` - Prereži nogu
- `saw ankle` - Prereži gležanj
- `cut leg` - Prereži nogu (sinonim)

**Medical Chamber:**
- `step on blue plate` - Stani na plavu ploču
- `step on red plate` - Stani na crvenu ploču
- `step on yellow plate` - Stani na žutu ploču
- `step on green plate` - Stani na zelenu ploču
- `bandage myself` - Zavijaj sebe
- `bandage marcus` - Zavijaj Marcusa
- `use gauze` - Koristi gazu
- `read note` - Pročitaj bilješku

**Observation Room:**
- `position chair` - Postavi stolicu
- `position cabinet` - Postavi ormarić
- `climb` - Popni se
- `respond trust` - Odgovori "trust"
- `answer trust` - Odgovori "trust" (sinonim)
- `saw arm` - Prereži ruku (solo scenario)

**Jaw Breaker Chamber:**
- `wear device` - Stavi uređaj na glavu
- `put on device` - Stavi uređaj na glavu
- `respond [answer]` - Odgovori na pitanje
- `let marcus play` - Pusti Marcusa da igra
- `i play` - Ja igram
- `take key` - Uzmi ključ
- `unlock device with key` - Otključaj uređaj s ključem
- `use key on device` - Koristi ključ na uređaju

**Control Room:**
- `approach terminal` - Približi se terminalu
- `examine screen` - Pogledaj ekran
- `code [text]` - Upiši kod
- `type [text]` - Upiši tekst
- `enter [text]` - Upiši tekst
- `open north door` - Otvori sjeverna vrata (freedom)
- `open south door` - Otvori južna vrata (revenge)

**Jigsaw's Chamber:**
- `kill jigsaw` - Ubij Jigsawa
- `murder jigsaw` - Ubij Jigsawa
- `strangle jigsaw` - Uguši Jigsawa
- `attack jigsaw` - Napadni Jigsawa
- `leave` - Napusti sobu
- `walk away` - Odi (sinonim)

---

## 7. ZVUČNI I VIZUELNI EFEKTI

### Kompletna lista zvukova (35 zvukova)

| Zvuk | Datoteka | Korištenje |
|------|----------|------------|
| TapeVoice | tape.ogg | Jigsaw govor na početku |
| ButtonPress | button_press.ogg | Pritisak dugmeta |
| CeilingMove | ceiling_move.ogg | Spuštanje stropa |
| SelfCut | self_cut.ogg | Rezanje noge |
| NPCCut | npc_cut.ogg | NPC rezanje |
| DeathCrush | death_crush.ogg | Smrt od stropa |
| Idea | idea.ogg | Ideja |
| PuzzleActivate | puzzle_activate.ogg | Aktivacija zagonetke |
| Bleeding | bleeding.ogg | Krvarenje |
| WoundClose | wound_close.ogg | Zatvaranje rane |
| PrisonerWake | prisoner_wake.ogg | Buđenje zatvorenika |
| TrapFail | trap_fail.ogg | Pogreška u zamci |
| PlateRed | plate_red.ogg | Crvena ploča |
| PlateBlue | plate_blue.ogg | Plava ploča |
| PlateYellow | plate_yellow.ogg | Žuta ploča |
| PlateGreen | plate_green.ogg | Zelena ploča |
| Screaming | screaming.ogg | Vriskanje |
| GameOver | gameover.ogg | Kraj igre |
| BodyFall | body_fall.ogg | Pad tijela |
| GameOverMusic | game_over_music.ogg | Muzika kraj igre |
| JigsawVoice | game.ogg | Jigsaw glas |
| SawTrap | saw.ogg | Zamka pile |
| ChairMove | chair.ogg | Pomjeranje stolice |
| Pressure | pressure.ogg | Pritisak |
| GameOver2 | gameover2.ogg | Alternativni game over |
| AdamCare | care.ogg | Adam briga |
| JawBreaker | jaw_breaker.ogg | Jaw breaker aktivacija |
| GasRelease | gas.ogg | Puštanje gasa |
| SadMusic | sad.ogg | Tužna muzika |
| AliveSound | alive.ogg | Zvuk života |
| DoorOpen | door.ogg | Otvaranje vrata |
| Keyboard | keyboard.ogg | Tipkanje |
| SelfDestruct | self_destruct.ogg | Samouništenje |
| PuppetLaugh | puppetlaugh.ogg | Smijeh lutke |
| Kill | kill.ogg | Ubijanje |
| AlarmSound | alarm.ogg | Alarm |
| Explosion | explosion.ogg | Eksplozija |

### Kompletna lista slika (13 slika)

| Slika | Datoteka | Korištenje |
|-------|----------|------------|
| CellImage | cell.png | Početna ćelija |
| MedicalChamberImage | medical_chamber.png | Medicinska soba |
| MarcusBleedingImage | marcus_bleeding.png | Marcus krvari |
| PressurePlatesImage | pressure_plates.png | Ploče u boji |
| CutLegImage | cut_leg.png | Prerezana noga |
| ArmBandageImage | arm-bandage.png | Zavoj na ruci |
| ObservationRoomImage | observation_room.png | Promatračnica |
| SawManImage | saw_man.png | Jigsaw na ekranu |
| JawBreakerRoomImage | jawbraker.png | Jaw breaker soba |
| BearTrapImage | beartrap.png | Bear trap (Marcusova smrt) |
| FinalCorridorImage | coridor.png | Završni hodnik |
| ControlRoomImage | final_test.png | Kontrolna soba |
| JigsawChamberImage | jigsaw_man.png | Jigsawova soba |

---

## 8. LOGIKA I ALGORITMI

### Brojanje pokušaja (Trivia kviz)

**Logika:**
```
Jaw-correct-answers = 0
Jaw-wrong-answers = 0
Jaw-current-question = 1

Za svaki odgovor:
  Ako je točan:
    Jaw-correct-answers++
    Ako Jaw-correct-answers >= 3:
      Otključaj ključ, završi kviz
    Inače:
      Sljedeće pitanje
  Ako je pogrešan:
    Jaw-wrong-answers++
    Ako Jaw-wrong-answers >= 3:
      Aktiviraj jaw breaker, smrt
    Inače:
      Sljedeće pitanje
```

**Ključna funkcionalnost:**
- Igrač treba 3 točna odgovora za prolaz
- Može pogriješiti 2 puta
- 3. pogreška = smrt

### Petlja alarma (Control Room)

**Logika:**
```
Alarm-active = false

Kada examine screen:
  Alarm-active = true
  Play AlarmSound

Svaki turn:
  Ako Alarm-active == true:
    Ako Final-puzzle-solved == true:
      Alarm-active = false
    Inače ako player nije u Control Room:
      Alarm-active = false
    Inače:
      Play AlarmSound (ponovo)
```

**Ključna funkcionalnost:**
- Alarm svira svaki turn dok je aktivan
- Zaustavlja se kad puzzle bude riješen ili igrač izađe

### Eksplozija nakon countdown

**Logika:**
```
Explosion-countdown = 0

Kada 3 pogrešna pokušaja:
  Odbrojavanje 10-1
  Play Explosion
  Explosion-countdown = 1

Svaki turn:
  Ako Explosion-countdown > 0:
    Explosion-countdown--
    Ako Explosion-countdown == 0:
      "THE END"
      Kraj igre
```

**Ključna funkcionalnost:**
- Eksplozija se svira odmah
- Čeka se 1 turn (Z)
- Zatim game over

### Krvarenje (Medical Chamber)

**Logika:**
```
Player-bleeding-turns = 0
Prisoner-bleeding-turns = 0

Svaki turn ako Player-bleeding == true:
  Player-bleeding-turns++
  Ako Player-bleeding-turns >= 5:
    Smrt od krvarenja

Bandage myself:
  Player-bleeding = false
  Player-bleeding-turns = 0
```

**Ključna funkcionalnost:**
- Krvarenje se povećava svaki turn
- Nakon 5 turnova = smrt
- Bandažiranje zaustavlja krvarenje

---

## 9. ZAVRŠECI IGRE

### 1. FREEDOM (Sloboda)

**Uvjeti:**
- Riješiti sve zagonetke
- Unijeti točan kod u Control Room
- Izabrati sjeverna vrata (NORTH)
- Ne ubiti Jigsawa (ili ga ne posjetiti)

**Sekvenca:**
1. CODE SACRIFICE TRUST PAIN CHOICE (u Control Room)
2. Obje vrata se otključavaju
3. GO NORTH
4. Otvaranje freedom door
5. Ulazak u Exit Hallway
6. Epilog: "You escaped. You survived. But the scars remain."
7. Game over (pozitivan završetak)

**Zvukovi:**
- door.ogg

**Ishod:**
- Igrač preživljava i izlazi slobodan

---

### 2. REVENGE (Osveta)

**Uvjeti:**
- Riješiti sve zagonetke
- Unijeti točan kod u Control Room
- Izabrati južna vrata (SOUTH)
- Ubiti Jigsawa (KILL JIGSAW)

**Sekvenca:**
1. CODE SACRIFICE TRUST PAIN CHOICE (u Control Room)
2. GO SOUTH
3. Ulazak u Jigsaw's Chamber
4. KILL JIGSAW
5. kill.ogg (gušenje)
6. Puppet izlazi → puppetlaugh.ogg
7. Jigsaw objašnjava zamku
8. self_destruct.ogg, alarm.ogg
9. Odbrojavanje 10-1
10. explosion.ogg
11. "THE END - You chose revenge, but died with him."
12. Z (čekanje)
13. Game over (negativan završetak)

**Zvukovi:**
- kill.ogg
- puppetlaugh.ogg
- self_destruct.ogg
- alarm.ogg
- explosion.ogg
- gameover.ogg

**Ishod:**
- Igrač i Jigsaw umiru u eksploziji

---

### 3. MERCY (Milost)

**Uvjeti:**
- Riješiti sve zagonetke
- Unijeti točan kod u Control Room
- Izabrati južna vrata (SOUTH)
- Ući u Jigsaw's Chamber
- Napustiti Jigsawa (LEAVE)
- Vratiti se u Control Room
- Izabrati sjeverna vrata (NORTH)

**Sekvenca:**
1. CODE SACRIFICE TRUST PAIN CHOICE (u Control Room)
2. GO SOUTH
3. Ulazak u Jigsaw's Chamber
4. LEAVE
5. Povratak u Control Room
6. GO NORTH
7. Otvaranje freedom door
8. Ulazak u Exit Hallway
9. Epilog: "You escaped. You chose mercy. The scars remain, but you're free."
10. Game over (pozitivan završetak s moralnom prednosti)

**Zvukovi:**
- door.ogg

**Ishod:**
- Igrač preživljava, poštedio je Jigsawa, moralna pobjeda

---

### 4. SMRT (Različiti scenariji)

**Smrt od stropa (Cell):**
- Uvjet: Čekanje bez rezanja noge
- Zvuk: death_crush.ogg
- Game over

**Smrt od krvarenja (Medical Chamber):**
- Uvjet: Ne zavijanje rane na vrijeme
- Zvuk: body_fall.ogg
- Game over

**Smrt od pile (Observation Room):**
- Uvjet: Krivi odgovor na pitanje
- Zvuk: saw.ogg, screaming.ogg
- Game over

**Smrt od jaw breakera (Jaw Breaker Chamber):**
- Uvjet: 3 pogrešna odgovora u triviji
- Zvuk: jaw_breaker.ogg, screaming.ogg
- Game over

**Smrt od eksplozije (Control Room):**
- Uvjet: 3 pogrešna unosa koda
- Zvuk: explosion.ogg, gameover.ogg
- Game over

**Smrt od eksplozije (Jigsaw's Chamber):**
- Uvjet: Ubijanje Jigsawa
- Zvuk: explosion.ogg, gameover.ogg
- Game over

---

## 10. RAZVOJNE ODLUKE I IZMJENE

### Faza 1: Osnovna struktura
- Kreirane sve sobe (Cell → Exit Hallway)
- Postavljeni osnovni opisi
- Implementirane veze između soba

### Faza 2: Zagonetke
- Medical Chamber: ploče u bojama, redoslijed BLUE-RED-YELLOW-GREEN
- Observation Room: test povjerenja, odgovor TRUST
- Jaw Breaker Chamber: trivia kviz, 5 pitanja
- Control Room: finalni kod, SACRIFICE TRUST PAIN CHOICE

### Faza 3: NPC (Marcus)
- Implementiran Marcus kao pratilac
- Dodane odluke: Marcus može umrijeti ili preživjeti
- Različiti scenariji u Jaw Breaker Chamber

### Faza 4: Zvukovi i slike
- Dodano 35 zvukova za svaki događaj
- Dodano 13 slika za atmosferu
- Implementirana petlja alarma

### Faza 5: Završeci
- Implementirana tri glavna završetka (Freedom, Revenge, Mercy)
- Dodana Jigsaw's Chamber s moralnim izborom
- Implementiran puppet failsafe

### Faza 6: Bugfixevi i optimizacije
- Ispravljen jaw_breaker.ogg (nije se čuo)
- Ispravljena logika trivije (3 točna odgovora dovoljno)
- Ispravljena observation room slika (nije se prikazivala)
- Ispravljeni nazivi vrata (izbjegnuti konflikti)
- Ispravljeni text substitution errori
- Dodana approach terminal i examine screen akcije
- Ispravljena leave akcija u Jigsaw's Chamber

---

## 11. BUGFIXEVI I OPTIMIZACIJE

### Bug #1: jaw_breaker.ogg se ne čuje (Room 4)
**Problem:** Zvuk jaw_breaker.ogg se ne čuje kada Marcus umire.
**Uzrok:** Više zvukova se svira istovremeno, jaw_breaker se prekriva.
**Rješenje:** Odvojen jaw_breaker zvuk da svira prvi, samostalno, prije drugih zvukova.

### Bug #2: Trivia kviz ne završava nakon 3 točna (Room 4)
**Problem:** Ako igrač ima 3 točna i 2 pogrešna, kviz ne završava.
**Uzrok:** Logika je gledala samo broj pitanja, ne broj točnih odgovora.
**Rješenje:** Dodana varijabla Jaw-correct-answers, kviz završava čim igrač ima 3 točna.

### Bug #3: Observation Room slika se ne prikazuje
**Problem:** Slika observation_room.png se ne prikazuje pri ulasku.
**Uzrok:** "stop the action" je sprječavao display komandu.
**Rješenje:** Uklonjen "stop the action", promijenjen redoslijed prikaza.

### Bug #4: Dark Corridor prikazuje krivu sliku
**Problem:** Dark Corridor prikazuje FinalCorridorImage umjesto ništa.
**Uzrok:** Copy-paste greška.
**Rješenje:** Uklonjeno prikazivanje slike u Dark Corridor.

### Bug #5: Inform 7 syntax error - door names
**Problem:** "Control room entrance" i "jigsaw door" su u konfliktu s imenima soba.
**Uzrok:** Inform 7 ne dozvoljava da vrata imaju nazive koji djelomično odgovaraju sobama.
**Rješenje:** Preimenovana vrata: "final entrance door" i "revenge door".

### Bug #6: Text substitution error
**Problem:** [tekst] u say naredbama je tretiran kao substitucija.
**Uzrok:** [ ] su rezervirani za Inform 7 substitucije.
**Rješenje:** Zamijenjeno [ ] sa ( ) u svim tekstovima.

### Bug #7: Comparison syntax error
**Problem:** "is 3 or greater" nije validna Inform 7 sintaksa.
**Uzrok:** Inform 7 ne podržava "or greater" u poređenju.
**Rješenje:** Zamijenjeno sa "is at least 3".

### Bug #8: Control Room alarm loop ne radi
**Problem:** Alarm ne svira u petlji.
**Uzrok:** Nije implementirana "Every turn" logika.
**Rješenje:** Dodana varijabla Alarm-active i Every turn pravilo.

### Bug #9: Freedom door "leads nowhere"
**Problem:** Igrač ne može izaći kroz freedom door.
**Uzrok:** Nedostaje Exit Hallway soba.
**Rješenje:** Dodana Exit Hallway soba sjeverno od freedom door.

### Bug #10: Leave u Jigsaw's Chamber završava igru odmah
**Problem:** Igrač ne može izabrati freedom nakon što napusti Jigsawa.
**Uzrok:** Leave akcija je automatski teleportirala igrača na izlaz.
**Rješenje:** Promijenjeno da leave vraća igrača u Control Room.

### Optimizacija #1: Zvuk self_destruct u Control Room
**Problem:** Svira krivi zvuk (JigsawVoice umjesto self_destruct).
**Uzrok:** JigsawVoice je odmah pratio self_destruct i prekrivao ga.
**Rješenje:** Uklonjen JigsawVoice, ostao samo self_destruct.

### Optimizacija #2: Explosion countdown
**Problem:** Explosion se svira i igra odmah završava.
**Uzrok:** Nije bilo pauze između explosion zvuka i game over.
**Rješenje:** Dodana varijabla Explosion-countdown, čeka 1 turn prije game over.

### Optimizacija #3: Alarm zvuk u Control Room
**Problem:** Alarm svira samo jednom.
**Uzrok:** Nije implementirana petlja.
**Rješenje:** Dodano "Every turn when Alarm-active is true: play AlarmSound".

### Optimizacija #4: Screen examine u Control Room
**Problem:** Zagonetka se prikazuje odmah nakon approach terminal.
**Uzrok:** Sve je bilo u jednoj akciji.
**Rješenje:** Razdvojeno: approach terminal → Jigsaw govor, examine screen → zagonetka, alarm.

---

## 12. WALKTHROUGH PRIMJERI

### Walkthrough 1: Freedom (Solo)

```
START
> look
> saw leg
> e
> e
> read note
> step on blue plate
> step on red plate
> step on yellow plate
> step on green plate
> bandage myself
> e
> position chair
> position cabinet
> climb
> respond trust
> e
> e
> wear device
> respond paris
> respond pacific
> respond four
> respond oxygen
(Završeno, 3 točna)
> take key
> unlock device with key
> e
> e
> approach terminal
> examine screen
> code sacrifice trust pain choice
> n
THE END - Freedom
```

### Walkthrough 2: Revenge (Solo)

```
START
> saw leg
> e
> e
> step on blue plate
> step on red plate
> step on yellow plate
> step on green plate
> bandage myself
> e
> position chair
> position cabinet
> climb
> respond trust
> e
> e
> wear device
> respond paris
> respond pacific
> respond four
(Završeno, 3 točna)
> take key
> unlock device with key
> e
> e
> approach terminal
> examine screen
> code sacrifice trust pain choice
> s
> kill jigsaw
(Eksplozija)
> z
THE END - Revenge (Death)
```

### Walkthrough 3: Mercy (Solo)

```
START
> saw leg
> e
> e
> step on blue plate
> step on red plate
> step on yellow plate
> step on green plate
> bandage myself
> e
> position chair
> position cabinet
> climb
> respond trust
> e
> e
> wear device
> respond paris
> respond pacific
> respond four
(Završeno, 3 točna)
> take key
> unlock device with key
> e
> e
> approach terminal
> examine screen
> code sacrifice trust pain choice
> s
> leave
> n
THE END - Freedom (Mercy)
```

### Walkthrough 4: Sa Marcusom (Incomplete - Marcus dies)

```
START
> saw leg
> e
> e
> step on blue plate
> step on red plate
> step on yellow plate
> step on green plate
> bandage myself
> bandage marcus
> e
> position chair
> position cabinet
> climb
> respond trust
> e
> e
> let marcus play
(Marcus igra trivia i umire)
> e
> e
> approach terminal
> examine screen
> code sacrifice trust pain choice
> n
THE END - Freedom (Alone)
```

---

## 13. TEHNIČKA IMPLEMENTACIJA

### Inform 7 Struktura

**Chapters:**
- Chapter 1: The Cell
- Chapter 1b: Sounds
- Chapter 15: Game Start
- Chapter 17: Entering Medical Chamber
- Chapter 27: Visual and Audio Cues
- Chapter 28: Hints for the Puzzle
- Chapter 29: Observation Room Furniture Positioning
- Chapter 31: The Impossible Question Timer and Solo Escape
- Chapter 36: Entering Observation Room With Marcus
- Chapter 37: Final Exit
- Chapter 38: Room 4 The Jaw Breaker Chamber
- Chapter 39: Room 4 Variables
- Chapter 39b: Room 5 Transition Corridor
- Chapter 39c: Room 5 The Final Control Room
- Chapter 39d: Room 5 Variables
- Chapter 40: Entering Room 4
- Chapter 42: Solo Scenario Unlocking Device
- Chapter 43: Marcus Scenario Making Choice
- Chapter 44: Marcus Death in Jaw Breaker
- Chapter 45: Room 5 Entry
- Chapter 45b: Approaching Terminal
- Chapter 46: Terminal Code Entry
- Chapter 47: Freedom Ending
- Chapter 48: Revenge Ending

### Varijable (Variables)

**Cell:**
- Prisoner-cut (truth state)
- Player-cut (truth state)

**Medical Chamber:**
- Player-bleeding (truth state)
- Player-bleeding-turns (number)
- Prisoner-bleeding (truth state)
- Prisoner-bleeding-turns (number)

**Observation Room:**
- Player-hands-trapped (number)
- Observation-room-trap-activated (truth state)
- Question-asked (truth state)
- Player-answered (truth state)

**Jaw Breaker Chamber:**
- Jaw-device-worn (truth state)
- Jaw-puzzle-activated (truth state)
- Jaw-puzzle-solved (truth state)
- Jaw-wrong-answers (number)
- Jaw-correct-answers (number)
- Jaw-current-question (number)
- Marcus-jaw-choice-made (truth state)
- Marcus-jaw-playing (truth state)

**Control Room:**
- Final-puzzle-solved (truth state)
- Terminal-code-entered (truth state)
- Terminal-approached (truth state)
- Screen-examined (truth state)
- Alarm-active (truth state)
- Explosion-countdown (number)
- Code-attempts (number)

**Jigsaw's Chamber:**
- Revenge-chosen (truth state)
- Freedom-chosen (truth state)
- Kill-sequence-countdown (number)
- Mercy-ending-countdown (number)

### Actions (Akcije)

**Cell:**
- Sawing leg
- Sawing ankle

**Medical Chamber:**
- Stepping on plate
- Bandaging

**Observation Room:**
- Positioning furniture
- Climbing
- Responding to question
- Sawing arm

**Jaw Breaker Chamber:**
- Wearing device
- Responding to question
- Choosing Marcus to play
- Choosing self to play
- Unlocking jaw device with

**Control Room:**
- Approaching terminal
- Examining screen
- Entering code

**Jigsaw's Chamber:**
- Killing jigsaw
- Leaving jigsaw

### Instead pravila (Instead rules)

- Instead of waiting in Cell
- Instead of examining ceiling in Cell
- Instead of going south from Control Room
- Instead of killing jigsaw (when not in chamber)
- Instead of leaving jigsaw (when not in chamber)

### After pravila (After rules)

- After going to Medical Chamber for the first time
- After going to Observation Room for the first time
- After going to Jaw Breaker Chamber for the first time
- After going to Final Corridor for the first time
- After going to Control Room for the first time
- After going to Jigsaw's Chamber for the first time
- After going to Exit Hallway

### Every turn pravila (Every turn rules)

- Every turn when Player-bleeding is true
- Every turn when Prisoner-bleeding is true
- Every turn when Alarm-active is true
- Every turn when Explosion-countdown is greater than 0
- Every turn when Kill-sequence-countdown is greater than 0
- Every turn when Mercy-ending-countdown is greater than 0

### Understand pravila (Understand rules)

Svi sinonimi za akcije:
- "saw leg" or "cut leg" or "saw ankle" as sawing leg
- "step on [something]" as stepping on plate
- "bandage myself" or "use gauze on myself" as bandaging
- "position [something]" or "move [something]" as positioning furniture
- "respond [text]" or "answer [text]" as responding to question
- "approach terminal" or "approach computer" as approaching terminal
- "code [text]" or "type [text]" or "enter [text]" as entering code
- "kill jigsaw" or "murder jigsaw" or "strangle jigsaw" as killing jigsaw
- "leave" or "walk away" as leaving jigsaw

---

## 14. DODATNI DETALJI

### Predmeti (Objects)

**Cell:**
- Rusty hand saw (ručna pila)
- Chains (lanci)
- Ceiling (strop)

**Medical Chamber:**
- Red plate (crvena ploča)
- Blue plate (plava ploča)
- Yellow plate (žuta ploča)
- Green plate (zelena ploča)
- Bloody note (krvava bilješka)
- Medical gauze (medicinska gaza)
- Medical tape (medicinski flaster)

**Observation Room:**
- Metal chair (metalna stolica)
- Filing cabinet (ormarić)
- Air vent (ventilacija)
- Monitors (monitori)

**Jaw Breaker Chamber:**
- Jaw breaker device (uređaj za čeljust)
- Metal chair (metalna stolica)
- Wall compartment (odjeljak u zidu)
- Jaw key (ključ)

**Control Room:**
- Computer terminal (kompjuterski terminal)
- Terminal screen (ekran terminala)
- Freedom door (vrata slobode)
- Revenge door (vrata osvete)

**Jigsaw's Chamber:**
- Jigsaw (osoba)
- Medical bed (medicinski krevet)
- Monitors (monitori)
- IV drips (infuzije)

### Likovi (Characters)

**Marcus (the other prisoner):**
- Može biti živ ili mrtav
- Može krvariti
- Može igrati trivia kviz
- Može pomoći u Observation Room
- Prati igrača kroz sobe

**Jigsaw:**
- Fixed in place (vezan za krevet)
- Umire od raka
- Može biti ubijen ili pošteđen
- Ima failsafe (eksplozija ako umre)

### Doors (Vrata)

1. Cell entrance (Cell ↔ Exit Hall)
2. Chamber entrance (Exit Hall ↔ Medical Chamber)
3. Chamber exit door (Medical Chamber ↔ Observation Room)
4. Observation exit door (Observation Room ↔ Dark Corridor)
5. Jaw breaker door (Dark Corridor ↔ Jaw Breaker Chamber)
6. Final corridor door (Jaw Breaker Chamber ↔ Final Corridor)
7. Final entrance door (Final Corridor ↔ Control Room)
8. Freedom door (Control Room ↔ Exit Hallway)
9. Revenge door (Control Room ↔ Jigsaw's Chamber)

---

## 15. ZAKLJUČAK I PREPORUKE

### Što je postignuto
✅ Kompletna tekstualna avantura s 10 soba  
✅ Višestruki završeci (3 glavna)  
✅ 35 zvučnih efekata  
✅ 13 slika  
✅ Kompleksne zagonetke  
✅ NPC pratilac (Marcus)  
✅ Moralni izbori  
✅ Petlje zvuka  
✅ Animirane sekvence  
✅ Brojanje pokušaja  
✅ Dinamičko otključavanje  

### Što može biti dodano (buduća proširenja)
- Više soba i zagonetki
- Više NPC likova
- Bodovni sustav
- Achievements/Trofeje
- Različiti nivoi težine
- Više završetaka (npr. Marcus preživljava i izlazi s tobom)
- Easter eggs
- Više puzzle variacija

### Preporuke za testiranje
1. Testiraj sve tri završetka
2. Testiraj sve scenarije smrti
3. Testiraj sa Marcusom i solo
4. Testiraj sve komande i sinonime
5. Provjeri da svi zvukovi i slike rade
6. Provjeri da petlje zvuka rade
7. Provjeri brojanje pokušaja

### Tehnička dokumentacija
- Inform 7 verzija: 6M62 ili novija
- Zvukovi: OGG format
- Slike: PNG format
- Kompatibilnost: Glulx interpreter

---

**Kraj priručnika**

Ovaj priručnik pokriva sve aspekte razvoja igre "Jigsaw" od početka do kraja, uključujući sve odluke, implementacije, bugfixeve i optimizacije. Služi kao kompletan vodič za razumijevanje i održavanje projekta.

**Verzija dokumenta:** 1.0 Final  
**Datum:** 14. decembar 2025  
**Linije koda:** ~2900+ linija Inform 7 koda  
**Trajanje razvoja:** Cijela sesija razgovora
