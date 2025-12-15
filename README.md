# Inform7-Jigsaw-game

**"Saw Escape Room"** - Interaktivna tekstualna avantura inspirirana Saw filmovima

## 📖 O igri

"Saw Escape Room" je mračna, intenzivna tekstualna avantura gdje se igrač budi zarobljen u nizu smrtonosnih soba. Svaka soba predstavlja test - fizički, mentalni ili moralni. Svaka odluka ima posljedice. Hoćete li preživjeti?

### Tema i atmosfera
-  **Horror survival** - Napetost i strah u svakom koraku
-  **Moralni izbori** - Odluke koje definiraju vašu žrtvu ili žrtvovanje drugih
-  **Logičke zagonetke** - Razmišljanje pod pritiskom
-  **Saw inspired** - Autentična atmosfera filmske franšize

### Karakteristike
-  **Jedinstvene sobe** sa različitim izazovima
-  **Različiti završeci** ovisno o vašim odlukama
-  **Zvučni efekati** za potpunu atmosferu
-  **Slike** koje vizualiziraju scene
-  **NPC pratilac (Marcus)** - hoće li preživjeti ovisi o vama
-  **Višestruki scenariji smrti** - svaka pogreška je fatalna
-  **Kompleksne zagonetke** - od colour plates do trivia kvizova
-  **In-game help sistem** - HELP komanda za sve komande

---

## 🎮 Kako igrati

### Osnovne komande

**Kretanje:**
- `north` / `n` - Idi na sjever
- `south` / `s` - Idi na jug
- `east` / `e` - Idi na istok
- `west` / `w` - Idi na zapad

**Interakcija:**
- `look` / `l` - Pogledaj oko sebe
- `examine [objekt]` / `x [objekt]` - Detaljno pregledaj objekt
- `take [objekt]` - Uzmi objekt
- `use [objekt]` - Koristi objekt
- `inventory` / `i` - Provjeri svoj inventar

**Pomoć:**
- `help` - Prikaži kompletan spisak komandi
- `about` - Informacije o igri

**Napredne akcije:**
- `saw leg` - Prereži nogu (Cell)
- `bandage myself` - Zavoj sebi ranu (Medical Chamber)
- `step on [color] plate` - Stani na određenu ploču (Medical Chamber)
- `respond [answer]` - Odgovori na pitanje (Observation Room / Jaw Breaker)
- `code [text]` - Upiši kod (Control Room)
- `kill jigsaw` / `leave` - Odluči Jigsawovu sudbinu

---

## 💾 Instalacija i pokretanje

### Preuzimanje

1. **Preuzmite cijeli projekt:**
   ```bash
   git clone https://github.com/[username]/Inform7-Jigsaw-game.git
   cd Inform7-Jigsaw-game
   ```

2. **Ili preuzmite ZIP:**
   - Idite na GitHub repository
   - Kliknite "Code" → "Download ZIP"
   - Raspakirajte na željenu lokaciju

### Potrebni alati

**Inform 7 IDE:**
- Preuzmite sa: https://ganelson.github.io/inform-website/
- Verzija: 6M62 ili novija
- Platforme: Windows, macOS, Linux

**Alternativno - Online:**
- Možete koristiti online Inform 7 editor na https://inform7.com/

### Kompajliranje igre

1. **Otvorite Inform 7 IDE**
2. **Otvorite projekat:**
   - File → Open → Odaberite folder `Inform7-Jigsaw-game`
3. **Kompajlirajte:**
   - Kliknite "Go!"  (ili Ctrl+G / Cmd+G)
   - Igra će se automatski kompajlirati u Glulx format
4. **Igrajte:**
   - Nakon uspješnog kompajliranja, igra će se automatski pokrenuti u interpreteru

### Release verzija

Za kreiranje release verzije:
1. U Inform 7 IDE, idite na: Release → Release
2. Odaberite opcije:
   -  Release along with an interpreter
   -  Release along with a website
3. Release će biti kreiran u `[project]/Build/Output/` folderu

---

## 🔧 Tehnički detalji

### Korištene tehnologije
- **Engine:** Inform 7 (6M62)
- **Format:** Glulx
- **Ekstenzije:** 
  - Basic Help Menu by Emily Short
  - Basic Screen Effects by Emily Short

### Kompatibilnost
-  Windows (Inform 7 IDE, Gargoyle, Windows Glulx)
-  macOS (Inform 7 IDE, Gargoyle)
-  Linux (Inform 7 IDE, Gargoyle)
-  Web (može se igrati u browseru putem Quixe interpretera)

## 🎮 Brzi start

```bash
# 1. Preuzmite projekat
git clone https://github.com/[username]/Inform7-Jigsaw-game.git

# 2. Otvorite u Inform 7 IDE
# File → Open → Odaberite folder projekta

# 3. Kompajlirajte i igrajte
# Kliknite "Go!" (Ctrl+G)

# 4. Uživajte u igri!
# Unesite: HELP za listu komandi
```

---

**⚠️ UPOZORENJE:** Igra sadrži grafičke opise nasilja, torture i smrti. Preporučeno za publiku 18+ godina.