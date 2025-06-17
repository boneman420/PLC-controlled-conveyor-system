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