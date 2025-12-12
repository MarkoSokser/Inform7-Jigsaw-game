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
	if the exit door is revealed:
		say "[line break]- An exit door to the north".

The Exit Hall is a room.
The description of the Exit Hall is
"A narrow concrete corridor stretches into darkness.
The air is colder here, heavier.
Whatever comes next, you have left the cell behind.

To the north, you can see a heavy metal door marked with biohazard symbols.
Behind it, you hear the faint hum of fluorescent lights.".

Rule for listing nondescript items when the location is the Exit Hall:
	if the exit door is marked for listing:
		now the exit door is not marked for listing;
	if the other prisoner is marked for listing:
		now the other prisoner is not marked for listing.

After looking in the Exit Hall:
	if the other prisoner is in the Exit Hall:
		say "[paragraph break]Marcus lies unconscious on the cold concrete floor, his bandaged ankle still seeping blood.".

The Medical Chamber is a room.
The Medical Chamber is north of the Exit Hall.

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
		say "[paragraph break]Four colored pressure plates (RED, BLUE, GREEN, and YELLOW) glow ominously on the floor near the exit door.";
	if the bloody note is in the Medical Chamber:
		say "[paragraph break]You can see a bloody note on the floor.".



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

The exit door is a door.
The exit door is north of the Cell and south of the Exit Hall.
The exit door is closed and unlocked.

The exit door can be revealed or unrevealed.
The exit door is unrevealed.

The exit door can be collapsed or standing.
The exit door is standing.

Rule for listing nondescript items when the exit door is unrevealed:
	if the exit door is marked for listing:
		now the exit door is not marked for listing.

Report opening the exit door:
	do nothing instead.


Chapter X - Hidden Exit

Instead of going north from the Cell when the exit door is unrevealed:
	say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going south from the Cell when the exit door is unrevealed:
		say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going west from the Cell when the exit door is unrevealed:
		say "The wall is solid concrete. There is no exit there. Its not like this chain will let you".
Instead of going east from the Cell when the exit door is unrevealed:
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
		now the exit door is revealed;
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

Instead of going through the exit door when the chain is in the Cell:
	say "The chain prevents you from reaching the door.".

Before going through the exit door:
	if the other prisoner is being-dragged:
		now the other prisoner is in the Exit Hall.

Instead of going through the exit door:
	now Ceiling-descending is false;
	now the exit door is collapsed;
	if the other prisoner is being-dragged:
		say "You throw yourself through the doorway, dragging him with you, as the ceiling crashes down behind you.";
		say "You both survived - at a terrible cost.";
	otherwise:
		say "You throw yourself through the doorway as the ceiling crashes down behind you.";
		say "You survived - at a terrible cost.";
	continue the action.

Instead of going south from the Exit Hall when the exit door is collapsed:
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
	if Prisoner-cut is true:
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
[paragraph break]You are alone. The other prisoner... you left him behind.".




Chapter 18 - Bleeding Mechanic

Every turn when the player is in the Medical Chamber:
	increase Chamber-turns-elapsed by 1;
	if the other prisoner is bleeding and the other prisoner is unbandaged:
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




Chapter 19 - Bandaging

Bandaging is an action applying to one thing.
Understand "bandage [someone]" or "wrap [someone]" or "stop bleeding of [someone]" or 
"use gauze on [someone]" or "apply gauze to [someone]" or "close wound of [someone]" as bandaging.

Bandaging yourself is an action applying to nothing.
Understand "bandage myself" or "bandage me" or "wrap myself" or "stop my bleeding" or 
"use gauze on myself" or "apply gauze to myself" or "close my wound" or "bandage my ankle" or "wrap my ankle" as bandaging yourself.

Check bandaging yourself:
	if Player-bleeding is false:
		say "You're not bleeding." instead;
	if the player does not carry the medical gauze:
		say "You need something to stop the bleeding with." instead.

Carry out bandaging yourself:
	if the player carries the medical tape:
		now Player-bandaged is true;
		now Player-bleeding is false;
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
			say "[paragraph break]The plates flash GREEN in sequence. You hear a heavy CLUNK as the door mechanism unlocks.
'You did it!' Marcus shouts. 'The door is open!'";
			now the chamber exit door is unlocked;
			now the chamber exit door is puzzle-unlocked;
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

