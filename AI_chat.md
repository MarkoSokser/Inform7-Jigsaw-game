
## AI POMOĆ I MENTORSTVO

Tijekom razvoja ove igre koristio sam AI asistenta (GitHub Copilot) kao mentora koji mi je pomagao razumjeti Inform 7 sintaksu, riješiti probleme i naučiti nove koncepte. U nastavku je spremljeni razgovori, pitanja i odgovora sa AI asistentom.

---

###  Razumijevanje Inform 7 sintakse

** Moje pitanje:**
> Kako mogu kreirati varijablu koja prati stanje igrača u Inform 7? Trebam pratiti je li igrač prerezao nogu i krvari li.

** AI odgovor:**
> U Inform 7, koriste se "truth state" varijable za praćenje boolean stanja. Evo kako ih možeš definirati:
> 
> ```inform7
> Player-cut is a truth state that varies.
> Player-cut is false.
> 
> Player-bleeding is a truth state that varies.  
> Player-bleeding is false.
> ```
> 
> "Truth state" je Inform 7 tip podataka koji može biti `true` ili `false`. Fraza "that varies" označava da se vrijednost može mijenjati tijekom igre. Možeš ih koristiti u uvjetima:
> 
> ```inform7
> if Player-cut is true:
>     say "Tvoja noga je odsječena.";
> ```
> 
> Za praćenje numeričkih vrijednosti poput broja turnova krvarenja, koristi:
> 
> ```inform7
> Player-bleeding-turns is a number that varies.
> Player-bleeding-turns is 0.
> ```

---

###  Implementacija Every Turn pravila

**Moje pitanje:**
> Kako mogu napraviti da se nešto događa svaki turn? Trebam da se strop spušta svaki turn dok igrač ne pobjegne ili umre.

** AI odgovor:**
> Inform 7 ima moćan mehanizam za to - "Every turn" pravila. Možeš ih koristiti ovako:
> 
> ```inform7
> Every turn when Ceiling-descending is true:
>     decrease Turns-remaining by 1;
>     if Turns-remaining is 0:
>         say "Strop te je smrskao.";
>         end the story;
>     otherwise:
>         say "Strop se spušta...";
> ```
> 
> Ključni koncepti:
> - `Every turn` se izvršava nakon svake akcije igrača
> - `when [uvjet]` filtrira kada se pravilo primjenjuje
> - `decrease X by 1` smanjuje numeričku varijablu
> - `end the story` završava igru
> 
> Savjet: Možeš imati više "Every turn" pravila s različitim uvjetima - svi aktivni će se izvršiti.

---

### Kreiranje custom akcija

**Moje pitanje:**
> Želim da igrač može napisati "saw leg" ili "cut my ankle" i da to odradi istu stvar. Kako da napravim custom akciju?

** AI odgovor:**
> Trebaš definirati novu akciju i registrirati više fraza koje je aktiviraju. Evo primjera:
> 
> ```inform7
> Cutting yourself is an action applying to nothing.
> 
> Understand "cut myself" or "cut my foot" or "cut my leg" or "cut my ankle" or 
> "saw myself" or "saw my foot" or "saw my leg" or "saw my ankle" as cutting yourself.
> ```
> 
> Objašnjenje:
> - `is an action applying to nothing` - akcija ne zahtijeva objekt
> - `Understand ... as ...` - mapira tekstualne naredbe na akciju
> - Možeš koristiti `or` za više sinonima
> 
> Za provjeru uvjeta koristi `Check`:
> ```inform7
> Check cutting yourself:
>     if the hand saw is not carried by the player:
>         say "Nemaš čime to napraviti." instead.
> ```
> 
> Za izvršenje koristi `Carry out`:
> ```inform7
> Carry out cutting yourself:
>     now Player-cut is true;
>     say "Prerezao si nogu...";
> ```

---

###  Zvukovi i slike

**Moje pitanje:**
> Kako mogu dodati zvukove u igru? Želim da se čuje zvuk rezanja kad igrač reže nogu.

** AI odgovor:**
> Inform 7 podržava multimediju kroz Glulx format. Evo koraka:
> 
> **1. Definiraj zvuk:**
> ```inform7
> Sound of SelfCut is the file "self_cut.ogg".
> ```
> 
> **2. Reproduciraj zvuk:**
> ```inform7
> play the sound of SelfCut;
> ```
> 
> **Za slike:**
> ```inform7
> Figure of CutLegImage is the file "cut_leg.png".
> display the Figure of CutLegImage;
> ```
> 
> Napomene:
> - Datoteke moraju biti u "Figures" i "Sounds" folderima projekta
> - OGG format je preporučen za zvukove (bolja kompresija od WAV-a)
> - PNG za slike (podržava transparenciju)
> - Igra mora biti kompajlirana za Glulx, ne Z-machine

---

###  NPC praćenje igrača

**Moje pitanje:**
> Imam NPC-a Marcusa kojeg igrač može vući kroz sobe. Kako implementirati da Marcus slijedi igrača?

** AI odgovor:**
> Možeš koristiti "Before going" pravilo da premjestiš NPC-a kada igrač mijenja sobu:
> 
> ```inform7
> The other prisoner can be being-dragged or not-dragged.
> The other prisoner is not-dragged.
> 
> Before going through the cell exit door:
>     if the other prisoner is being-dragged:
>         now the other prisoner is in the Exit Hall.
> ```
> 
> Za generičko praćenje kroz sve sobe:
> ```inform7
> After going when the other prisoner is being-dragged:
>     if the other prisoner is alive:
>         now the other prisoner is in the location;
>         say "Vučeš Marcusa za sobom.";
> ```
> 
> Savjet: Koristi "After going" umjesto "Before going" ako želiš da se NPC pojavi NAKON što igrač stigne u novu sobu, što je prirodnije za naraciju.

---

### Debugiranje - Greška s varijablama

**Moje pitanje:**
> Dobivam grešku "I was expecting a condition here" kad pokušam provjeriti `if Player-cut:`. Što radim krivo?

** AI odgovor:**
> U Inform 7, moraš eksplicitno usporediti truth state s `true` ili `false`. Ovo neće raditi:
> 
> ```inform7
> if Player-cut:  [GREŠKA!]
> ```
> 
> Ispravan način:
> ```inform7
> if Player-cut is true:
>     [...]
> ```
> 
> Inform 7 nije kao Python ili JavaScript gdje je boolean direktno uvjet. Uvijek koristi `is true`, `is false`, ili za negaciju `is not true`.
> 
> Isto vrijedi za provjeru objekata:
> ```inform7
> if the other prisoner is conscious:  [OK - jer je "conscious" definirano stanje]
> if the other prisoner is bleeding:   [OK]
> ```

---

### Višestruki završeci igre

**Moje pitanje:**
> Kako mogu napraviti različite završetke igre ovisno o odlukama igrača? Želim "Revenge", "Mercy" i "Freedom" ending.

** AI odgovor:**
> Inform 7 ima nekoliko načina za završetak igre s različitim porukama:
> 
> **Osnovni završeci:**
> ```inform7
> end the story;                           [Neutralan kraj]
> end the story finally;                   [Definitivan kraj]
> end the story saying "You escaped!";     [Custom poruka]
> ```
> 
> **Za tvoje završetke:**
> ```inform7
> [Revenge ending - igrač ubija Jigsawa]
> end the story saying "REVENGE - You killed him, but at what cost?";
> 
> [Mercy ending - igrač štedi Jigsawa]  
> end the story saying "MERCY - You chose forgiveness over vengeance.";
> 
> [Freedom ending - igrač jednostavno izlazi]
> end the story saying "FREEDOM - You escaped. The nightmare is over.";
> ```
> 
> Savjet: Koristi varijable za praćenje odluka kroz igru:
> ```inform7
> Jigsaw-spared is a truth state that varies.
> Marcus-alive is a truth state that varies.
> ```
> Pa na kraju provjeri sve uvjete za određivanje najboljeg završetka.

---

### Trivia kviz implementacija

**Moje pitanje:**
> Kako napraviti trivia kviz gdje igrač mora odgovoriti na pitanja, a ako pogriješi 3 puta, umire?

** AI odgovor:**
> Trebaš kombinirati nekoliko tehnika - praćenje stanja, custom akcije i logiku brojanja:
> 
> ```inform7
> Trivia-wrong-answers is a number that varies.
> Trivia-wrong-answers is 0.
> 
> Trivia-correct-answers is a number that varies.
> Trivia-correct-answers is 0.
> 
> Current-question is a number that varies.
> Current-question is 1.
> ```
> 
> **Akcija za odgovor:**
> ```inform7
> Responding is an action applying to one topic.
> Understand "respond [text]" or "answer [text]" or "say [text]" as responding.
> 
> Carry out responding when the location is Jaw Breaker Chamber:
>     if Current-question is 1:
>         if the topic understood matches "paris":
>             increment Trivia-correct-answers;
>             say "Točno!";
>         otherwise:
>             increment Trivia-wrong-answers;
>             say "Netočno!";
>     [provjeri za smrt ili pobjedu]
>     if Trivia-wrong-answers is 3:
>         say "Jaw breaker se aktivira...";
>         end the story;
>     if Trivia-correct-answers is 3:
>         say "Prošao si test!";
>         [otključaj vrata]
> ```
> 
> Ključno je koristiti `topic` tip za slobodan unos teksta i `matches` za usporedbu.

---

### Problem sa spuštajućim stropom

**Moje pitanje:**
> Strop se spušta čak i nakon što igrač pobjegne iz ćelije. Kako zaustaviti Every turn pravilo?

** AI odgovor:**
> Moraš eksplicitno isključiti uvjet koji aktivira pravilo. Imaš `Ceiling-descending` varijablu - jednostavno je postavi na `false` kad igrač pobjegne:
> 
> ```inform7
> Instead of going through the cell exit door:
>     now Ceiling-descending is false;  [KLJUČNO - zaustavlja strop]
>     now the cell exit door is collapsed;
>     say "Bacaš se kroz vrata dok se strop ruši iza tebe.";
>     continue the action.
> ```
> 
> Sada će `Every turn when Ceiling-descending is true:` prestati s izvršavanjem jer je uvjet `false`.
> 
> Ovaj pattern koristi za sve "timed" mehanike - uvijek imaj boolean koji možeš isključiti.

---

### Death Delay sistem

**Moje pitanje:**
> Kad igrač umre, želim dramatičnu pauzu prije nego što se igra završi. Kako to napraviti?

** AI odgovor:**
> Možeš implementirati "death countdown" sistem. Umjesto da odmah završiš igru, odgodi završetak za par turnova:
> 
> ```inform7
> Death-countdown is a number that varies.
> Death-countdown is 0.
> 
> Death-type is a text that varies.
> Death-type is "".
> ```
> 
> **Kad igrač umre (umjesto direktnog završetka):**
> ```inform7
> [Umjesto: end the story;]
> now Death-countdown is 2;
> now Death-type is "ceiling";
> ```
> 
> **Handler:**
> ```inform7
> Every turn when Death-countdown is greater than 0:
>     decrease Death-countdown by 1;
>     if Death-countdown is 1:
>         say "[paragraph break][bold type]*** Press any key ***[roman type]";
>     otherwise if Death-countdown is 0:
>         end the story;
> ```
> 
> Ovo daje igraču turn da vidi poruku o smrti, pa tek onda završava igru. Možeš prilagoditi broj turnova pauze.

---

###  Korištenje ekstenzija

**Moje pitanje:**
> Čuo sam za ekstenzije u Inform 7. Kako mogu dodati help meni u igru?

** AI odgovor:**
> Inform 7 ima bogat ekosustav ekstenzija. Za help meni, preporučujem "Basic Help Menu by Emily Short":
> 
> **1. Uključi ekstenziju:**
> ```inform7
> Include Basic Help Menu by Emily Short.
> ```
> 
> **2. Definiraj sadržaj:**
> ```inform7
> Table of Basic Help Options
> title	description
> "Movement"	"Use N, S, E, W or NORTH, SOUTH, EAST, WEST to move."
> "Interaction"	"LOOK, EXAMINE [object], TAKE [object], USE [object]"
> "Special"	"SAW LEG, BANDAGE MYSELF, RESPOND [answer]"
> ```
> 
> **3. Igrač koristi:**
> ```
> > HELP
> [Prikazuje se meni]
> ```
> 
> Druga korisna ekstenzija je "Basic Screen Effects by Emily Short" za:
> - `wait for any key` - pauza do pritiska tipke
> - `clear the screen` - čisti ekran
> 
> Ekstenzije se automatski preuzimaju s Inform 7 websitea.

---

###  Dinamički opisi objekata

**Moje pitanje:**
> Kako mogu napraviti da se opis NPC-a mijenja ovisno o stanju (živ, mrtav, krvari, zavijen)?

** AI odgovor:**
> Koristi inline uvjete unutar opisa s `[if]` strukturom:
> 
> ```inform7
> The description of the other prisoner is
> "[if the other prisoner is in the Cell]Čovjek leži prikovan pokraj tebe, 
> bez svijesti.[otherwise if the other prisoner is bleeding]Marcus krvari! 
> Krv se širi po podu.[otherwise if the other prisoner is bandaged]Marcus 
> leži zavijen. Disanje mu je plitko ali stabilno.[otherwise]Marcus leži 
> nepomično na podu.[end if]".
> ```
> 
> Ovo omogućava jedan opis koji se dinamički prilagođava stanju. Možeš kombinirati više uvjeta:
> 
> ```inform7
> "[if conscious and bandaged]Marcus te gleda zahvalno.[end if]"
> ```
> 
> Savjet: Za kompleksne opise, definiraj "To say" fraze:
> ```inform7
> To say prisoner-status:
>     if bleeding, say "krvari";
>     if bandaged, say "je zavijen";
>     [...]
> ```

