here's a list of the things i wanna do today:
- need to add logic for what to do in a fault condition
- need to integrate fault condition with HMI
- HMI:
	- add start stop fault etc condition LEDs to the HMI
	- add a small timer next to each conveyor to tell the remaining delay time

------
what do i want in the fault condition?
	when a conveyor is at fault, i want the conveyors behind the faulty one to stop immediately, and the ones infront of it to continue working.

---
there's a problem with the stop condition when it is called from the start condition -it doesnt clear the objects on it. i think this has to do with the timer memory of the conveyors in stop condition. i think they get reset.

---
sir essentially wants me to write pseudocode for reading and writing onto the PLCs. think up of your own functions and stuff. ig what i can do is write C code that reads from 4 memory spaces and compares them -or better i could write code to read a memory space from 4 STM32s, i think i have 4 STM32s -and then write a GUI code in C to show the difference between the 4 memory spaces.