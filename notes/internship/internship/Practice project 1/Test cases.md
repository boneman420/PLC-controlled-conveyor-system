## (WITHOUT BAGGAGE)
1. stop to start
	- there is a safety delay of 3S (need to be increased later on)
	- motors start upstream to downstream in a cascaded manner with 1 second delay
	- the hmi displays the time left for nth motor to start on the nth motor
	- lamp flashes green till motors start and stays green when everything is running
2. stop to low power
	- safety delay
	- motors dont run
	- motors in the hmi turn blue
	- lamp flashes green

3. start to stop
	- motors stop downstream to upstream in a cascaded manner with a set delay for each conveyor length
	- the hmi displays time left for nth motor to turn off on the nth motor
	- green lamp turns off. lamp flashes red till all motors are turning off, then it stays red when all motors turn off
4. start to low power
	- all conveyors immediately go into low power mode (turn blue) and stop running
	- the hmi shows all conveyors as blue except for the ones handling bags
	- lamp flashes green
5. start to fault
	- the fault conveyor turns yellow
	- the conveyors before the fault turn off immedietly
	- the conveyors after the fault go into low power mode (turn blue)
	- system start/stop memory is reset -the only state from fault is into stop
	- the fault lamp flashes yellow. stop lamp stays red

6. low power to start
	- same as stop to start
7. low power to stop
	- all conveyors stop immediately 
	- all conveyors stay red on the HMI
	- lamp stays red
8. low power to fault
	- same as start to fault but the trigger is a baggage going over it.

9. fault to stop
	- when fault condition is triggered the stop condition is set true
	- when reset button is pressed the system stays in stop condition
## (WITH BAGGAGE)
1. stop to start
	- there is a safety delay of 3S (need to be increased later on)
	- motors start upstream to downstream in a cascaded manner with 1 second delay
	- the hmi displays the time left for nth motor to start on the nth motor
	- lamp flashes green till motors start and stays green when everything is running
	- bag:
		- no effect of baggage on the conveyor
2. stop to low power
	- safety delay
	- motors dont run
	- motors in the hmi turn blue
	- lamp flashes green
	- bag:
		- nth conveyor runs for a fixed time when n-1th sensor detects bag

3. start to stop
	- motors stop downstream to upstream in a cascaded manner with a set delay for each conveyor length
	- bag:
		- the conveyors are sensor controlled till all the existing bags are cleared
		- new bags dont trigger the start sensor
	- the hmi displays time left for nth motor to turn off on the nth motor
	- green lamp turns off. lamp flashes red till all motors are turning off, then it stays red when all motors turn off
4. start to low power
	- all conveyors immediately go into low power mode (turn blue) and stop running
	- bag:
		- the sensory memory is used to keep moving all the bags in the middle of the conveyors
		- nth conveyor runs for a fixed time when n-1th sensor detects bag
	- the hmi shows all conveyors as blue except for the ones handling bags
	- lamp flashes green
5. start to fault
	- the fault conveyor turns yellow
	- the conveyors before the fault turn off immedietly
	- the conveyors after the fault go into low power mode (turn blue)
	- bag:
		- the conveyors before the fault dont move bags
		- the conveyors after the fault are sensor controlled
	- system start/stop memory is reset -the only state from fault is into stop
	- the fault lamp flashes yellow. stop lamp stays red

6. low power to start
	- same as stop to start
	- bag:
		- no effect of bags
7. low power to stop
	- all conveyors stop
	- bag:
		- the conveyors are sensor controlled till all the existing bags are cleared
		- new bags dont trigger the start sensor
	- all conveyors stay red on the HMI
	- lamp stays red
8. low power to fault
	- the fault conveyor turns yellow
	- the conveyors before the fault turn off immedietly
	- the conveyors after the fault go into low power mode (turn blue)
	- bag:
		- the conveyors before the fault dont move bags
		- the conveyors after the fault are sensor controlled
	- system start/stop memory is reset -the only state from fault is into stop
	- the fault lamp flashes yellow. stop lamp stays red

9. fault to stop
	- when fault condition is triggered the stop condition is set true
	- when reset button is pressed the system stays in stop condition
	- bag:
		- the conveyors are sensor controlled till all the existing bags are cleared
		- new bags dont trigger the start sensor