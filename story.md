"Saw Escape Room" by "Marko Sokser"

Release along with an interpreter.
Release along with a website.

Chapter 1 - Global Game States

Game-started is a truth state that varies.
Game-started is false.

Ceiling-descending is a truth state that varies.
Ceiling-descending is false.

Ceiling-pending is a truth state that varies.
Ceiling-pending is false.

Turns-remaining is a number that varies.
Turns-remaining is 6.

Player-cut is a truth state that varies.
Player-cut is false.

Player-bleeding is a truth state that varies.
Player-bleeding is false.

Player-bandaged is a truth state that varies.
Player-bandaged is false.

Player-bleeding-turns is a number that varies.
Player-bleeding-turns is 0.

Prisoner-cut is a truth state that varies.
Prisoner-cut is false.



Chapter 1b - Sounds

Sound of TapeVoice is the file "tape.ogg".
Sound of ButtonPress is the file "button_press.ogg".
Sound of CeilingMove is the file "ceiling_move.ogg".
Sound of SelfCut is the file "self_cut.ogg".
Sound of NPCCut is the file "npc_cut.ogg".
Sound of DeathCrush is the file "death_crush.ogg".
Sound of Idea is the file "idea.ogg".
Sound of PuzzleActivate is the file "puzzle_activate.ogg".
Sound of Bleeding is the file "bleeding.ogg".
Sound of WoundClose is the file "wound_close.ogg".
Sound of PrisonerWake is the file "prisoner_wake.ogg".
Sound of TrapFail is the file "trap_fail.ogg".
Sound of PlateRed is the file "plate_red.ogg".
Sound of PlateBlue is the file "plate_blue.ogg".
Sound of PlateYellow is the file "plate_yellow.ogg".
Sound of PlateGreen is the file "plate_green.ogg".
Sound of Screaming is the file "screaming.ogg".
Sound of GameOver is the file "gameover.ogg".
Sound of BodyFall is the file "body_fall.ogg".
Sound of GameOverMusic is the file "game_over_music.ogg".
Sound of JigsawVoice is the file "game.ogg".
Sound of SawTrap is the file "saw.ogg".
Sound of ChairMove is the file "chair.ogg".
Sound of Pressure is the file "pressure.ogg".
Sound of GameOver2 is the file "gameover2.ogg".
Sound of AdamCare is the file "care.ogg".
Sound of JawBreaker is the file "jaw_breaker.ogg".
Sound of GasRelease is the file "gas.ogg".
Sound of SadMusic is the file "sad.ogg".



Chapter 2 - The World

The Cell is a room.

The description of the Cell is
"You wake up strapped to a rusted metal bed in a filthy concrete cell.  
A heavy iron shackle locks your ankle in place, connected by a thick chain to another body nearby.  
Dark stains cover the floor beneath you, old and dried.  
The air reeks of metal, mold, and something far worse.  

There are no windows.  
No mercy.  
Only waiting.";

After looking in the Cell:
	say "[paragraph break]You can see:";
	if the other prisoner is in the Cell:
		say "[line break]- The unconscious man chained beside you";
	if the chain is in the Cell:
		say "[line break]- The heavy iron chain binding you both";
	if the glowing button is in the Cell:
		say "[line break]- A glowing button on the wall";
	if the hand saw is in the Cell:
		say "[line break]- A rusty hand saw";
	if the cell exit door is revealed:
		say "[line break]- An exit door to the north".

The Exit Hall is a room.
The description of the Exit Hall is
"A narrow concrete corridor stretches into darkness.
The air is colder here, heavier.
Whatever comes next, you have left the cell behind.

To the north, you can see a heavy metal door marked with biohazard symbols.
Behind it, you hear the faint hum of fluorescent lights.".

Rule for listing nondescript items when the location is the Exit Hall:
	if the cell exit door is marked for listing:
		now the cell exit door is not marked for listing;
	if the other prisoner is marked for listing:
		now the other prisoner is not marked for listing.

After looking in the Exit Hall:
	if the other prisoner is in the Exit Hall:
		say "[paragraph break]Marcus lies unconscious on the cold concrete floor, his bandaged ankle still seeping blood.".

The Medical Chamber is a room.

The medical chamber entrance door is a door.
The medical chamber entrance door is north of the Exit Hall and south of the Medical Chamber.
The medical chamber entrance door is open and unlocked.

The description of the medical chamber entrance door is "A heavy metal door marked with biohazard symbols. [if open]It stands open, leading into the medical chamber[otherwise]It is closed[end if].".

The description of the Medical Chamber is
"You step into what appears to be an abandoned operating room.
Rusted surgical tools hang from racks on blood-stained walls.
A massive examination table dominates the center, covered in leather restraints.
The floor is slick with something dark and viscous.

Three glass cylinders stand against the far wall, each containing a severed limb suspended in murky fluid.
Above them, a digital counter reads: 'SPECIMENS: 3 / 6'

The walls are lined with cabinets, some open, revealing medical supplies in various states of decay.

To the east, you can see a heavy metal door with a complex locking mechanism.".

Rule for listing nondescript items when the location is the Medical Chamber:
	if the other prisoner is marked for listing:
		now the other prisoner is not marked for listing.

After looking in the Medical Chamber:
	if the other prisoner is in the Medical Chamber:
		say "[paragraph break][description of the other prisoner]";
	if Puzzle-activated is true:
		say "[paragraph break]Four colored pressure plates (RED, BLUE, GREEN, and YELLOW) glow ominously on the floor near the chamber exit door.";
	if the bloody note is in the Medical Chamber:
		say "[paragraph break]You can see a bloody note on the floor.".

The Observation Room is a room.
The Observation Room is east of the chamber exit door.

The description of the Observation Room is
"You step into what appears to be a surveillance room.
The walls are lined with cracked monitors, most displaying nothing but static.
A few still flicker with grainy footage of empty corridors and cells.

High on the far wall, thin beams of light pierce through an air vent grate.
The light draws your attention upward - freedom might lie beyond that vent.

A metal chair sits in the corner, and a filing cabinet stands against the wall.

The room feels claustrophobic, as if it's watching you back.".

The air vent is scenery in the Observation Room.
The air vent is fixed in place.
The description of the air vent is "High on the far wall, approximately 3 meters up, an air vent grate allows thin beams of light to pierce through. The vent looks like it could be large enough to crawl through - if you could reach it. [if Chair-positioned is true and Cabinet-positioned is true]The chair stacked on the cabinet creates a makeshift ladder that might allow you to reach the vent[otherwise if Chair-positioned is true]The chair is positioned beneath it, but it's not tall enough on its own[otherwise if Cabinet-positioned is true]The cabinet is positioned beneath it, but you'd need something else to boost yourself higher[otherwise]You'll need to position furniture beneath it to have any chance of reaching it[end if]."

Understand "vent" or "grate" or "vent grate" or "air vent grate" as the air vent.

The metal chair is a thing in the Observation Room.
The metal chair can be positioned-under-vent or not-positioned.
The metal chair is not-positioned.
The description of the metal chair is "A sturdy metal chair with a welded frame. [if Chair-positioned is true]It's currently positioned directly beneath the air vent[otherwise]It looks heavy but movable[end if]."

Understand "chair" or "sturdy chair" as the metal chair.

The filing cabinet is a thing in the Observation Room.
The filing cabinet can be positioned-under-vent or not-positioned.
The filing cabinet is not-positioned.
The description of the filing cabinet is "A heavy metal filing cabinet, about waist-high. [if Cabinet-positioned is true]It's positioned beneath the air vent[otherwise]Its weight makes it difficult to move, but not impossible[end if]."

Understand "cabinet" or "metal cabinet" as the filing cabinet.



Chapter 3 - The Other Prisoner

The other prisoner is a man in the Cell.
The other prisoner is fixed in place.

The other prisoner can be conscious or unconscious.
The other prisoner is unconscious.

The other prisoner can be bleeding or not-bleeding.
The other prisoner is not-bleeding.

The other prisoner can be bandaged or unbandaged.
The other prisoner is unbandaged.

The other prisoner can be alive or dead.
The other prisoner is alive.

Prisoner-bleeding-turns is a number that varies.
Prisoner-bleeding-turns is 0.

The description of the other prisoner is
"[if the other prisoner is in the Cell]A man is chained beside you, his body limp and unnaturally still. His head hangs to one side. His breathing is shallow, barely noticeable.[otherwise if the other prisoner is in the Exit Hall][prisoner-name] lies unconscious on the cold concrete floor, his bandaged ankle still seeping blood.[otherwise if the other prisoner is in the Medical Chamber and the other prisoner is conscious][prisoner-name] sits against the wall, clutching his bandaged ankle. His face is pale but his eyes are alert, watching you with a mixture of fear and gratitude.[otherwise if the other prisoner is in the Medical Chamber and the other prisoner is bandaged][prisoner-name] lies unconscious on the chamber floor. His ankle is bandaged, and the bleeding has stopped. His breathing is shallow but stable.[otherwise if the other prisoner is in the Medical Chamber and the other prisoner is bleeding][prisoner-name] lies on the blood-slicked floor, unconscious. Blood pools rapidly beneath his severed ankle. He's dying![otherwise][prisoner-name] lies motionless on the floor.[end if]".

After examining the other prisoner when the other prisoner is bleeding and the other prisoner is unbandaged and the other prisoner is in the Medical Chamber:
	say "[paragraph break]BLOOD is pooling beneath his severed ankle. He is losing a lot of blood quickly!".

The other prisoner can be introduced or unintroduced.
The other prisoner is unintroduced.

Understand "man" or "prisoner" or "other man" or "marcus" as the other prisoner.

The printed name of the other prisoner is "[if introduced]Marcus[otherwise]man[end if]".

To say prisoner-name:
	if the other prisoner is introduced:
		say "Marcus";
	otherwise:
		say "The man".
		
To say prisoner-name-possessive:
	if the other prisoner is introduced:
		say "Marcus's";
	otherwise:
		say "The man's".



Chapter 4 - Checking If He Is Alive

Checking life is an action applying to one thing.
Understand "check [someone]" or "check if [someone] is alive" or
"check breathing of [someone]" as checking life.

Check checking life:
	if the noun is not the other prisoner:
		say "That tells you nothing useful." instead.

Carry out checking life:
	say "You force yourself to watch his chest.  
After several agonizing seconds, it rises slightly.  
He is alive.";


Chapter 5 - Trying to Wake Him

Trying to wake is an action applying to one thing.
Understand "wake [someone]" or "wake up [someone]" or
"shake [someone]" as trying to wake.

Check trying to wake:
	if the noun is not the other prisoner:
		say "That accomplishes nothing." instead;
	if the other prisoner is conscious:
		say "He's already awake." instead;
	if the other prisoner is dead:
		say "He's dead. He won't wake up." instead.

Carry out trying to wake:
	if the other prisoner is in the Cell:
		say "You grab his shoulder and shake him hard.  
His body reacts, but his eyes never open.
Whatever they injected into him has left him completely helpless.";
	otherwise if the other prisoner is bandaged and the other prisoner is in the Medical Chamber:
		now the other prisoner is conscious;
		now the other prisoner is introduced;
		play the sound of PrisonerWake;
		say "You shake his shoulder firmly, calling out to him.
His eyes suddenly flutter open. He gasps, looking around in confusion and pain.
'What... where am I?' he croaks, his voice hoarse.
He looks down at his bandaged ankle and then at you.
'You... you saved me. I thought I was going to die in that cell.'";
	otherwise if the other prisoner is bleeding:
		say "You shake him desperately, but he doesn't respond.
He's losing too much blood. You need to stop the bleeding before worrying about waking him!";
	otherwise:
		say "You shake him, but there's no response.".


Chapter 6 - The Chain

The chain is a thing in the Cell.
The chain is fixed in place.

The description of the chain is
"The heavy iron chain binds you to the other prisoner.  
Each of you wears a tight ankle shackle, far too small to slip free.  

The chain passes through an iron bar embedded in the wall.  
There is no way to pull a body through it.  
This was engineered with precision.";


Chapter 7 - The Glowing Button

The glowing button is a device in the Cell.
The glowing button is fixed in place.

The description of the glowing button is
"A circular metal button embedded in the wall beside you.  
It pulses faintly, as if aware of your hesitation.";


Chapter 8 - Objects That Appear Later

The hand saw is a thing.
The hand saw is nowhere.

The cell exit door is a door.
The cell exit door is north of the Cell and south of the Exit Hall.
The cell exit door is closed and unlocked.

To say cell door status:
	if the cell exit door is collapsed:
		say "The ceiling has crushed it completely, blocking any return";
	otherwise if the cell exit door is open:
		say "It stands open";
	otherwise:
		say "It stands closed".

The description of the cell exit door is "A heavy steel door that led out of your cell. [cell door status].".

The cell exit door can be revealed or unrevealed.
The cell exit door is unrevealed.

The cell exit door can be collapsed or standing.
The cell exit door is standing.

Rule for listing nondescript items when the cell exit door is unrevealed:
	if the cell exit door is marked for listing:
		now the cell exit door is not marked for listing.

Report opening the cell exit door:
	do nothing instead.


Chapter X - Hidden Exit

Instead of going north from the Cell when the cell exit door is unrevealed:
	say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going south from the Cell when the cell exit door is unrevealed:
		say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going west from the Cell when the cell exit door is unrevealed:
		say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going east from the Cell when the cell exit door is unrevealed:
		say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".




Chapter 9 - Pressing the Button

Instead of pushing the glowing button:
	if Game-started is true:
		say "The button is dead.";
	otherwise:
		now Game-started is true;
		now Ceiling-pending is true;
		now Turns-remaining is 6;
		now the hand saw is in the Cell;
		now the cell exit door is revealed;
		say "You press the button.[paragraph break]";
		play the sound of ButtonPress;
		say "[paragraph break]A section of the far wall collapses, revealing a heavy metal door.";
		say "[paragraph break]A rusty hand saw falls from the ceiling, landing between you and the unconscious man.".



Chapter 9b - Ceiling Activation

Every turn when Ceiling-pending is true:
	now Ceiling-pending is false;
	now Ceiling-descending is true;
	play the sound of CeilingMove;
	say "[paragraph break]Hidden machinery roars to life inside the walls.";
	say "The ceiling shudders — then begins to descend.".





Chapter 10 - The Descending Ceiling

Every turn when Ceiling-descending is true:
	decrease Turns-remaining by 1;
	if Turns-remaining is 0:
		play the sound of DeathCrush;
		say "[paragraph break]The ceiling comes down with terrible finality.";
		say "There is no escape.";
		say "[paragraph break]Everything goes black.";
		end the story;
	otherwise:
		say "The ceiling grinds lower, showering you with dust and fragments of concrete.".




Chapter 12 - Cutting Yourself Free

Cutting yourself is an action applying to nothing.
Understand "cut myself" or "cut my foot" or "cut my leg" or "cut my ankle" or 
"saw myself" or "saw my foot" or "saw my leg" or "saw my ankle" or
"saw yourself" or "cut yourself" as cutting yourself.

Check cutting yourself:
	if the hand saw is not carried by the player:
		say "You have nothing to do that with." instead.


Carry out cutting yourself:
	now the chain is nowhere;
	now Player-cut is true;
	display the Figure of CutLegImage;
	play the sound of SelfCut;
	say "You bite down and force the saw through bone and flesh.
The pain is indescribable.
You collapse - but the chain falls away.".




Chapter 12b - Trying to Cut the Chain

Cutting the chain is an action applying to one thing.
Understand "cut [thing]" or "cut through [thing]" or "saw [thing]" or "saw through [thing]" as cutting the chain when the noun is not a person.

Check cutting the chain:
	if the noun is not the chain:
		say "That's not something you can cut." instead;
	if the hand saw is not carried by the player:
		say "You have nothing to cut with." instead.

Carry out cutting the chain:
	play the sound of Idea;
	say "You press the blade against the thick iron chain and start sawing desperately.

The metal barely scratches.

The chain is far too thick. There isn't enough time.".



Chapter 13 - Cutting the Other Prisoner Free

Cutting the prisoner is an action applying to one thing.
Understand "cut [someone]" or "cut [someone] free" or "cut foot of [someone]" or "cut leg of [someone]" or 
"cut ankle of [someone]" or "saw [someone]" or "saw [someone] free" or "saw foot of [someone]" or 
"saw leg of [someone]" or "saw ankle of [someone]" as cutting the prisoner.

Check cutting the prisoner:
	if the noun is not the other prisoner:
		say "That would achieve nothing." instead;
	if the hand saw is not carried by the player:
		say "You have nothing to cut with." instead.

Carry out cutting the prisoner:
	now the chain is nowhere;
	now Prisoner-cut is true;
	play the sound of NPCCut;
	say "You saw through his ankle.
His body jerks violently, but he remains unconscious.
The chain finally drops.".



Chapter 13b - Dragging the Prisoner

The other prisoner can be being-dragged or not-dragged.
The other prisoner is not-dragged.

Dragging is an action applying to one thing.
Understand "save [someone]" or "drag [someone]" or 
"pull [someone]" or "carry [someone]" as dragging.

Check dragging:
	if the noun is not the other prisoner:
		say "That makes no sense." instead;
	if Player-cut is true and Player-bleeding is true:
		say "You are losing too much blood. You can barely stand.
You don't have the strength to drag him.
You need to stop your bleeding first!" instead;
	if Player-cut is true and Player-bandaged is false:
		say "You are weak from blood loss. You can barely stand.
You don't have the strength to drag him." instead;
	if Prisoner-cut is false:
		say "He is still chained. You cannot move him." instead.

Carry out dragging:
	now the other prisoner is being-dragged;
	say "You grab him under the arms and begin dragging his limp body.
Every second counts.".




Chapter 14 - Endings

Instead of going through the cell exit door when the chain is in the Cell:
	say "The chain prevents you from reaching the door.".

Before going through the cell exit door:
	if the other prisoner is being-dragged:
		now the other prisoner is in the Exit Hall.

Instead of going through the cell exit door:
	now Ceiling-descending is false;
	now the cell exit door is collapsed;
	if the other prisoner is being-dragged:
		say "You throw yourself through the doorway, dragging him with you, as the ceiling crashes down behind you.";
		say "You both survived - at a terrible cost.";
	otherwise:
		say "You throw yourself through the doorway as the ceiling crashes down behind you.";
		say "You survived - at a terrible cost.";
	continue the action.

Instead of going south from the Exit Hall when the cell exit door is collapsed:
	say "The ceiling has completely collapsed. There is no way back.".




Chapter 1c - Medical Chamber State Variables

Chamber-turns-elapsed is a number that varies.
Chamber-turns-elapsed is 0.

Puzzle-activated is a truth state that varies.
Puzzle-activated is false.

Player-lost-limb is a truth state that varies.
Player-lost-limb is false.

Limb-type is text that varies.
Limb-type is "".

Medical-supplies-used is a number that varies.
Medical-supplies-used is 0.

Player-wrist-bleeding is a truth state that varies.
Player-wrist-bleeding is false.

Player-wrist-bleeding-turns is a number that varies.
Player-wrist-bleeding-turns is 0.

Observation-room-trap-activated is a truth state that varies.
Observation-room-trap-activated is false.

Chair-positioned is a truth state that varies.
Chair-positioned is false.

Cabinet-positioned is a truth state that varies.
Cabinet-positioned is false.

Player-hands-trapped is a number that varies.
Player-hands-trapped is 0.

Question-asked is a truth state that varies.
Question-asked is false.

Player-answered is a truth state that varies.
Player-answered is false.

Marcus-betrayed is a truth state that varies.
Marcus-betrayed is false.

Player-confessed is a truth state that varies.
Player-confessed is false.

Solo-escape-turns is a number that varies.
Solo-escape-turns is 0.

Betrayal-dying is a truth state that varies.
Betrayal-dying is false.

Betrayal-death-turns is a number that varies.
Betrayal-death-turns is 0.

Last-hand-dying is a truth state that varies.
Last-hand-dying is false.

Last-hand-death-turns is a number that varies.
Last-hand-death-turns is 0.

Solo-arm-trap-turns is a number that varies.
Solo-arm-trap-turns is 0.




Chapter 16 - Medical Chamber Objects

The surgical cabinets are scenery in the Medical Chamber.
The description of the surgical cabinets is "Metal cabinets line the walls, most of them rusted shut. However, one cabinet door hangs open[if the medical gauze is in the open cabinet or the medical tape is in the open cabinet], revealing medical supplies inside:[otherwise]. It appears to be empty now.[end if][if the medical gauze is in the open cabinet]
- Sterile medical gauze[end if][if the medical tape is in the open cabinet]
- Surgical tape[end if][if the medical gauze is in the open cabinet or the medical tape is in the open cabinet]

The open cabinet is within reach. You can take what you need[end if].".

Understand "cabinets" or "metal cabinets" or "rusted cabinets" as the surgical cabinets.

The open cabinet is a container in the Medical Chamber.
The open cabinet is scenery.
The open cabinet is fixed in place.
The open cabinet is open.
The open cabinet is not openable.
The description of the open cabinet is "An open medical cabinet[if the medical gauze is in the open cabinet or the medical tape is in the open cabinet] containing various supplies[otherwise] that appears to be empty now[end if].".

Understand "cabinet" or "open cabinet" or "metal cabinet" as the open cabinet.

Does the player mean doing something with the open cabinet: it is very likely.

The medical gauze is a thing in the open cabinet.
The description of the medical gauze is "Sterile medical gauze, still in its packaging. It could be used to stop bleeding.".

Understand "gauze" or "sterile gauze" as the medical gauze.

The medical tape is a thing in the open cabinet.
The description of the medical tape is "Surgical tape, sticky and strong. Perfect for securing bandages.".

Understand "tape" or "surgical tape" as the medical tape.

The examination table is scenery in the Medical Chamber.
The examination table is fixed in place.
The description of the examination table is "A massive steel table covered in leather restraints. Dark stains suggest it has been used for something terrible. The restraints look disturbingly worn.".

Understand "table" or "steel table" or "restraints" as the examination table.

The glass cylinders are scenery in the Medical Chamber.
The glass cylinders are fixed in place.
The description of the glass cylinders is "Three large glass cylinders stand against the wall. Each contains a severed limb suspended in murky preservative fluid:
- The first contains a human arm
- The second contains a human leg  
- The third contains a human hand
Above them, a digital display reads 'SPECIMENS: 3 / 6'.
The sight is deeply disturbing.".

Understand "cylinder" or "cylinders" or "glass cylinder" or "limbs" or "severed limbs" or "specimens" as the glass cylinders.

The chamber exit door is a door.
The chamber exit door is east of the Medical Chamber.
The chamber exit door is closed and locked.

The chamber exit door can be puzzle-locked or puzzle-unlocked.
The chamber exit door is puzzle-locked.

The description of the chamber exit door is "A heavy metal door with a complex locking mechanism. [if puzzle-locked]The mechanism consists of four colored pressure plates that must be activated in the correct sequence[otherwise]The door is now unlocked[end if].".

Understand "metal door" or "exit" or "door" as the chamber exit door.

The pressure plates are scenery in the Medical Chamber.
The pressure plates are fixed in place.
The description of the pressure plates is "Four colored pressure plates are embedded in the floor near the door: RED, BLUE, GREEN, and YELLOW. They seem to be part of the door's locking mechanism.".

Understand "plate" or "plates" or "pressure plate" or "colored plates" as the pressure plates.

The red plate is scenery in the Medical Chamber.
The red plate is fixed in place.

The blue plate is scenery in the Medical Chamber.
The blue plate is fixed in place.

The green plate is scenery in the Medical Chamber.
The green plate is fixed in place.

The yellow plate is scenery in the Medical Chamber.
The yellow plate is fixed in place.

Plate-sequence is a list of text that varies.
Plate-sequence is {}.

Correct-sequence is a list of text that varies.
Correct-sequence is {"blue", "red", "yellow", "green"}.




Chapter 17 - Entering Medical Chamber

After going to the Medical Chamber for the first time:
	display the Figure of MedicalChamberImage;
	if Prisoner-cut is true and the other prisoner is not dead:
		if the other prisoner is in the Exit Hall or the other prisoner is being-dragged:
			now the other prisoner is in the Medical Chamber;
			now the other prisoner is bleeding;
			now Prisoner-bleeding-turns is 0;
			play the sound of Bleeding;
			if Player-cut is true:
				now Player-bleeding is true;
				now Player-bleeding-turns is 0;
				say "[paragraph break]As you enter the chamber, you notice both your severed ankle and [prisoner-name-possessive] severed ankle are bleeding heavily. Blood pools beneath you both, spreading across the floor.
You need to stop the bleeding quickly, or neither of you will make it.";
			otherwise:
				say "[paragraph break]As you enter the chamber, you notice [prisoner-name-possessive] severed ankle is bleeding heavily. Blood pools beneath him, spreading across the floor.
You need to do something quickly, or he won't make it.";
		otherwise if Player-cut is true:
			now Player-bleeding is true;
			now Player-bleeding-turns is 0;
			play the sound of Bleeding;
			say "[paragraph break]As you enter the chamber, you notice your severed ankle is bleeding heavily. Blood pools beneath you, spreading across the floor.
You need to stop the bleeding quickly, or you won't make it.
[paragraph break]You are alone. The other prisoner... you left him behind.";
	otherwise if Player-cut is true:
		now Player-bleeding is true;
		now Player-bleeding-turns is 0;
		play the sound of Bleeding;
		say "[paragraph break]As you enter the chamber, you notice your severed ankle is bleeding heavily. Blood pools beneath you, spreading across the floor.
You need to stop the bleeding quickly, or you won't make it.
[paragraph break]You are alone. The other prisoner... you left him behind.".




Chapter 18 - Bleeding Mechanic

Every turn when the player is in the Medical Chamber:
	increase Chamber-turns-elapsed by 1;
	if the other prisoner is in the Medical Chamber and the other prisoner is bleeding and the other prisoner is unbandaged and the other prisoner is not dead:
		increase Prisoner-bleeding-turns by 1;
		if Prisoner-bleeding-turns is 1:
			say "[paragraph break]Blood continues to pour from [prisoner-name-possessive] wound. His breathing becomes more labored.";
		otherwise if Prisoner-bleeding-turns is 2:
			say "[paragraph break][prisoner-name-possessive] face is deathly pale. The pool of blood is growing rapidly.";
		otherwise if Prisoner-bleeding-turns is 3:
			say "[paragraph break][prisoner-name-possessive] breathing is barely detectable. He's losing too much blood!";
		otherwise if Prisoner-bleeding-turns is 4:
			say "[paragraph break][prisoner-name-possessive] body is going into shock. His pulse is fading. This is his last chance!";
		otherwise if Prisoner-bleeding-turns is 5:
			say "[paragraph break][prisoner-name-possessive] lips are turning blue. His eyes are rolling back. He's dying!";
		otherwise if Prisoner-bleeding-turns is 6:
			now the other prisoner is dead;
			say "[paragraph break][prisoner-name-possessive] chest stops moving. The blood has stopped flowing because his heart has stopped beating. He is dead.
You failed to save him.";
	if Player-bleeding is true and Player-bandaged is false:
		increase Player-bleeding-turns by 1;
		if Player-bleeding-turns is 1:
			say "[paragraph break]Blood continues to pour from your severed ankle. You feel dizzy and weak.";
		otherwise if Player-bleeding-turns is 2:
			say "[paragraph break]Your vision blurs. The pool of blood beneath you is growing rapidly. You need to stop the bleeding now!";
		otherwise if Player-bleeding-turns is 3:
			say "[paragraph break]Your breathing becomes shallow. You're losing too much blood!";
		otherwise if Player-bleeding-turns is 4:
			say "[paragraph break]Your body is going into shock. Your pulse is fading. This is your last chance!";
		otherwise if Player-bleeding-turns is 5:
			say "[paragraph break]Your lips are turning blue. Everything is getting darker. You're dying!";
		otherwise if Player-bleeding-turns is 6:
			play the sound of Bleeding;
			say "[paragraph break]Your vision goes black. The blood has stopped flowing because your heart has stopped beating.
You are dead.";
			end the story;
	if Chamber-turns-elapsed is 10 and Puzzle-activated is false:
		activate the puzzle.

Every turn when the player is in the Observation Room:
	if Player-wrist-bleeding is true:
		increase Player-wrist-bleeding-turns by 1;
		if Player-wrist-bleeding-turns is 1:
			say "[paragraph break]Blood spurts from your severed wrist. You're losing blood fast! You need to bandage yourself NOW!";
		otherwise if Player-wrist-bleeding-turns is 2:
			play the sound of BodyFall;
			say "[paragraph break]Too much blood loss. Your vision goes black.
[paragraph break]You collapse to the floor, unconscious.
[paragraph break]You will never wake up.";
			end the story.




Chapter 19 - Bandaging

Bandaging is an action applying to one thing.
Understand "bandage [someone]" or "wrap [someone]" or "stop bleeding of [someone]" or 
"use gauze on [someone]" or "apply gauze to [someone]" or "close wound of [someone]" as bandaging.

Bandaging yourself is an action applying to nothing.
Understand "bandage myself" or "bandage me" or "wrap myself" or "stop my bleeding" or 
"use gauze on myself" or "apply gauze to myself" or "close my wound" or "bandage my ankle" or "wrap my ankle" as bandaging yourself.

Check bandaging yourself:
	if Player-bleeding is false and Player-wrist-bleeding is false:
		say "You're not bleeding." instead;
	if the player does not carry the medical gauze:
		say "You need something to stop the bleeding with." instead.

Carry out bandaging yourself:
	if the player carries the medical tape:
		if Player-wrist-bleeding is true:
			now Player-wrist-bleeding is false;
			now Player-wrist-bleeding-turns is 0;
			increase Medical-supplies-used by 1;
			if Medical-supplies-used is 2:
				now the medical gauze is nowhere;
				now the medical tape is nowhere;
			display the Figure of ArmBandageImage;
			play the sound of WoundClose;
			say "You grit your teeth and wrap the gauze around your severed wrist, securing it tightly with the medical tape.
The bleeding slows and finally stops.
You might actually survive this.";
		otherwise:
			now Player-bandaged is true;
			now Player-bleeding is false;
			increase Medical-supplies-used by 1;
			if Medical-supplies-used is 2:
				now the medical gauze is nowhere;
				now the medical tape is nowhere;
			display the Figure of MarcusBleedingImage;
			play the sound of WoundClose;
			say "You grit your teeth and wrap the gauze around your severed ankle, securing it tightly with the medical tape.
The bleeding slows and finally stops.
Your breathing stabilizes slightly. You might actually survive this.";
	otherwise:
		say "The gauze alone won't hold. You need something to secure it with.".

Check bandaging:
	if the noun is not the other prisoner:
		say "That doesn't need bandaging." instead;
	if the other prisoner is dead:
		say "It's too late. He's already gone." instead;
	if the other prisoner is not bleeding:
		say "He's not bleeding." instead;
	if the player does not carry the medical gauze:
		say "You need something to stop the bleeding with." instead.

Carry out bandaging:
	if the player carries the medical tape:
		now the other prisoner is bandaged;
		now the other prisoner is not-bleeding;
		increase Medical-supplies-used by 1;
		if Medical-supplies-used is 2:
			now the medical gauze is nowhere;
			now the medical tape is nowhere;
		display the Figure of MarcusBleedingImage;
		play the sound of WoundClose;
		say "You quickly wrap the gauze around [prisoner-name-possessive] severed ankle, securing it tightly with the medical tape.
The bleeding slows and finally stops.
His breathing stabilizes slightly. He might actually survive this.";
	otherwise:
		say "The gauze alone won't hold. You need something to secure it with.".




Chapter 20 - Marcus Waking Up

Every turn when the other prisoner is bandaged and the other prisoner is unconscious and the other prisoner is alive:
	if a random chance of 1 in 3 succeeds:
		now the other prisoner is conscious;
		now the other prisoner is introduced;
		play the sound of PrisonerWake;
		say "[paragraph break]The man's eyes suddenly flutter open. He gasps, looking around in confusion and pain.
'What... where am I?' he croaks, his voice hoarse.
He looks down at his bandaged ankle and then at you.
'You... you saved me. I thought I was going to die in that cell.'";
		continue the action.




Chapter 21 - Talking to Marcus

Talking to is an action applying to one thing.
Understand "talk to [someone]" or "speak to [someone]" or "speak with [someone]" or 
"ask [someone] about himself" or "converse with [someone]" as talking to.

Check talking to:
	if the noun is not the other prisoner:
		say "No response." instead;
	if the other prisoner is unconscious:
		say "He's unconscious. He can't hear you." instead;
	if the other prisoner is dead:
		say "He's dead. There's nothing more to say." instead.

Carry out talking to the other prisoner:
	if the other prisoner is conscious:
		if the other prisoner is unintroduced:
			now the other prisoner is introduced;
			say "'I'm Marcus,' he says, wincing in pain. 'I don't remember much... just waking up in that cell, chained like an animal.'
He looks around the room, his eyes widening in horror at the glass cylinders.
'My God... what is this place? Who would do this?'
He tries to sit up but grimaces. 'I can't walk. My ankle... you're going to have to figure out how to get us out of here.'
'Be careful,' he warns. 'This room is designed to hurt us. Don't make any mistakes.'";
		otherwise:
			say "Marcus looks at you with pain in his eyes. 'We need to get out of here. Look for a way to open that door.'".




Chapter 22 - Asking Marcus About Things

Instead of asking the other prisoner about something:
	if the other prisoner is unconscious:
		say "He's unconscious and can't respond.";
	otherwise if the other prisoner is dead:
		say "He's dead.";
	otherwise:
		say "Marcus shakes his head. 'I don't know anything about that. I'm just trying to stay alive.'".




Chapter 23 - Puzzle Activation

To activate the puzzle:
	now Puzzle-activated is true;
	display the Figure of PressurePlatesImage;
	play the sound of PuzzleActivate;
	say "[paragraph break]BZZZZT!

A loud buzzer echoes through the chamber.
The lights flicker and turn red.

A distorted voice booms from hidden speakers:
'YOU HAVE IGNORED THE RULES FOR TOO LONG. THE PUZZLE IS NOW ACTIVE.
STEP ON THE COLORED PLATES IN THE CORRECT SEQUENCE TO UNLOCK THE DOOR.
EACH MISTAKE WILL COST YOU A PIECE OF YOURSELF.
YOU HAVE THREE CHANCES.
FAIL THREE TIMES, AND YOU WILL NEVER LEAVE.'

The pressure plates on the floor begin to glow ominously.";
	if the other prisoner is conscious:
		say "[paragraph break]Marcus's voice trembles: 'Oh God... we need to figure this out quickly. Look for clues!'".




Chapter 24 - Stepping on Pressure Plates

Stepping on is an action applying to one thing.
Understand "step on [something]" or "press [something]" or "activate [something]" or 
"stand on [something]" as stepping on.

Check stepping on:
	if the noun is not the red plate and the noun is not the blue plate and the noun is not the green plate and the noun is not the yellow plate:
		say "You can't step on that." instead;
	if Puzzle-activated is false:
		say "The plates don't respond. They haven't been activated yet." instead.

Carry out stepping on the red plate:
	add "red" to Plate-sequence;
	play the sound of ButtonPress;
	say "You step on the RED plate. It glows brighter and emits a low tone.";
	check the sequence.

Carry out stepping on the blue plate:
	add "blue" to Plate-sequence;
	play the sound of ButtonPress;
	say "You step on the BLUE plate. It glows brighter and emits a low tone.";
	check the sequence.

Carry out stepping on the green plate:
	add "green" to Plate-sequence;
	play the sound of ButtonPress;
	say "You step on the GREEN plate. It glows brighter and emits a low tone.";
	check the sequence.

Carry out stepping on the yellow plate:
	add "yellow" to Plate-sequence;
	play the sound of ButtonPress;
	say "You step on the YELLOW plate. It glows brighter and emits a low tone.";
	check the sequence.




Chapter 25 - Checking Sequence

To check the sequence:
	if the number of entries in Plate-sequence is 4:
		if Plate-sequence is Correct-sequence:
			say "[paragraph break]The plates flash GREEN in sequence. You hear a heavy CLUNK as the door mechanism unlocks.";
			now the chamber exit door is unlocked;
			now the chamber exit door is puzzle-unlocked;
			now the medical chamber entrance door is closed;
			now the medical chamber entrance door is locked;
			say "[paragraph break]Behind you, the entrance door SLAMS shut and locks with a mechanical THUNK. There is no going back.";
			if Limb-type is "right hand":
				say "[paragraph break]But as you take a step toward freedom, your vision blurs.
Blood loss from both severed wrists is too severe.
Everything goes dark before your eyes.";
				play the sound of BodyFall;
				say "[paragraph break]You collapse to the floor, unconscious.
[paragraph break]You will never wake up.";
				end the story;
			otherwise if Limb-type is "left hand":
				now Player-wrist-bleeding is true;
				now Player-wrist-bleeding-turns is 0;
				say "[paragraph break]But blood continues to pour from your severed wrist. The pain is overwhelming.
You need to stop the bleeding before you can leave, or you won't make it.";
				if the other prisoner is conscious:
					say "[paragraph break]Marcus calls out: 'Use the medical supplies! Bandage yourself quickly!'";
			otherwise:
				if the other prisoner is conscious:
					say "[paragraph break]'You did it!' Marcus shouts. 'The door is open!'";
		otherwise:
			now Player-lost-limb is true;
			now Plate-sequence is {};
			play the sound of TrapFail;
			if Limb-type is "":
				now Limb-type is "left hand";
				play the sound of Screaming;
				say "[paragraph break]WRONG!

The mechanical device LUNGES forward with terrifying speed. Before you can react, it clamps onto your left hand.
You scream as the blade severs your hand at the wrist.
The machine retracts, depositing your severed hand into the collection basin.

The digital counter updates: 'SPECIMENS: 4 / 6'

The pain is unbearable, but you're still alive.";
				if the other prisoner is conscious:
					say "[paragraph break]Marcus screams: 'NO! Oh God, your hand! Try again, but be careful!'";
			otherwise if Limb-type is "left hand":
				now Limb-type is "right hand";
				play the sound of Screaming;
				say "[paragraph break]WRONG AGAIN!

The machine strikes once more. This time it takes your right hand.
You fall to your knees, screaming. Blood pours from both wrists.

The counter updates: 'SPECIMENS: 5 / 6'";
				if the other prisoner is conscious:
					say "[paragraph break]Marcus is crying: 'Please, you have to get this right! One more mistake and...'";
			otherwise:
				say "[paragraph break]WRONG FOR THE LAST TIME!

The machine grabs you by the neck, pulling you into its blades.
There is no escape.

The counter updates: 'SPECIMENS: 6 / 6'

Everything goes black.";
				play the sound of Screaming;
				play the sound of GameOver;
				end the story finally.




Chapter 26 - Resetting Sequence

Resetting sequence is an action applying to nothing.
Understand "reset" or "start over" or "clear sequence" as resetting sequence.

Check resetting sequence:
	if Puzzle-activated is false:
		say "There's nothing to reset." instead.

Carry out resetting sequence:
	now Plate-sequence is {};
	say "You step back. The plates dim slightly, ready for a new attempt.".




Chapter 27 - Visual and Audio Cues

Figure of MedicalChamberImage is the file "medical_chamber.png".
Figure of MarcusBleedingImage is the file "marcus_bleeding.png".
Figure of PressurePlatesImage is the file "pressure_plates.png".
Figure of CutLegImage is the file "cut_leg.png".
Figure of ArmBandageImage is the file "arm-bandage.png".
Figure of ObservationRoomImage is the file "observation_room.png".
Figure of SawManImage is the file "saw_man.png".
Figure of JawBreakerRoomImage is the file "jawbraker.png".
Figure of BearTrapImage is the file "beartrap.png".




Chapter 28 - Hints for the Puzzle

The bloody note is a thing in the Medical Chamber.
The description of the bloody note is "A blood-stained note with shaky handwriting:
'The order is written in the colors of water, fire, caution, and life.
Blue flows first, Red burns second, Yellow warns third, Green grows last.
BLUE - RED - YELLOW - GREEN'".

Understand "note" or "hint" or "clue" or "paper" as the bloody note.




Chapter 15 - Game Start

Use no scoring.

Figure of CellImage is the file "cell.png".

When play begins:
	say "You regain consciousness to the sound of chains and distant machinery.[paragraph break]";
	say "A distorted voice fills the room.";
	play the sound of TapeVoice;
	display the Figure of CellImage.

When play ends:
	play the sound of GameOverMusic.



Chapter 29 - Observation Room Furniture Positioning

Positioning furniture is an action applying to one thing.
Understand "position [something] under vent" or "move [something] under vent" or 
"push [something] under vent" or "drag [something] under vent" or
"place [something] under vent" or "put [something] under vent" as positioning furniture.

Check positioning furniture:
	if the player is not in the Observation Room:
		say "There's nothing to position here." instead;
	if the noun is not the metal chair and the noun is not the filing cabinet:
		say "That won't help you reach the vent." instead;
	if Player-hands-trapped is 2:
		say "Without hands, you can't move anything." instead;
	if Player-hands-trapped is 1:
		say "With only one hand, moving heavy furniture is extremely difficult, but you manage it with great effort.".

Carry out positioning furniture:
	if the noun is the metal chair:
		if Chair-positioned is true:
			say "The chair is already positioned under the vent.";
		otherwise:
			now Chair-positioned is true;
			now the metal chair is positioned-under-vent;
			play the sound of ChairMove;
			say "You drag the metal chair across the floor, positioning it directly beneath the air vent. [if Cabinet-positioned is true]With the cabinet already in place, you carefully climb onto the cabinet and place the chair on top of it. The makeshift tower looks precarious but might work[otherwise]It's not tall enough on its own - you'll need something else[end if].";
	otherwise if the noun is the filing cabinet:
		if Cabinet-positioned is true:
			say "The cabinet is already positioned under the vent.";
		otherwise:
			now Cabinet-positioned is true;
			now the filing cabinet is positioned-under-vent;
			play the sound of ChairMove;
			say "You push the heavy filing cabinet with great effort, slowly moving it across the floor until it's positioned beneath the air vent. [if Chair-positioned is true]The chair is already there. You manage to stack the cabinet and chair together, creating a precarious tower[otherwise]It's sturdy, but you'll need to stack something on top to reach the vent[end if].".



Chapter 30 - Reaching the Vent

Reaching the vent is an action applying to nothing.
Understand "reach vent" or "reach air vent" or "climb to vent" or 
"climb up" or "climb tower" or "reach for vent" or "grab vent" as reaching the vent.

Check reaching the vent:
	if the player is not in the Observation Room:
		say "There's no vent here." instead;
	if Observation-room-trap-activated is true:
		say "You already triggered the trap. There's no turning back now." instead;
	if Chair-positioned is false or Cabinet-positioned is false:
		say "You can't reach the vent without both the cabinet and chair positioned beneath it." instead.

Carry out reaching the vent:
	now Observation-room-trap-activated is true;
	say "You carefully climb onto the filing cabinet, then step up onto the chair balanced on top.
The tower wobbles dangerously, but you steady yourself.

You reach toward the vent grate...

SNAP!";
	play the sound of SawTrap;
	say "
Hidden mechanisms activate instantly. Metal clamps shoot out from the wall, clamping around your wrist";
	if Limb-type is "right hand" or Limb-type is "left hand":
		if the other prisoner is in the Observation Room and the other prisoner is conscious:
			now Player-hands-trapped is 1;
			say "!

You're trapped, suspended in the air, held by your single hand.

The monitors flicker to life. A distorted figure appears on every screen - The Jigsaw Killer.";
			play the sound of JigsawVoice;
			display the Figure of SawManImage;
			say "

'Ah, you've already sacrificed so much. One hand gone, and now... the other is mine.'

The mechanism begins to activate.

'There is no escape this time. No questions. No deals. Just... the end.'

You can try to STRUGGLE, but it's futile.";
			now Last-hand-dying is true;
			now Last-hand-death-turns is 1;
			play the sound of SawTrap;
		otherwise:
			now Player-hands-trapped is 1;
			say "!

You're trapped, suspended in the air, held by your single hand.

The monitors flicker to life. A distorted figure appears on every screen - The Jigsaw Killer.";
			play the sound of JigsawVoice;
			display the Figure of SawManImage;
			say "

'Ah, you've come this far alone... but now your sacrifice has become your doom.'

The mechanism begins to activate.

'One hand already gone, and now this one too. There is no escape. No way out. Just... the end.'

You can try to STRUGGLE, but it's futile.";
			now Last-hand-dying is true;
			now Last-hand-death-turns is 1;
			play the sound of SawTrap;
	otherwise:
		if the other prisoner is in the Observation Room and the other prisoner is conscious:
			now Player-hands-trapped is 2;
			say "s!

BOTH your wrists are locked in the mechanisms! You're suspended in the air, completely helpless.

The monitors flicker to life. A distorted figure appears on every screen - The Jigsaw Killer.";
			play the sound of JigsawVoice;
			display the Figure of SawManImage;
			say "

'Welcome to your final test,' the voice rasps. 'You've learned about sacrifice. About pain. But have you learned about TRUST?

Both your hands are locked in place. In exactly 5 minutes, these mechanisms will sever them both. You will fall, and with no hands left, you will bleed out in seconds.

But there is a way to survive...'

The voice pauses for dramatic effect.

'I will ask you ONE question. Answer correctly, and the mechanism releases. Answer incorrectly... and you die.

However, your companion knows the answer. You may ask him for help.

But here's the twist: If you ask him, HE must decide whether to help you or save himself. 
If he tells you the truth, you both go free. 
If he lies to save himself, you die and he escapes alone.

The choice is yours. Do you trust him with your life?'

[paragraph break]The question appears on all the monitors:

'WHAT IS THE ONE THING THAT CAN BE GIVEN, BUT NEVER TAKEN BACK?'";
			play the sound of SawTrap;
		otherwise:
			now Player-hands-trapped is 1;
			now Solo-arm-trap-turns is 0;
			say "!

Metal clamps shoot out and lock around your entire right arm - from shoulder to wrist! You're held firmly in place.

The monitors flicker to life. A distorted figure appears on every screen - The Jigsaw Killer.";
			play the sound of JigsawVoice;
			display the Figure of SawManImage;
			say "

'Welcome to your final test. You've come this far alone. Impressive.

Your arm is locked in place. Answer my question correctly, and you go free.

Answer incorrectly... and this mechanism will pull you into the saw blades behind you. You'll be torn apart.'

The voice pauses.

'There is one other way... you can sacrifice your arm. Cut it off and escape. But with only one arm left, survival becomes... difficult.

The choice is yours.'

[paragraph break]The question appears on all the monitors:

'WHAT IS THE ONE THING THAT CAN BE GIVEN, BUT NEVER TAKEN BACK?'

[paragraph break]You can ANSWER the question or use your SAW to cut your arm.";
			play the sound of SawTrap;
	now Question-asked is true.

Chapter 31 - The Impossible Question Timer and Solo Escape

Every turn when Observation-room-trap-activated is true and Player-hands-trapped is greater than 0 and Last-hand-dying is false:
	if the other prisoner is in the Observation Room and the other prisoner is conscious and Question-asked is true and Player-answered is false:
		say "[paragraph break]The monitors display: 'ANSWER THE QUESTION OR ASK YOUR COMPANION. TIME IS RUNNING OUT.'";
	otherwise if the other prisoner is not in the Observation Room and Player-hands-trapped is 1:
		increase Solo-arm-trap-turns by 1;
		if Solo-arm-trap-turns is 1:
			say "[paragraph break]The monitors display: 'ANSWER THE QUESTION OR CUT YOUR ARM. YOU HAVE 3 MOVES LEFT.'";
		otherwise if Solo-arm-trap-turns is 2:
			say "[paragraph break]The monitors flash red: 'TIME IS RUNNING OUT! 2 MOVES LEFT!'";
		otherwise if Solo-arm-trap-turns is 3:
			say "[paragraph break]The monitors flash red rapidly: 'FINAL WARNING! 1 MOVE LEFT!'";
		otherwise if Solo-arm-trap-turns is greater than 3:
			say "[paragraph break]The monitors go dark.

'TIME'S UP,' the voice rasps.

The mechanism activates.

You feel the clamps pulling you backward - straight into the spinning saw blades!

You scream as the blades tear into your back, ripping through flesh and bone.";
			play the sound of SawTrap;
			play the sound of Screaming;
			play the sound of BodyFall;
			say "

There is no mercy. No escape.

The blades consume you.

This is the end.";
			end the story.



Chapter 32 - Solo Escape With Saw

Cutting hand with saw is an action applying to nothing.
Understand "cut my hand" or "cut my wrist" or "saw my hand" or "saw my wrist" or "cut my arm" or "saw my arm" or
"use saw" or "cut myself with saw" or "saw through wrist" or "saw through arm" or
"cut hand" or "cut wrist" or "cut arm" or "saw hand" or "saw wrist" or "saw arm" or
"use saw on arm" or "use saw on hand" or "use saw on wrist" or "use the saw" or "saw off arm" or "cut off arm" as cutting hand with saw.

Check cutting hand with saw:
	if the player is not in the Observation Room:
		say "There's nothing to cut." instead;
	if Observation-room-trap-activated is false:
		say "You're not trapped." instead;
	if the other prisoner is in the Observation Room:
		say "You need to answer the question or ask Marcus for help." instead;
	if the hand saw is not carried by the player:
		say "You don't have anything to cut with." instead;
	if Player-hands-trapped is 2:
		say "With both hands trapped, you can't use the saw." instead;
	if Player-hands-trapped is 0:
		say "You're not trapped anymore." instead.

Carry out cutting hand with saw:
	if the other prisoner is in the Observation Room:
		say "You need to work with Marcus, not harm yourself!";
		stop the action;
	say "You pull out the rusty hand saw from your pocket.

With your free hand, you bring it to your trapped arm and begin cutting through the flesh and bone.";
	play the sound of NPCCut;
	say "
The pain is indescribable. The saw blade tears through muscle, grinds against bone.

But you don't stop.

Blood sprays everywhere.

CRACK!

Your arm falls away. You collapse to the ground, free but bleeding heavily from the shoulder.";
	now Player-hands-trapped is 0;
	now Observation-room-trap-activated is false;
	now the observation exit door is unlocked;
	now the observation exit door is open;
	now the observation exit door is trap-unlocked;
	if Medical-supplies-used is 2:
		play the sound of BodyFall;
		say "[paragraph break]Blood pours from your severed shoulder. You have no medical supplies left!

You try to stop the bleeding with pressure, but it's not enough.

Your vision fades as you collapse.

You survived so much... but you can't survive this.";
		end the story;
	otherwise:
		now Player-wrist-bleeding is true;
		now Player-wrist-bleeding-turns is 0;
		say "[paragraph break]You need to bandage your shoulder IMMEDIATELY or you will bleed out!

You have [if Medical-supplies-used is 0]medical supplies available[otherwise]ONE use of medical supplies left[end if]. Use them now!

[paragraph break]The question monitor goes dark. The door at the far end of the room unlocks with a heavy CLUNK.

You are free. But at what cost?".



Chapter 33 - Answering The Question

Responding to question is an action applying to one topic.
Understand "answer [text]" or "respond [text]" or "say [text]" or "the answer is [text]" as responding to question.

Check responding to question:
	if the player is in the Jaw Breaker Chamber:
		if Jaw-device-worn is false:
			say "You need to wear the device first." instead;
		if Jaw-puzzle-activated is false:
			say "The puzzle isn't active." instead;
		if Jaw-current-question is 0:
			say "There's no question displayed yet." instead;
	otherwise if the player is in the Observation Room:
		if Observation-room-trap-activated is false:
			say "You haven't triggered the trap yet." instead;
		if Player-answered is true:
			say "You already answered." instead;
	otherwise:
		say "There's no question to answer." instead.

Carry out responding to question:
	if the player is in the Jaw Breaker Chamber:
		let the answer be "[the topic understood in lower case]";
		let correct be false;
		if Jaw-current-question is 1 and the answer matches the text "paris":
			now correct is true;
		if Jaw-current-question is 2 and (the answer matches the text "pacific" or the answer matches the text "pacific ocean"):
			now correct is true;
		if Jaw-current-question is 3 and (the answer matches the text "four" or the answer matches the text "4"):
			now correct is true;
		if Jaw-current-question is 4 and (the answer matches the text "oxygen" or the answer matches the text "o"):
			now correct is true;
		if Jaw-current-question is 5 and (the answer matches the text "shakespeare" or the answer matches the text "william shakespeare"):
			now correct is true;
		if correct is true:
			say "You hear a confirmation tone.

'CORRECT.'

";
			if Jaw-current-question is 5:
				say "'You have completed the test. Well done.'

A compartment in the wall slides open with a mechanical hiss, revealing a brass key.";
				now the jaw key is in the wall compartment;
				now the wall compartment is open;
				now Jaw-puzzle-solved is true;
				now Jaw-puzzle-activated is false;
				say "

You can now TAKE the KEY to unlock the device and escape.";
			otherwise:
				increase Jaw-current-question by 1;
				say "[paragraph break]The next question appears on the screen...

";
				if Jaw-current-question is 2:
					say "QUESTION 2: What is the largest ocean on Earth?";
				if Jaw-current-question is 3:
					say "QUESTION 3: How many sides does a square have?";
				if Jaw-current-question is 4:
					say "QUESTION 4: What element does 'Au' represent on the periodic table?";
				if Jaw-current-question is 5:
					say "QUESTION 5: Who wrote 'Romeo and Juliet'?";
		otherwise:
			play the sound of TrapFail;
			increase Jaw-wrong-answers by 1;
			say "You hear an error tone.

'WRONG.'

";
			if Jaw-wrong-answers is less than 3:
				say "The device tightens slightly around your jaw. You feel pressure building.

'You have [3 minus Jaw-wrong-answers] wrong answer[s] remaining before the device activates.'

[paragraph break]The next question appears...

";
				increase Jaw-current-question by 1;
				if Jaw-current-question is 2:
					say "QUESTION 2: What is the largest ocean on Earth?";
				if Jaw-current-question is 3:
					say "QUESTION 3: How many sides does a square have?";
				if Jaw-current-question is 4:
					say "QUESTION 4: What element does 'Au' represent on the periodic table?";
				if Jaw-current-question is 5:
					say "QUESTION 5: Who wrote 'Romeo and Juliet'?";
			otherwise:
				say "The device ACTIVATES.

You feel the mechanisms inside the cage begin to expand. 

The metal presses against your jaw, forcing it open wider... wider...

You scream, but the device doesn't stop.";
				play the sound of JawBreaker;
				play the sound of Screaming;
				say "

CRACK!

Your jaw shatters. Blood fills your mouth.

The device continues expanding.

CRUNCH!

Your skull splits open.

Darkness.";
				play the sound of BodyFall;
				play the sound of GameOver;
				end the story;
		stop the action;
	now Player-answered is true;
	let the answer be "[the topic understood]";
	if the answer matches the text "trust" or the answer matches the text "trust.":
		say "You shout: 'TRUST!'

The monitors flash green.

The mechanical clamps release instantly. You fall, catching yourself on the furniture below.

'CORRECT,' the voice booms. 'You've learned the lesson. Trust is given freely, but once broken, it can never be restored.'

The door at the far end of the room unlocks with a heavy CLUNK.

You are free.";
		now Player-hands-trapped is 0;
		now Observation-room-trap-activated is false;
		now the observation exit door is unlocked;
		now the observation exit door is open;
		now the observation exit door is trap-unlocked;
		if the other prisoner is in the Observation Room:
			say "[paragraph break]Marcus stares at you in disbelief. 'You... you did it. We're free!'";
	otherwise:
		play the sound of TrapFail;
		play the sound of Screaming;
		say "You shout: '[the answer]!'

The monitors flash RED.

'WRONG,' the voice declares.

The mechanisms activate.";
		if the other prisoner is not in the Observation Room and Player-hands-trapped is 1:
			say "

The mechanism begins to pull you backward!

You feel the clamps dragging your arm toward the spinning saw blades behind you.

You scream as the blades tear into your flesh.

There is no mercy. No escape.

The saw rips through muscle, bone, and sinew.";
			play the sound of BodyFall;
			say "

Your body goes limp as the blades consume you.

This is the end.";
			end the story;
		otherwise:
			say "

[if Player-hands-trapped is 2]Both blades cut through your wrists simultaneously. You fall, hitting the ground hard.

Blood spurts from both severed wrists. There is no way to stop it.

[otherwise]The blade cuts through your single remaining wrist. You fall.

Blood pours from the stump. With no hands left, you can't even try to stop it.

[end if]Your vision goes dark.

This is the end.";
			end the story.



Chapter 34 - Asking Marcus For Help

Asking Marcus for help is an action applying to nothing.
Understand "ask marcus for help" or "ask marcus" or "ask marcus about answer" or 
"ask marcus about question" or "marcus help" or "help marcus" as asking Marcus for help.

Check asking Marcus for help:
	if the player is not in the Observation Room:
		say "Marcus isn't here." instead;
	if the other prisoner is not in the Observation Room:
		say "Marcus isn't here." instead;
	if the other prisoner is unconscious:
		say "Marcus is unconscious." instead;
	if the other prisoner is dead:
		say "Marcus is dead." instead;
	if Observation-room-trap-activated is false:
		say "There's nothing to ask him about." instead;
	if Player-answered is true:
		say "You already answered the question." instead.

Carry out asking Marcus for help:
	now Player-answered is true;
	play the sound of Pressure;
	say "You look at Marcus desperately.

'Marcus! Do you know the answer?! Please!'

Marcus stares at you, his face conflicted. Sweat beads on his forehead.

The monitors display: 'HE KNOWS THE ANSWER. WILL HE SAVE YOU... OR HIMSELF?'

Marcus's voice trembles: 'I... I do know it. I remember... from before.'

He pauses, looking between you and the chamber exit door.

'But if I tell you... we both go free. If I don't...'

He's considering betraying you.

[paragraph break]You can see the internal struggle in his eyes.

What do you say?

(Type 'confess your sins' or 'lie to marcus')".



Chapter 35 - Player's Final Choice

Confessing is an action applying to nothing.
Understand "confess" or "confess your sins" or "confess sins" or "tell truth" or "be honest" as confessing.

Check confessing:
	if the player is not in the Observation Room:
		say "There's nothing to confess." instead;
	if Observation-room-trap-activated is false:
		say "You haven't triggered the trap yet." instead;
	if Player-answered is false:
		say "You need to ask Marcus for help first." instead;
	if Player-confessed is true or Marcus-betrayed is true:
		say "It's too late. The choice has been made." instead.

Carry out confessing:
	now Player-confessed is true;
	say "You take a deep breath.

'Marcus... I need to tell you something.'

Your voice cracks.

'In the cell... when I had to choose... I almost left you behind. I thought about saving only myself. Part of me wanted to.'

Tears stream down your face.

'But I didn't. I saved you. And if I could do it again... I'd make the same choice. Because you're worth saving.'

Marcus's eyes widen. His expression softens.

'You... you're telling the truth.'

He steps closer.

'The answer is TRUST,' he says clearly. 'The thing that can be given but never taken back is TRUST.'

The monitors flash GREEN.

The mechanical clamps release. You fall, catching yourself.

'CORRECT,' the voice booms.

Marcus helps you down from the furniture.

'Thank you,' he says quietly. 'Thank you for being honest. Thank you for saving me.'

The observation exit door unlocks with a heavy CLUNK.

You both survived.";
	now Player-hands-trapped is 0;
	now Observation-room-trap-activated is false;
	now the observation exit door is unlocked;
	now the observation exit door is open;
	now the observation exit door is trap-unlocked.



Lying to Marcus is an action applying to nothing.
Understand "lie" or "lie to marcus" or "deceive" or "manipulate" as lying to Marcus.

Check lying to Marcus:
	if the player is not in the Observation Room:
		say "There's no one to lie to." instead;
	if Observation-room-trap-activated is false:
		say "You haven't triggered the trap yet." instead;
	if Player-answered is false:
		say "You need to ask Marcus for help first." instead;
	if Player-confessed is true or Marcus-betrayed is true:
		say "It's too late. The choice has been made." instead.

Carry out lying to Marcus:
	now Marcus-betrayed is true;
	say "You force a calm expression.

'Marcus, listen to me. I saved you in the cell, didn't I? I could have left you to die, but I didn't. That has to count for something.'

You're trying to manipulate him.

'You owe me your life. Now it's time to repay that debt. Tell me the answer. You know we'll both get out of here.'

Marcus looks at you carefully. His eyes narrow.

'You're... you're lying,' he says slowly. 'I can see it in your eyes.'

His expression hardens.

'You didn't save me out of kindness. You saved me because you thought you'd need me. As leverage. As a tool.'

He steps back toward the exit.

He walks to the observation exit door. It unlocks for him.

'Now you'll never have mine.'

He leaves.

The monitors flash RED.

'BETRAYAL COMPLETE,' the voice announces.

The mechanisms activate.";
	play the sound of Screaming;
	say "

[if Player-hands-trapped is 2]Both blades cut through your wrists. You fall.

[otherwise]The blade severs your remaining hand. You fall.

[end if]Blood pours from your wounds. You can't stop it.

Marcus's footsteps fade into the distance.

[paragraph break]You can try to STRUGGLE or SHOUT, but time is running out...";
	now Betrayal-dying is true;
	now Betrayal-death-turns is 1;
	now Player-hands-trapped is 0.


Struggling is an action applying to nothing.
Understand "struggle" or "fight" or "resist" as struggling.

Check struggling:
	if Betrayal-dying is false and Last-hand-dying is false:
		say "There's nothing to struggle against." instead.

Carry out struggling:
	if Betrayal-dying is true:
		say "You try to move, to fight, to do something... anything.

But your struggle is in vain. The blood loss is too severe. Your body won't respond.

You're dying.";
		now Betrayal-death-turns is 0;
	otherwise if Last-hand-dying is true:
		say "You pull against the mechanism with all your remaining strength.

But it's futile.

The mechanism activates.";
		play the sound of NPCCut;
		say "

Your last hand is severed.

You fall to the ground.";
		now Last-hand-death-turns is 0.


Shouting is an action applying to nothing.
Understand "shout" or "scream" or "yell" or "call for help" or "cry for help" as shouting.

Check shouting:
	if Betrayal-dying is false:
		say "There's no reason to shout." instead.

Carry out shouting:
	say "You scream with everything you have left.

'HELP! SOMEONE! ANYONE!'

Your voice echoes through the empty room.

But no one hears. No one is coming. You're alone.";
	now Betrayal-death-turns is 0.


Instead of doing anything when Betrayal-dying is true:
	if looking:
		continue the action;
	otherwise:
		say "You're too weak to do that.".

Instead of doing anything when Last-hand-dying is true:
	if looking or struggling:
		continue the action;
	otherwise:
		say "You're trapped. The only thing you can do is STRUGGLE.".

Every turn when Betrayal-dying is true:
	if Betrayal-death-turns is greater than 0:
		decrease Betrayal-death-turns by 1;
	otherwise:
		say "[paragraph break]Your vision darkens. The blood loss is too much.";
		play the sound of BodyFall;
		end the story.

Every turn when Last-hand-dying is true:
	if Last-hand-death-turns is greater than 0:
		decrease Last-hand-death-turns by 1;
	otherwise:
		say "[paragraph break]With no hands, you cannot stop the bleeding.

Your vision fades.

This is the end.";
		play the sound of BodyFall;
		end the story.



Chapter 36 - Entering Observation Room With Marcus

Before going to the Observation Room from the Medical Chamber:
	if the other prisoner is in the Medical Chamber and the other prisoner is conscious:
		now the other prisoner is in the Observation Room;
	continue the action.

After going to the Observation Room for the first time:
	display the Figure of ObservationRoomImage;
	if the other prisoner is in the Observation Room:
		say "[paragraph break]Marcus limps in behind you, leaning against the wall for support.
'Another room... another trap,' he mutters. 'We need to be careful.'";
	stop the action.



Chapter 37 - Final Exit

The observation exit door is a door.
The observation exit door is east of the Observation Room and west of the Dark Corridor.
The observation exit door is closed and locked.

The observation exit door can be trap-unlocked or trap-locked.
The observation exit door is trap-locked.

The observation exit door can be trap-unlocked or trap-locked.
The observation exit door is trap-locked.

Every turn when Player-hands-trapped is 0 and the player is in the Observation Room and Observation-room-trap-activated is true and the observation exit door is trap-locked:
	now the observation exit door is unlocked;
	now the observation exit door is open;
	now the observation exit door is trap-unlocked.

The Dark Corridor is a room.
The Dark Corridor is east of the observation exit door.

The description of the Dark Corridor is "You step into a dark, narrow corridor. The walls are cold concrete, barely lit by a single flickering bulb at the far end.

Behind you, the door to the Observation Room stands open. Ahead, another door waits.

[if the other prisoner is in the Dark Corridor]Marcus walks beside you, limping but alive.[otherwise]You walk alone. Marcus didn't make it.[end if]

This nightmare isn't over yet.".

Before going to the Dark Corridor:
	if the other prisoner is in the Observation Room and the other prisoner is conscious and the other prisoner is alive:
		now the other prisoner is in the Dark Corridor.



Chapter 38 - Room 4 The Jaw Breaker Chamber

The Jaw Breaker Chamber is a room.

The description of the Jaw Breaker Chamber is "You enter a cold, concrete room lit by a single flickering bulb. The walls are bare except for rust stains and scratch marks - evidence of previous victims.

In the center of the room sits a metal chair, and mounted above it is a horrifying device: a massive mechanical jaw breaker - a metal cage designed to fit over someone's head. Its internal mechanisms gleam with cruel precision.

[if the jaw breaker door is locked]The door behind you has locked automatically.[otherwise]The door behind you stands open.[end if]

A small wall compartment is embedded in the east wall."

The jaw breaker door is a door.
The jaw breaker door is east of the Dark Corridor and west of the Jaw Breaker Chamber.
The jaw breaker door is closed and unlocked.

The jaw breaker chair is scenery in the Jaw Breaker Chamber.
The description of the jaw breaker chair is "A cold metal chair sits directly beneath the jaw breaker device. Restraints dangle from its arms."

Understand "chair" or "metal chair" or "restraints" as the jaw breaker chair.

The jaw breaker device is scenery in the Jaw Breaker Chamber.
The description of the jaw breaker device is "A nightmarish contraption: a metal cage fitted with hydraulic pistons designed to force the jaws apart. Once activated, it will slowly expand until the victim's jaw is shattered and their skull is split open. 

[if Jaw-device-worn is false]It hangs ominously above the chair, waiting.[otherwise]It's locked around your head. You can feel its cold metal pressing against your face.[end if]"

Understand "device" or "jaw device" or "jaw breaker device" or "jaw breaker" or "cage" or "metal cage" or "contraption" as the jaw breaker device.

Does the player mean examining the jaw breaker device: it is very likely.

The wall compartment is scenery in the Jaw Breaker Chamber.
The description of the wall compartment is "[if the jaw key is in the wall compartment]A small compartment in the wall has slid open, revealing a brass key inside.[otherwise if Jaw-puzzle-solved is true]The compartment stands empty now.[otherwise]A small metal compartment, currently sealed shut.[end if]"

Understand "compartment" or "small compartment" or "metal compartment" as the wall compartment.

The wall compartment is a closed openable container.

The jaw key is a thing.
The description of the jaw key is "A small brass key. It looks like it would fit the jaw breaker device lock - and possibly the door."

Understand "key" or "brass key" or "small key" as the jaw key.



Chapter 39 - Room 4 Variables

Jaw-device-worn is a truth state that varies. Jaw-device-worn is false.
Jaw-puzzle-activated is a truth state that varies. Jaw-puzzle-activated is false.
Jaw-puzzle-solved is a truth state that varies. Jaw-puzzle-solved is false.
Jaw-wrong-answers is a number that varies. Jaw-wrong-answers is 0.
Jaw-current-question is a number that varies. Jaw-current-question is 0.
Marcus-jaw-choice-made is a truth state that varies. Marcus-jaw-choice-made is false.
Marcus-jaw-playing is a truth state that varies. Marcus-jaw-playing is false.
Marcus-jaw-question is a number that varies. Marcus-jaw-question is 0.
Gas-released is a truth state that varies. Gas-released is false.
Gas-death-turns is a number that varies. Gas-death-turns is 0.
Marcus-death-sequence is a truth state that varies. Marcus-death-sequence is false.
Marcus-death-turn is a number that varies. Marcus-death-turn is 0.



Chapter 40 - Entering Room 4

After going to the Jaw Breaker Chamber for the first time:
	if the other prisoner is in the Dark Corridor and the other prisoner is conscious and the other prisoner is alive:
		now the other prisoner is in the Jaw Breaker Chamber;
		now the jaw breaker door is locked;
		say "[paragraph break]Marcus follows you into the room. The heavy door SLAMS shut behind you both and locks with a mechanical CLUNK.";
		play the sound of ButtonPress;
		display the Figure of JawBreakerRoomImage;
		say "

A distorted voice crackles from hidden speakers in the ceiling.";
		play the sound of JigsawVoice;
		say "

'Welcome to your penultimate test,' the voice rasps. 'I've watched you both work together. I've seen trust develop between you.

How... touching.

But all good things must end.'

The voice pauses dramatically.

'This game is different. This game... is not for you. This game is for Marcus.'

Marcus's eyes widen in horror.

'The device above that chair is a jaw breaker. Once activated, it will slowly expand, shattering the jaw and crushing the skull. 

Marcus, you will sit in that chair and wear the device. You will answer five questions. Get three wrong... and the device activates.

If Marcus refuses to play, I will release gas into this room. You will both die choking on the floor.

The choice is simple: one dies, or both die.

What will it be?'

[paragraph break]Marcus looks at you, terrified. 'There has to be another way...' he whispers.";
	otherwise:
		say "[paragraph break]As you step into the room, the door locks behind you automatically.";
		play the sound of ButtonPress;
		display the Figure of JawBreakerRoomImage;
		say "

A distorted voice crackles from hidden speakers in the ceiling.";
		play the sound of JigsawVoice;
		say "

'Welcome, Adam. You've made it this far alone. Impressive.

This is the Jaw Breaker. A device designed to expand the human jaw beyond its breaking point.

Your test is simple: Put the device on your head. Answer five questions correctly.

You may get TWO questions wrong. But if you fail a third time... the device activates, and your skull will be crushed.

If you answer all five correctly - or survive with only two wrong answers - a compartment will open in the wall containing a key. That key will unlock both the device and the exit door.

Refuse to play, and you will never leave this room.

Your time starts... NOW.'".



Chapter 41 - Solo Scenario Wearing Device

Wearing device is an action applying to nothing.
Understand "wear device" or "put on device" or "wear jaw breaker" or "put on jaw breaker" or 
"sit in chair" or "sit on chair" or "sit down" or "wear the device" or "put device on" as wearing device.

Check wearing device:
	if the player is not in the Jaw Breaker Chamber:
		say "There's no device here." instead;
	if the other prisoner is in the Jaw Breaker Chamber:
		say "The game is for Marcus, not you." instead;
	if Jaw-device-worn is true:
		say "You're already wearing it." instead.

Carry out wearing device:
	say "You take a deep breath and sit in the cold metal chair.

You reach up and pull the jaw breaker device down over your head.";
	play the sound of ChairMove;
	say "

The moment it settles into place, metal locks SNAP shut around your neck.

You're trapped.";
	play the sound of Pressure;
	say "

The device is cold against your face. You can feel the internal mechanisms pressing against your jaw.

'Good,' the voice says. 'Let us begin.'

[paragraph break]The first question crackles through the speakers...";
	now Jaw-device-worn is true;
	now Jaw-puzzle-activated is true;
	now Jaw-current-question is 1;
	say "

QUESTION 1: What is the capital of France?".



Chapter 42 - Solo Scenario Unlocking Device

Instead of unlocking the jaw breaker device with something:
	if the player is not in the Jaw Breaker Chamber:
		say "There's no device here.";
	otherwise if Jaw-device-worn is false:
		say "You're not wearing the device.";
	otherwise if the second noun is not the jaw key:
		say "That won't unlock the device.";
	otherwise if the jaw key is not carried by the player:
		say "You don't have the key.";
	otherwise:
		say "With trembling hands, you insert the key into the lock mechanism on the side of the device.

CLICK!

The locks release. The jaw breaker lifts away from your head.

You're free.";
		now Jaw-device-worn is false;
		say "

You stand up from the chair, breathing heavily. You survived.

The exit door unlocks with a heavy CLUNK.";
		now the jaw breaker door is unlocked;
		now the jaw breaker door is open.

Unlocking jaw device with is an action applying to two things.
Understand "unlock device with [something]" or "unlock jaw breaker with [something]" or 
"use [something] on device" or "use [something] on jaw breaker" or
"insert [something] into device" or "use key on device" as unlocking jaw device with.

Does the player mean unlocking jaw device with the jaw key: it is very likely.



Chapter 43 - Marcus Scenario Making Choice

Choosing Marcus to play is an action applying to nothing.
Understand "let marcus play" or "marcus play" or "marcus plays" or "choose marcus" or "marcus should play" as choosing Marcus to play.

Choosing self to play is an action applying to nothing.
Understand "play yourself" or "i play" or "i will play" or "choose myself" or "i'll play" or "play myself" as choosing self to play.

Check choosing Marcus to play:
	if the player is not in the Jaw Breaker Chamber:
		say "There's no choice to make here." instead;
	if the other prisoner is not in the Jaw Breaker Chamber:
		say "Marcus isn't here." instead;
	if Marcus-jaw-choice-made is true:
		say "You've already made your choice." instead.

Carry out choosing Marcus to play:
	say "You look at Marcus. He's terrified, but you both know there's no other option.

'Marcus... you have to play,' you say quietly.

Marcus closes his eyes. After a long moment, he nods.

'Okay. Okay, I'll do it. Better one than both.'

He walks slowly to the chair and sits down. His hands are shaking as he pulls the jaw breaker device over his head.";
	play the sound of ChairMove;
	say "

The locks SNAP shut around his neck.";
	play the sound of Pressure;
	say "

'Good,' Jigsaw's voice echoes. 'Let the game begin.'";
	now Marcus-jaw-choice-made is true;
	now Marcus-jaw-playing is true;
	now Marcus-jaw-question is 0.
	

Check choosing self to play:
	if the player is not in the Jaw Breaker Chamber:
		say "There's no choice to make here." instead;
	if the other prisoner is not in the Jaw Breaker Chamber:
		say "Marcus isn't here." instead;
	if Marcus-jaw-choice-made is true:
		say "You've already made your choice." instead.

Carry out choosing self to play:
	now Marcus-jaw-choice-made is true;
	say "'No,' you say firmly. 'I'll play. Not him.'

'How noble,' Jigsaw's voice mocks. 'But I'm afraid that's not an option.'

Before you can react, you hear a HISSING sound.";
	play the sound of GasRelease;
	say "

Gas begins pouring into the room from hidden vents in the ceiling.

Marcus screams. 'NO! What did you do?!'

The gas fills your lungs. It burns. You can't breathe.

Both of you collapse to the floor, gasping, choking.

Your vision blurs. You try to crawl toward the door, but your body won't respond.

Marcus is next to you, convulsing, his face turning blue.";
	now Gas-released is true;
	now Gas-death-turns is 0.

Every turn when Gas-released is true:
	if Gas-death-turns is 0:
		say "[paragraph break]You can try to STRUGGLE or SHOUT, but time is running out...";
		increase Gas-death-turns by 1;
	otherwise if Gas-death-turns is 1:
		say "[paragraph break]'You had one simple choice,' the voice says coldly. 'And you chose wrong.'

Everything goes black.";
		play the sound of Screaming;
		play the sound of GameOver;
		end the story.

Instead of doing anything when Gas-released is true:
	if looking or struggling or shouting:
		continue the action;
	otherwise:
		say "You're choking on the gas. You can barely move.".



Chapter 44 - Marcus Scenario Scripted Death Sequence

Every turn when Marcus-jaw-playing is true and Marcus-jaw-question is less than 6:
	if Marcus-jaw-question is 0:
		say "[paragraph break]The first question crackles through the speakers...

QUESTION 1: What is the tallest mountain in the world?

Marcus thinks for a moment, then answers: 'Mount Everest.'

You hear a confirmation tone.

'CORRECT.'

[paragraph break]Marcus breathes a sigh of relief. 'Okay... I can do this...'";
		now Marcus-jaw-question is 1;
	otherwise if Marcus-jaw-question is 1:
		say "[paragraph break]The second question appears:

QUESTION 2: What is the chemical symbol for water?

Marcus answers confidently: 'H2O.'

You hear a confirmation tone.

'CORRECT.'
";
		now Marcus-jaw-question is 2;
	otherwise if Marcus-jaw-question is 2:
		say "[paragraph break]The third question appears:

QUESTION 3: How many continents are there?

Marcus hesitates. 'Uh... six?'

You hear an error tone.

'WRONG. The correct answer is seven.'";
		play the sound of TrapFail;
		say "

The device tightens around Marcus's head. He gasps in pain.

'One wrong answer. Two more and the device activates.'";
		now Marcus-jaw-question is 3;
	otherwise if Marcus-jaw-question is 3:
		say "[paragraph break]The fourth question appears:

QUESTION 4: What year did World War II end?

Marcus thinks carefully. '1945.'

You hear a confirmation tone.

'CORRECT.'
";
		now Marcus-jaw-question is 4;
	otherwise if Marcus-jaw-question is 4:
		say "[paragraph break]The fifth and final question appears:

QUESTION 5: What is the smallest prime number?

Marcus's face goes pale. He's not sure.

'Um... one?' he guesses.

You hear an error tone.

'WRONG. The correct answer is two.'";
		play the sound of TrapFail;
		say "

The device ACTIVATES.

'NO!' Marcus screams.

You watch in horror as the jaw breaker begins to expand.

Marcus's jaw is forced open wider... wider...";
		play the sound of JawBreaker;
		say "

";
		display the Figure of BearTrapImage;
		play the sound of Screaming;
		say "

CRACK!

His jaw shatters. Blood pours from his mouth.

The device doesn't stop.

CRUNCH!

His skull splits open.

Marcus's body goes limp.";
		play the sound of BodyFall;
		now Marcus-jaw-playing is false;
		now Marcus-death-sequence is true;
		now Marcus-death-turn is 0;
		now Marcus-jaw-question is 6.

Every turn when Marcus-death-sequence is true:
	if Marcus-death-turn is 0:
		say "[paragraph break]Press any key to continue...";
		increase Marcus-death-turn by 1;
	otherwise if Marcus-death-turn is 1:
		say "[paragraph break]He's dead.

You stand there, frozen in shock.

Marcus... the man who helped you survive. The man you trusted. The man you worked with to escape this nightmare.

Gone.

You feel a wave of emotions crashing over you - shock, anger, frustration, grief.

You drop to your knees, staring at his lifeless body.

'Why?' you whisper. 'Why did it have to end like this?'

The silence is deafening.";
		play the sound of SadMusic;
		increase Marcus-death-turn by 1;
	otherwise if Marcus-death-turn is 2:
		say "[paragraph break]Press any key to continue...";
		increase Marcus-death-turn by 1;
	otherwise if Marcus-death-turn is 3:
		say "[paragraph break]You can't move. You can't think. All you can do is stare at what's left of your companion.

The monitors flicker. Jigsaw's face appears.

'Unfortunate. But necessary. You see, Adam, this was never about him surviving. This was about YOU learning the cost of trust.

You trusted him to succeed. He failed. And now he's dead because of that trust.

Remember this lesson well.'";
		increase Marcus-death-turn by 1;
	otherwise if Marcus-death-turn is 4:
		say "[paragraph break]Press any key to continue...";
		increase Marcus-death-turn by 1;
	otherwise if Marcus-death-turn is 5:
		say "[paragraph break]Adam: [bracket]shouting[close bracket] 'I don't give a crap if you covered yourself in peanut butter and had a 15 hooker gang bang!'";
		play the sound of AdamCare;
		say "

The monitors go dark.

The exit door unlocks with a heavy CLUNK.

Marcus is gone. But you can still move forward.";
		now the other prisoner is dead;
		now the jaw breaker door is unlocked;
		now the jaw breaker door is open;
		now Marcus-death-sequence is false.

Instead of doing anything when Marcus-death-sequence is true:
	if looking:
		continue the action;
	otherwise:
		say "You're too shocked to do anything but wait.".
