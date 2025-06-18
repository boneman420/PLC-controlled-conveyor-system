##### `[need to record the progress from before 26 may]`

#### 26 may
- IO devices - PLC to PLC communication using hardware
	- PROFINET basics
	- programming a PLC
	- limitations of PLCsim
#### 27 may
- tried out get/put commands
- learnt about using datablocks with get/put commands
#### 28 may
- learnt about TCP communication
	- TCON, TDISCON, TSEND, TRCV etc
#### 29 may
- discussed problem statement for project with mentor
- made a detailed document of the problem statement


##### 2 June
- installed factoryIO, set up everything with PLC
- made the first half of start condition

##### 3 June
- added blinking lamp block
- upgraded the conveyor function block
- tried changing the logic to SCL (failed)

##### 4 June
- remade the project for the third time, this time using FBD (FBD seems better than LAD and SCL)
- haven't implemented any lamp logic. but got very far with the conveyor logic
- basic conveyor logic is still not complete yet, i got very confused with a lot of variables, need to restart
- all changes up till now are in V3
-----
- restarted with solid logic for cascaded downstream start condition - V4.
- all the motors stop in a cascaded downstream manner
- need to implement cascaded upstream stop condition

##### 5 June
- got the start and stop functionality working properly (without lamp)
- saved this progress and started V4.1
- implemented start/stop/low power condition 90% (there might be some edge cases)
- saved this progress and started V4.2
- implemented start and stop lamp control logic (june 5 notes)
- implemented logic for start and stop button lights
- saved this progress and started V4.3
---------
some changes mentor asked:
- stop button shouldn't stop all the conveyors immediately. the conveyors should always clear what's on them 
-----
- added 4 more conveyors, made a U shaped system
- there's still a small bug with stopping this system
----
more changes:
- add a carousel to the conveyors, something the objects can keep looping in

##### 6 June
- added git to the project
- added different delay for different sized conveyors
- changed memory elements (system state and standard parameter) to a datablock instead of using plc tags
- saved the progress so far as V5.1
- removed the use for current sensor on each conveyor -the conveyor runs for a fixed time when the preceding sensor detects an object
- you can now start the system in low power mode
- saved the progress and started V5.2
-----
more changes (or additions):
- have two carousels now, and a divider which divides the baggage into a fixed ratio
-----
the stop condition needs some fixing

##### 9 June
- checked out sorting mechanisms, pop up wheel sorter is the best for simulation use
- TASK: C script for a system management application in Guwahati airport
- manager told ill get to do a presentation of my project by the end of my internship


##### 10 June
- fell back to ap19 V5.2 and factoryIO V2 because i was getting too distracted with a bigger system
- stop condition, dieback condition and HMI integration needs to be worked on

- removed a lot of unnecessary variables from the system state datablock
- fixed stop condition by adding sensor control function block to it
- saved the progress so far and started V5.3
----
- sir suggested to use a DB with structs to transmit the data to a HMI which is a good idea
- use underscores and not spaces
----
- added a motor fault which triggers when the motor is supposed to be active but there's no feedback from the encoders
- basic HMI implementation -it displays the running/stopped of each conveyor

##### 12 June
- the HMI conveyor elements turn yellow when there's a fault
- added a timer to the HMI that shows the conveyor delay left
- fixed a bug where start -> stop condition would stop the conveyor too quickly
- implemented fault condition -it's total chaos. it's a mess
##### 16 June
- fixed the fault condition.
- added a low power mode condition to each conveyor
- added blue color which indicates that a conveyor is in low power mode
- there is a bug where system goes into fault condition sometimes when starting
- saved progress and started v5.4
- added more logic for lamp control network to include low power mode
- added low power mode to conveyor motor condition -it shows as blue in the HMI
- cleared the fault condition during start up bug by just adding a long delay 
- new bug where the hmi does not show blue conveyors when the system is in low power mode
- fixed the above bug by adding a delay to the reset button

- i messed up the lamp control logic a bit by not reading through what chatgpt gave me. gotta fix that
- need to optimize the program a bit, compress logic into function blocks a bit for the next version
- need to implement this on a bigger conveyor system

##### 17 June
- fixed lamp control logic
- system is not going into fault condition properly
- fixed the fault condition bug

- when resetting fault condition the conveyors forget the objects on them and are dependant on the sensor to come move them -this can be solved by activating the conveyor for some time when there's a falling edge on reset button
- need to build standard test cases

- saved the progress and started v6
- renamed everything to use underscores instead of spaces
- compressed lamp control logic into one function block
- saved the progress and started v6.1
---
new changes:
- combine all the conditions into the conveyor FB (like the real program sir showed)
- start condition should start with a constant 1 second delay
- each conveyor should have it's own on and off timer
---
- trying to make the new compressed system.
##### 18 June
- compressed all logic in each condition intro the conveyor control FB
- compressing the main loop FC logic
- optimized the main loop FC logic by a lot
- saving progress and started v6.2
- need to define standard test cases
- figured out something where i can define system states and all the control blocks can be controlled using system states. also discovered word logic operations
- standard cases defined (WITHOUT BAGGAGE). now need to test the current system against the standard cases and fix the system so far.
---
- im gonna have to remake the conveyor control FB. im gonna have to remake the entire program once. most of these test conditions will fail.

---
- cancel plans. the presentation is tomorrow at 4pm. need to find the most stable version and do bug fixes on it


- removed sensor control from stop logic
- made on delay and off delay of conveyor control retain it's values
- added logic to remove the need for a low power switch
---
- fixed a lot of bugs and made the required changes for tomorrow's session
- start to low power still has a bug where the conveyors forget the sensor value before
- mostly fixed that bug but it doesnt show the 1s delay on hmi in start condition
- saved progress and started v6.3
- compressed fault set reset logic into the conveyor blocks
- lamp logic got messed up. need to fix that
	- that lamp logic took me almost half an hour to fix, because the problem was rooted deep. whenever you wanna use set reset in an FB always use inout or static. sigh.

- **version 6.3 is the most stable version so far** 
- saved progress and started v6.4
- compressed all the system control networks into one FB
- saved this progress and started v6.5
- compressed conveyor control condition logic into conveyor FB
- organized everything into folder groups
- start to stop is not working properly
- fixed the above
- added HMI connections properly
- cascaded stop not working as intended but it's okay

tomorrow:
before lunch:
- get ppt reviewed
- type out what to speak
after lunch
- practice for the meeting
throughout:
- program:
	- add useful indicators to HMI instead of low power mode and all conveyors running
	- implement this into a bigger system with at least 10-15 conveyors and a carousel
	- maybe fix the cascaded stop issue
