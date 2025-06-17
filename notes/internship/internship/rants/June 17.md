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
