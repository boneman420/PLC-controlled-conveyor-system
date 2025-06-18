standard test cases:

i mean, there are 4 conditions and 16 possible combinations. just gotta figure out what happens for al 16 combinations

1. stop to start
	- there is a safety delay of 3S (need to be increased later on)
	- motors start upstream to downstream in a cascaded manner with 1 second delay
	- the hmi displays the time left for nth motor to start on the nth motor
	- lamp flashes green till motors start and stays green when everything is running
2. stop to low power
	- motors dont run
	- motors in the hmi turn blue
	- lamp flashes green
3. stop to fault
	- not possible

4. start to stop
	- motors stop downstream to upstream in a cascaded manner with a set delay for each conveyor length
	- the hmi displays time left for nth motor to turn off on the nth motor
	- green lamp turns off. lamp flashes red till all motors are turning off, then it stays red when all motors turn off
5. start to low power
	- all conveyors immediately go into low power mode (turn blue) and stop running
	- the hmi shows all conveyors as blue except for the ones handling bags
	- lamp flashes green
6. start to fault
	- the fault conveyor turns yellow
	- the conveyors before the fault turn off immedietly
	- the conveyors after the fault go into low power mode (turn blue)
	- system start/stop memory is reset -the only state from fault is into stop
	- the fault lamp flashes yellow. stop lamp stays red

7. low power to start
	- same as stop to start
8. low power to stop
	- all conveyors stop and go red on the HMI
9. low power to fault
	- same as start to fault

10. fault to stop
	- when fault condition is triggered the stop condition is set true
	- when reset button is pressed the system stays in stop condition


#### June 18 testing (WITHOUT BAGGAGE)
1. pass
2. pass
3. pass
4. pass
5. pass
6. pass
7. pass
8. -
9. fail


---
do i have time for remaking the entire program?
the presentation is tomorrow at 4
i think it's best if i do bug fixes on v6.2, add the new features and implement it on a bigger system

---
##### V6.2 test with baggage
1. pass
2. pass
3. 
4. -
5. -
6. -
7. fail
8. -
9. -
---



| system start/stop mem (A) | all conv running (B) | some conv running (C) | low power mode enable (F) |
| ------------------------- | -------------------- | --------------------- | ------------------------- |
| 0                         | 0                    | 0                     | 0                         |
| 0                         | 0                    | 1                     | 1                         |
| 0                         | 1                    | 0                     | x                         |
| 0                         | 1                    | 1                     | 1                         |
| 1                         | 0                    | 0                     | 1                         |
| 1                         | 0                    | 1                     | 1                         |
| 1                         | 1                    | 0                     | x                         |
| 1                         | 1                    | 1                     | 0                         |

