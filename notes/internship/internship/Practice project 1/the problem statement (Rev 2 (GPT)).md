# conveyor belt system with basic controls and conditions

design a conveyor belt system with the following specifications
### consists of
- N conveyors of length L moving at speed S
	- object detector on each conveyor
	- motor isolator
	- motor running feedback
	- motor fault feedback

- control panel
	- start push button with illumination
	- stop push button with illumination
	- fault reset with illumination
	- power save toggle
	- lamp
		- system run
		- system stop
		- fault
		- buzzer
	- HMI with a diagram of the conveyors and each conveyor's status


![[project 1.png]]
### working logic

#### start condition
- activates when the start push button is pressed
- the start button illuminates immediately
- system run lamp flashes for 10 seconds as a warning
- conveyors start in a cascading manner from upstream to downstream with a delay of `2*L/S` seconds between them
- once all conveyors are running:
	- system run lamp stops flashing and stays on
	- conveyors enter running condition

#### running condition
- all conveyors continue running unless another condition is triggered

#### power save condition
- activates when power save toggle is enabled
- if the sensor feedback of the `n-1-th` conveyor is 0 for `2*L/S` seconds:
	- the `n-th` conveyor stops to save power
	- running feedback = 0, fault feedback = 0 on the `n-th` conveyor
- if the sensor feedback on the `n-1-th` conveyor turns 1:
	- the `n-th` conveyor resumes running

#### dieback condition
- activates when the fault feedback of the `n-th` conveyor is 1
- the `n-1-th` conveyor stops when its sensor detects an object (sensor feedback = 1)
- actions:
	- fault lamp starts blinking
	- buzzer beeps once
	- fault feedback of the `n-1-th` conveyor turns 1
- the cycle continues upstream until conveyor 1
- once all conveyors downstream to the `n-th` conveyor have fault feedback = 1:
	- upstream conveyors enter power save mode (if not already)
	- system run lamp turns off
	- fault lamp stays on
	- buzzer beeps twice every 1 minute
	- fault reset button illuminates

after the fault at the `n-th` conveyor has been cleared:
- the system remains in fault condition
- operator must press the fault reset button
- upon pressing:
	- fault reset lamp starts blinking
	- buzzer beeps once
	- upstream conveyors of the `n-th` exit power save mode in a cascading manner with `2*L/S` second delay
	- after another `2*L/S` seconds, the `n-th` conveyor:
		- starts running
		- running feedback = 1
		- fault feedback = 0
	- after another `2*L/S` seconds, downstream conveyors return to their previous condition (running or power save)
	- fault reset button stops illuminating
	- fault reset lamp turns off
	- system run lamp turns on

#### stop condition
- activates when the stop push button is pressed
- stop button illuminates immediately
- system run lamp starts blinking
- conveyors stop in a cascading manner from downstream to upstream:
	- each conveyor stops when its sensor detects an object (sensor feedback = 1)
- once all conveyors have stopped:
	- system run lamp turns off
	- system stop lamp turns on
	- buzzer beeps once
