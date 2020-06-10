# doors
Work in progress: A clever self-contained Python3 procedural generation "dungeon crawl" demo. Generates state on-the-fly, stores player state inside itself. User commands are kept as "inline metadata".

# Use
Intended to be called once per command, so I can later hook it up to a remote channel (chat room, etc).

Here is a sample run:

[garyd@dizzymouse doors]$ ./doors help

Demo - Self-contained procedural generation dungeon crawl

Usage: doors <command>

  look                        Show current room/status

  look <N|E|S|W>              Look north, east, south, west

  open <N|E|S|W>              Unlock a door (or try)

  go   <N|E|S|W>              Go in direction (or try)

  take <object>               Take thing, if hands are free

  drop <object>               Drop whatever you're holding
  listen <N|E|S|W>            Listen at door in direction
  exits                       "Look" in all directions
  dump <N|E|S|W>              Dev: Dump room in direction
  keys                        Dev: Dump player keys
---------------------------------------------------------------
Tips:
  You can also just use N, E, S, or W to go in those directions.
---------------------------------------------------------------

[garyd@dizzymouse doors]$ ./doors look

? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0

[garyd@dizzymouse doors]$ ./doors exits
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway
To the e is The Small Stinky Garden
To the s is no exit
To the w is The Small Obscure Crypt

[garyd@dizzymouse doors]$ ./doors look n
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway

[garyd@dizzymouse doors]$ ./doors listen n
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway
You listen to the n, and hear something.

[garyd@dizzymouse doors]$ ./doors go n
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway
? Open this door with "open <N|E|S|W> <code>"
? Hint: nlkuco

[garyd@dizzymouse doors]$ ./doors open n unlock
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway
! Well done! You have unlocked The Cramped Fancy Causeway
You've acquired the key to The Cramped Fancy Causeway!

[garyd@dizzymouse doors]$ ./doors go n
? 0x4 | The Modest Wicked Skyway | 4228 | Occupied: 0 | Pit: 0
To the n is The Cramped Fancy Causeway
! Key in collection 4195
! Granting access, updating position
Game state updated with PlayerPosition 0 3

[garyd@dizzymouse doors]$ ./doors exits
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591807993
To the n is The Miniature Worst Skydome
To the e is The Large Stuffy Corridor
To the s is The Modest Wicked Skyway
To the w is The Modest Expensive Entryway

[garyd@dizzymouse doors]$ ./doors listen e
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808065
To the e is The Large Stuffy Corridor
You listen to the e, and hear nothing.

[garyd@dizzymouse doors]$ ./doors go e
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808082
To the e is The Large Stuffy Corridor
? Open this door with "open <N|E|S|W> <code>"
? Hint: asemes

[garyd@dizzymouse doors]$ ./doors open e sesame
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808106
To the e is The Large Stuffy Corridor
! Well done! You have unlocked The Large Stuffy Corridor
You've acquired the key to The Large Stuffy Corridor!

[garyd@dizzymouse doors]$ ./doors go e
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808111
To the e is The Large Stuffy Corridor
! Key in collection 4198
! Granting access, updating position

[garyd@dizzymouse doors]$ ./doors look
? 1x3 | The Large Stuffy Corridor | 4198 | Occupied: 0 | Pit: 0

[garyd@dizzymouse doors]$ ./doors go w
? 1x3 | The Large Stuffy Corridor | 4198 | Occupied: 0 | Pit: 0
To the w is The Cramped Fancy Causeway
! Key in collection 4195
! Granting access, updating position
Game state updated with PlayerPosition 0 3

[garyd@dizzymouse doors]$ ./doors look
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808157

[garyd@dizzymouse doors]$ ./doors keys
? 0x3 | The Cramped Fancy Causeway | 4195 | Occupied: 1 | Pit: 0
! Room occupied
  Name	 dobuci 	Seed 4195
  Wields fist 	AC 15
  HP	 49
  STR 	 9
  DEX 	 20
  CON 	 20
  INT 	 18
  WIS 	 10
  CHA 	 10
  Action 1591808179
Player keys: ['4195', '4198']

