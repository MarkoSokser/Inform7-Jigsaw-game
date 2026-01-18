# Inform7-Jigsaw-game

**"Saw Escape Room"** - Interaktivna tekstualna avantura inspirirana Saw filmovima

## O igri

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

## Kako igrati

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

## Instalacija i pokretanje

### Preuzimanje

1. **Preuzmite cijeli projekt:**
   ```bash
   git clone https://github.com/MarkoSokser/Inform7-Jigsaw-game.git
   cd Inform7-Jigsaw-game
   ```

2. **Ili preuzmite ZIP:**
   - Idite na GitHub repository
   - Kliknite "Code" → "Download ZIP"
   - Raspakirajte na željenu lokaciju

3. **Preporučeno - Release verzija:**
   - Preuzmite folder `Jigsaw_game_relese`
   - Sadrži već kompajliranu igru spremnu za igranje

### Potrebni alati

#### Za igranje (Release verzija):

**Glulx Interpreter:**
- **Windows:** Windows Glulx ili Gargoyle (https://ccxvii.net/gargoyle/)
- **macOS:** Gargoyle ili Spatterlight
- **Linux:** Gargoyle
- **Web browser:** Otvorite `Jigsaw_game_relese/Saw Escape Room.materials/Release/index.html`

#### Za razvoj/modifikaciju (opciono):

**Inform 7 IDE:**
- Preuzmite sa: https://ganelson.github.io/inform-website/
- Verzija: 6M62 ili novija
- Platforme: Windows, macOS, Linux

### Pokretanje igre

#### Metoda 1: Web browser (najlakše)

1. Navigirajte do foldera `Jigsaw_game_relese/Saw Escape Room.materials/Release/`
2. Dvostruki klik na `index.html`
3. Igra će se pokrenuti u vašem web browseru

#### Metoda 2: Standalone Interpreter

1. Instalirajte Glulx interpreter (npr. Gargoyle)
2. Otvorite fajl:
   - `Jigsaw_game_relese/Saw Escape Room.materials/Release/Saw Escape Room.gblorb`
   - Ili `Jigsaw_game_relese/Saw Escape Room.inform/Build/output.gblorb`
3. Igra će se pokrenuti u interpreteru

#### Metoda 3: Inform 7 IDE (za developere)

1. **Otvorite Inform 7 IDE**
2. **Otvorite projekat:**
   - File → Open
   - Odaberite folder `Jigsaw_game_relese/Saw Escape Room.inform`
3. **Igrajte postojeću verziju:**
   - Release → Play in Browser
   - Ili kliknite "Go!" za kompajliranje i igranje
4. **Za modifikaciju:**
   - Source tab sadrži `story.ni` sa izvornim kodom
   - Nakon izmjena kliknite "Go!" za rekompajliranje

---

##  Tehnički detalji

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

##  Brzi start

### Opcija 1: Instant Play (Web Browser)
```bash
# 1. Preuzmite projekat
git clone https://github.com/MarkoSokser/Inform7-Jigsaw-game.git

# 2. Navigirajte do release foldera
cd "Jigsaw_game_relese/Saw Escape Room.materials/Release"

# 3. Otvorite index.html u browseru
start index.html  # Windows
# open index.html  # macOS
# xdg-open index.html  # Linux

# 4. Uživajte u igri!
# Unesite: HELP za listu komandi
```

### Opcija 2: Standalone Interpreter
```bash
# 1. Preuzmite i instalirajte Gargoyle/Glulx interpreter

# 2. Otvorite fajl:
# Jigsaw_game_relese/Saw Escape Room.materials/Release/Saw Escape Room.gblorb

# 3. Igrajte!
```

---

** UPOZORENJE:** Igra sadrži grafičke opise nasilja, torture i smrti. Preporučeno za publiku 18+ godina.
