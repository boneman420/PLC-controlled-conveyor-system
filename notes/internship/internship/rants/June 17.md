| low power mode | system start/stop memory | conveyors running | all conveyors running | system start | system stop |
| -------------- | ------------------------ | ----------------- | --------------------- | ------------ | ----------- |
| 0              | 0                        | 0                 | 0                     | 0            | 1           |
| 0              | 0                        | 0                 | 1                     | x            | x           |
| 0              | 0                        | 1                 | 0                     | 0            | blink       |
| 0              | 0                        | 1                 | 1                     | 0            | blink       |
| 0              | 1                        | 0                 | 0                     | blink        | 0           |
| 0              | 1                        | 0                 | 1                     | x            | x           |
| 0              | 1                        | 1                 | 0                     | bilnk        | 0           |
| 0              | 1                        | 1                 | 1                     | 1            | 0           |
| 1              | 0                        | 0                 | 0                     | 0            | 1           |
| 1              | 0                        | 0                 | 1                     | x            | x           |
| 1              | 0                        | 1                 | 0                     | 0            | blink       |
| 1              | 0                        | 1                 | 1                     | 0            | blink       |
| 1              | 1                        | 0                 | 0                     | blink        | 0           |
| 1              | 1                        | 0                 | 1                     | x            | x           |
| 1              | 1                        | 1                 | 0                     | blink        | 0           |
| 1              | 1                        | 1                 | 1                     | 1            | 1           |
Input Definitions:
- `A` = system start/stop memory
- `B` = conveyors running
- `C` = all conveyors running
- `D` = low power mode ← new input
We'll rederive expressions for:
- `F` = system start
- `Q` = system start blink
- `S` = system stop
- `T` = system stop blink

| D   | A   | B   | C   | `F` | `Q` | `S` | `T` |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   | 0   | 1   | 0   |
| 0   | 0   | 0   | 1   | x   | x   | x   | x   |
| 0   | 0   | 1   | 0   | 0   | 0   | 0   | 1   |
| 0   | 0   | 1   | 1   | 0   | 0   | 0   | 1   |
| 0   | 1   | 0   | 0   | 0   | 1   | 0   | 0   |
| 0   | 1   | 0   | 1   | x   | x   | x   | x   |
| 0   | 1   | 1   | 0   | 0   | 1   | 0   | 0   |
| 0   | 1   | 1   | 1   | 1   | 0   | 0   | 0   |
| 1   | 0   | 0   | 0   | 0   | 0   | 1   | 0   |
| 1   | 0   | 0   | 1   | x   | x   | x   | x   |
| 1   | 0   | 1   | 0   | 0   | 0   | 0   | 1   |
| 1   | 0   | 1   | 1   | 0   | 0   | 0   | 1   |
| 1   | 1   | 0   | 0   | 0   | 1   | 0   | 0   |
| 1   | 1   | 0   | 1   | x   | x   | x   | x   |
| 1   | 1   | 1   | 0   | 0   | 1   | 0   | 0   |
| 1   | 1   | 1   | 1   | 1   | 0   | 1   | 0   |
F = ABC
Q = AC'
S = DAC+A'B'
T= BA'

(verified)

---
lamp control logic:
- inputs: system start stop memory,
		all conveyors running,
		conveyors running,
		low power mode,
		fault flag
- outputs: start, fault, stop

conveyor control logic:
- in start condition:
	- inputs: (clearance delay off: belt delay, succeeding conveyor running feedback)
	- outputs: delay
- in low power condition:
	- inputs: (sensor control: belt delay, preceding sensor)
	- outputs: %% delay %%
- in stop condition:
	- inputs: (sensor control: belt delay, preceding sensor), (clearance delay off: belt delay, preceding conveyor running feedback), low power mode
	- outputs: delay
- in fault condition:
	- inputs: (sensor control: belt delay, preceding sensor), succeeding conveyor fault feedback out
	- outputs: delay

so each conveyor has a sensor control block and a timer block before enable

