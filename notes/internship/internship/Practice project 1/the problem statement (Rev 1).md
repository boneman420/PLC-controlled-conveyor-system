# conveyer belt system with basic controls and conditions

design a conveyor belt system with the following specifications 
### consists of
- N conveyers of length L moving at speed S
	- object detector on each conveyer
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
	- HMI with a diagram of the conveyers and each conveyer's status
### working logic
##### start condition
- this condition activates when start push button is pressed
- the start button illuminates immediately 
- the system run lamp flashes for 10 seconds before starting as a warning
- the conveyers start in a cascading manner from upstream to downstream with `2*L/S` seconds (to clear the objects off the conveyer) delay between them
- once all conveyers are moving, the system run lamp stops flashing and stays on
- the conveyers move into running condition
##### running condition
- all the conveyers keep running till there is a change in condition
##### power save condition
- the condition activates when power save toggle is enabled
- when the sensor feedback `n-1th` conveyer is 0 for `2*L/S` seconds, the `nth` conveyer stops to save power
- running feedback is 0, fault feedback is 0 on the `nth` conveyer
- when the sensor feedback on `n-1th` conveyer is 1, the `nth` conveyer resumes running
##### dieback condition
- this condition activates if the fault feedback of `nth` conveyer is 1
- the `n-1th` conveyer stops when the `n-1th` sensor feedback is 1 (the object on the conveyer reaches it's own sensor)
- the fault lamp starts blinking and the buzzer beeps once
- the fault feedback of `n-1th` conveyer turns 1
- the cycle repeats till the starting conveyer
- once all the conveyers downstream to `nth` conveyer have fault feedback as 1
	- the conveyers upstream to `nth` conveyer go into power save condition (if power save toggle was not enabled already)
	- the system running lamp turns off
	- the fault lamp stays on
	- the buzzer beeps twice every 1 minute
	- the fault reset button illuminates

after the fault at `nth` conveyer has been cleared:
- the fault condition will still be active
- the operator needs to press the fault reset button, once they do
	- the fault reset lamp starts blinking
	- the buzzer beeps once
	- the conveyers upstream of `nth` conveyer leave power save condition (if power save toggle was not enabled already) in a cascading manner 
	- `2*L/S` seconds later, the `nth` conveyer starts moving again, it's running feedback turns 1, fault feedback turns 0
	- `2*L/S` seconds later, the conveyers downstream of `nth` conveyer go back to their previous condition (running or power save)
	- the fault reset button stops illuminating
	- the fault reset lamp turns off
	- the system running lamp turns on
##### stop condition
- this condition activates when stop push button is pressed
- the stop button illuminates immediately 
- the system run lamp starts blinking
- the conveyers stop in a cascading manner from downstream to upstream
	- the `nth` conveyer stops when the `nth` sensor feedback is 1 (the object on the conveyer reaches it's own sensor)
- once all the conveyers stop
	- the system run lamp turns off
	- the system stop lamp turns on
	- the buzzer beeps once
