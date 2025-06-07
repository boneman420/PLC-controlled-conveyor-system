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