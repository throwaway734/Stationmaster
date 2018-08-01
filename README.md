# Stationmaster

This repository has the text assets for Stationmaster, an NSFW game available on Patreon.

Welcome, and thank you for checking out the contributor side!

I recommend taking a look at the existing events to get a feel for the scripting. I designed it to be simple to write, but it is a bit terse.

Any new text documents added to the folders under the main "Text" folder will be automatically appended. Generally, please try to keep your own additions to their own files. The giant "Core" file is a relic from when they had to be in the same file, and may be split at some point.

That said, here's a sample:

{reputation > 20}The Traveler
You are going about your normal duties when you are distracted by the sudden awareness of an unauthorized space ship materializing aboard your station. It superficially appears to be an ancient phone booth, but the fact that it was able to so easily bypass your defenses is unnerving. Almost immediately, a man and a woman emerge and begin to look around. It's obvious that they are unaware of where they are, and the man is carefully examining the environment. As they step through the door, you immediately see that the box is larger on the inside.[Addslave|Kiss-o-gram from a primitive world|You enslaved her with her companion after they appeared in a mysterious spacecraft|20/23|80/100|80/100]
	Watch the strangers
		The strangers appear to be scandalized when they see the state of the slaves on your station, and immediately attempt to start a revolution. Your slaves are far too smart to join a random stranger under your eyes though, and your security drones quickly descend on both the man and his companion. 
		The man pulls out a small metal stick and manages to disable one of your drones, but they are far too numerous, and he is quickly overwhelmed. The woman surrenders without a fight after seeing the brutal power of your drones, and they drag her away for processing.
		Your drones attempt to execute the man, but he has some form of failsafe that you're not familiar with. After they tear him limb from limb, he dissolves into dust, and reassembles himself as a woman. You shrug and have the drones drag her away for processing as well. [Addslave|Nigh-indestructible alien with extra organs|You enslaved her with her companion after they appeared in a mysterious spacecraft|20/23|80/100|80/100][select|1]
	Incinerate the strangers
		You simply seal off the corridor that they landed in, and incinerate it. The woman is reduced to dust immediately, but the man dissolves into a glowing storm of nanites several times before eventually joining his companion in the ashes. You have a security drone analyze their ship, which was bizarrely unaffected by the intense heat. It appears to be indestructible and impossible to open, so you jettison it from the station to avoid any surprises.[remove]

The first line is the title of the event. This is what displays in the notification bar. A condition in this line (displayed {like this} ) that is not met will make the randomizer choose a different event. 
The second line is the initial text that is displayed.
For all future lines, the progression is driven by indentation:
  Lines indented at the next level (one tab) will be options shown on dialog buttons
    The next level will be system response
    A second line at the same indentation level will be presented after a "next" button
      And so on.
  This will present as another dialog option.
    And this will be presented as the response to that choice.


There are quite a lot of scripting operations you can do. In general, the syntax will read [method|paramter1|parameter2|etc.]

*Basics:*
name
  Display's the active character's name
AddSlave
  Adds a slave, and selects/displays it if there is no other active character. This one has a ton of parameters, all optional:
  Quirk: The slave's basic description. If there are several of these separated by slashes, the system will pick a random one
  Acquisition: How you came to acquire the slave
  Age: The slave's age range (presented as min/max)
  Obedience: Ditto
  Fear: Ditto
  Name
  Virginity Status: V or N
  Tags: There are a lot of these. More documentation will be incoming later.
br
  Inserts a linebreak. Note that you have to use this to insert a literal linebreak because a carriage return starts the next screen.
close
  Closes the dialog window completely, and shows the new slave queue if there is one.
money
  Edit's player's money. [money|500|Source information (leave blank for "Events")]
influence
  Increase or decrease influence by the provided amount. Usage: [inf|200]
reputation
  Sets the player's reputation [rep|230]
remove
  Removes the selected slave from the player's posession [remove]
  
*Cutscenes:  *
backgroundloop
  Sets the background soundtrack. Available options available in examples.
humansound
  Starts the provided human sound. Options are:
  	crying
    weeping
    painfulsex
    sex
    wince
    gasp
    grunt
    scream
    Idle
    CutoffScream
    gaggedsex
    Gaggedscream
    Punch
    Gasping
    begging
    beggingsex
    cough
    coughing
    fear
    rage
    snoring
    screams
pose
  Sets the visible character's pose. Options are
  	cowering
    dance
    facedownonground
    keepback
    dronehanging
    dronestruggle
    droneupsidedown
    idle
    boundseated
    dance
    sleeping
    doggy
    doggyprep
    doggyrape
    doggyrapeprep
    dronedoggy
    dronedoggyprep
    dronemissionary
    dronemissionaryprep
    missionary
    missionaryprep
    missionaryrape
    missionaryrapeprep
    torture
playsound
  Plays a one-time sound. Options available in event samples
endhumansound
  Shuts off all human sounds
environment
  Loads an environment into the notification
strip
  Removes all clothes from the selected character
clothe
  Clothes the selected character.  
expression
  Sets the viewed character's expression. Options are:
    Acceptance
    Defiant
    Fear
    Pain
    Pleading
    Rage
    Scream
    Submission
    Anger
    Idle
hide
  Hide the selected character
select
  Selects one of the slaves added by the current event (zero-indexed)
sex
  Triggers sex with the active character. This takes virginity, and rolls pregnancy
show
  Shows the selected slave

*Variables:*
set
  Sets a variable [set|isOpen] 
unset
  Removes a variable. [unset|isOpen]
var
  Switches based on a variable set with [set]. These are global. [var|isOpen|The door is open|The door is closed]

*Switches:*
random
  Randomly selects between the provided parameters. Usage: [Random|option1|option2|option3]
citizen
  Switch based on whether the selected character is a citizen: [citizen|This character is a citizen|This character is not a citizen]
fearswitch
  Switches between values based on the selected slave's fear. Usage: [fearswitch|Unafraid|Kind of afraid|Really afraid]
hastag
  Switch based on whether the active character has a tag. Usage: [hastag|insane|This character is insane|This character is not insane]
lactating
  Switch based on lactation. [lactating|This character is lactating|This character is not lactating]
obedienceswitch
  [obedienceswitch|Disobedient|Somewhat Obedient|Obedient]
peaceswitch
  [peaceswitch|The player is at peace with the selected faction|The player is not at peace with the selected faction]
playercharacter
  [playercharacter|The selected character is the player character|The selected character is not the player character]
slave
  [Slave|This is a slave|This is not a slave]
tourist
  [tourist|This character is a tourist|This character is not a tourist]
virgin
  [virgin|This character is a virgin|This character is not a virgin]
relationshipswitch
  Switches based on your relationship with the selected faction. [relationshipswitch|hate|mediocre|love]
  
  
  
  
*Slaves:*
acquisitionindicator 
  Shows how the selected slave was acquired
addtag
  Adds a tag to the given slave. Formatted as [AddTag|New Tag]
ageindicator
  Display's the selected character's age. Only works if there is a selected character.
assign
  Sets the selected character's assignment to the given value. Case-sensitive.
assignmentindicator
  Shows the selected character's assignment. Only works on slaves.
fear
  Adds or subtracts the value from the selected slave's fear (usage: [fear|-14])
obedience
  Adjusts the obedience of the selected slave
fearindicator
  Shows the friendly display of the selected slave's fear ("Unafraid")
obedienceindicator
  Displays the obedience of the selected slave
familytree
  Shows the viewed character's family tree
globalfear
  Like fear, but operats across all slaves. Not just the selected one.
globalobedience
  Like globalfear, but obedience
charismaindicator
  Shows the character's charimsa
lactationindicator
  Returns something like "Lactating at 20% efficiency"
tagindicator
  Shows the tags of the selected character
pregstring
  Shows the selected slave's pregnancy amount (as "3rd trimester")
prestige
  Adjusts the prestige of the selected slave
prestigeindicator
  Displays the prestige of the selected slave
  
  
*Esoterics:*
body
  Shows the name of the selected celestial body
bodyfear
  Same, but shows the fear
bodyobedience
  Ditto, but obedience
bodyquirk
  Ditto, but the quirk
bodytypedisplay
  Ditto, but the type.
addartifact
  Adds an artifact with the given name to the inventory (note that, unlike most commands, this is case-sensitive)
defense
  Shows the defensive strength of the selected body
government
  Shows the name of the selected government
hidebody
  Hide the selected body
economy
  Shows the economic strength of the selected body
hideassistant
  Hide the assistant model.
hisher
  Returns "his" if the character is male, and "her" if the character is female.
showassistant
  Shows the assistant model in the notification window
showbody
  Displays the selected body in the notification window
resetcamera
  Sets the camera to its default state
restart
  Restarts the event tree
relationship
  Adjusts the relationship with the selected faction. [relationship|20]
removebody
  Removes the selected body from the player's posession
removetag
  Removes the given tag from the selected character [removetag|insane]


  

Legal Stuff:

The text in this repository is presented for demonstration purposes. StationmasterDev retains copyright over first-party content, and it is not to be used in whole or in part within other work without express written permission. By comitting to this repository, you grant a non-exclusive license to StationmasterDev to use the uploaded content within this or any future games, or in any associated materials (such as screenshots, press releases, and other media).
