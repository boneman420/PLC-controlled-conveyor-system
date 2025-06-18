time: 40 minutes

- introduction
- briefing
- demonstration
- question and answer

#### introduction
- introduce myself
- mention mentor and what I worked on
#### Briefing
- the problem statement
	- what the scenario consists of: control panel, conveyors, HMI
	- the logic each work on
- the tools used
	- small brief about factoryIO
	- PLC sim, TIA portal
- program
	- explain the parts of the program
	- show how the program is modular and expandable
#### Demonstration
- demonstrating the general use
	- start the system from a complete stop
		- point out the cascaded start
	- send items through the conveyors one by one for a short while
	- after a good number of items are on the conveyors, stop sending items to demonstrate low power condition
	- continue sending items (at a slower rate this time), and inject an off failure to demonstrate the fault condition
	- clear the fault and show the reset button functionality
	- reset the system and show how the conveyors start again
	- press stop button and stop sending items to show the cascaded stop