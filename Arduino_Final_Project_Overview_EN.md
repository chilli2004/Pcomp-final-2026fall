# Arduino Final Project | The Assembled Body

## Project Concept

A horror investigation game that combines a physical installation with storytelling on a computer. The player is a police officer examining a strange body assembled from different people's body parts, guided remotely by a detective. As the investigation progresses, the player discovers that the detective is the killer—and that they are his next intended victim.

Estimated experience length: 5 minutes.

## Physical Installation and Computer Interface

- **Physical installation:** An enclosure with limbs and a head attached in unusual positions. It has four interactive areas.
- **Computer interface:** A case terminal made in p5.js, featuring the detective's dialogue, investigation tasks, evidence, and sound. Players examine the physical object and click the screen to advance dialogue.
- **Opening:** The player's police ID and badge number, such as 0714, appear at the beginning to set up the final reveal.

## Four Physical Interactions

| Step | Player Action | Story Response | Simple Hardware |
|---|---|---|---|
| 1 | Press or hold the hand | A missing person's file appears, revealing that the body parts belong to different people. | A button hidden in the palm |
| 2 | Press a wound on the head | A voice says, “Don't listen to him.” The detective dismisses it as an old recording. | A button hidden beneath the wound |
| 3 | Open the chest compartment | The player discovers an empty space for a missing body part and receives a clue about where to look next. | The closed lid holds down a button; opening it releases the button. |
| 4 | Open a small hidden panel | The player finds their own badge number on a physical label, triggering the ending. | The closed panel holds down a button; opening it releases the button. |

## Ending

The hidden label reads:

> Missing component  
> Source: Officer 0714

The detective drops his act, and the player realizes that they are part of his plan.

The screen displays “The final donor has arrived,” while an LED inside the installation begins pulsing like a heartbeat.

It's all over!

## Communication Between Arduino and the Computer

- **Arduino → PC:** Four buttons detect physical interactions and send corresponding messages over USB serial.
- **PC → Arduino:** At the ending, the computer sends a command to trigger the LED's heartbeat pattern.

Arduino handles input detection and lighting. p5.js handles the story, visuals, sound, and interaction sequence.

## Keeping Interactions in Order

p5.js tracks the current step and only accepts the action required for that step.

- **An action happens too early:** It does not advance the story and is not saved to trigger automatically later.
- **A clue or dialogue is being shown:** Physical inputs are temporarily ignored. The next step becomes active after the player clicks “Continue.”
- **An input must be repeated:** Buttons must be released and pressed again. If a panel was opened too early, the player must close and reopen it at the correct step.

Software cannot prevent players from seeing the physical badge number early. One possible solution is a small lock on the final panel, with its key hidden in the chest compartment in Step 3. This physical design is still to be confirmed.

## Minimum Build

- Four buttons
- One LED with a current-limiting resistor
- An Arduino board and USB connection
- A physical enclosure with body-part props

First, build a simple working connection: one button triggers dialogue on the computer, and the computer controls the LED. Then expand it into the four-step story.

No complex moving mechanisms or real identity recognition are needed. The badge number is part of the player's fictional role.

