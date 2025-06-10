what am i trying to do here

there are 3 user inputs: start button, stop button, and low power mode toggle.
there are 4 sensors: start sensor, sensor 0, sensor 1, sensor 2
there are 3 encoders in each conveyor: encoder 0, encoder 1, encoder 2
there are 3 motors in the conveyor to control: motor 0, motor 1, motor 2

the conveyors from downstream to upstream are numbered: 0 > 1 > 2

when i press start button:
- there's a 3 second delay
- conveyor 2 starts
- if encoder 2 is high, after a 2 second delay
- conveyor 1 starts
- if encoder 1 is high, after a 2 second delay
- conveyor 0 starts

when i press the stop button:
- conveyor 0 stops
- if encoder 0 is low, after a 2 second delay
- conveyor 1 stops
- if encoder 1 is low, after a 2 second delay
- conveyor 2 stops

when low power mode is not active:
- the conveyors keep running
when low power mode is active:
- the conveyors run only when there's an object detected by the preceding sensor
- the conveyors stop half a second after the same object is detected by it's own sensor
- if entering low power mode mid operation, the conveyors should keep running till an object reaches their own sensor

this completes the conveyor behavior of start condition, stop condition and power save condition