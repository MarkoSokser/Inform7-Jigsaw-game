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
Whatever comes next, you have left the cell behind.".



Chapter 3 - The Other Prisoner

The other prisoner is a man in the Cell.
The other prisoner is fixed in place.

The other prisoner can be conscious or unconscious.
The other prisoner is unconscious.

The description of the other prisoner is
"A man is chained beside you, his body limp and unnaturally still.  
His head hangs to one side.  
His breathing is shallow, barely noticeable.";

Understand "man" or "prisoner" or "other man" as the other prisoner.



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
		say "That accomplishes nothing." instead.

Carry out trying to wake:
	say "You grab his shoulder and shake him hard.  
His body reacts, but his eyes never open.".

After trying to wake the other prisoner:
	say "Whatever they injected into him has left him completely helpless.".


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
	play the sound of SelfCut;
	say "You bite down and force the saw through bone and flesh.
The pain is indescribable.
You collapse - but the chain falls away.".




Chapter 12b - Trying to Cut the Chain

Cutting the chain is an action applying to one thing.
Understand "cut [something]" or "cut through [something]" or "saw [something]" or "saw through [something]" as cutting the chain.

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
	if Player-cut is true:
		say "You are losing too much blood. You can barely stand.
You don't have the strength to drag him.
You need to get out before you bleed out completely." instead;
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




Chapter 15 - Game Start

Use no scoring.

Figure of CellImage is the file "cell.png".

When play begins:
	say "You regain consciousness to the sound of chains and distant machinery.[paragraph break]";
	say "A distorted voice fills the room.";
	play the sound of TapeVoice;
	display the Figure of CellImage.

