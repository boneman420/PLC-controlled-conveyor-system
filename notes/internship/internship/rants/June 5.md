about low power mode:
- the system cannot start when in low power mode. low power mode can only be activated after the system starts and is fully running

---------

| lp mode | start 0 | start 1 | start fc | stop fc | lp fc |
| ------- | ------- | ------- | -------- | ------- | ----- |
| 0       | 0       | 0       | 0        | 1       | 0     |
| 0       | 0       | 1       | 0        | 1       | 0     |
| 0       | 1       | 0       | 0        | 1       | 0     |
| 0       | 1       | 1       | 1        | 0       | 0     |
| 1       | 0       | 0       | 0        | 1       | 0     |
| 1       | 0       | 1       | 0        | 1       | 0     |
| 1       | 1       | 0       | 0        | 1       | 0     |
| 1       | 1       | 1       | 0        | 0       | 1     |



| system start/stop memory | conveyors running | all conveyors running | system start | system stop |
| ------------------------ | ----------------- | --------------------- | ------------ | ----------- |
| 0                        | 0                 | 0                     | 0            | 1           |
| 0                        | 0                 | 1                     | x            | x           |
| 0                        | 1                 | 0                     | 0            | blink       |
| 0                        | 1                 | 1                     | 0            | blink       |
| 1                        | 0                 | 0                     | blink        | 0           |
| 1                        | 0                 | 1                     | x            | x           |
| 1                        | 1                 | 0                     | bilnk        | 0           |
| 1                        | 1                 | 1                     | 1            | 0           |

| system start/stop memory (A) | conveyors running (B) | all conveyors running (C) | system start (F) | system start blink (Q) |
| ---------------------------- | --------------------- | ------------------------- | ---------------- | ---------------------- |
| 0                            | 0                     | 0                         | 0                | 0                      |
| 0                            | 0                     | 1                         | x                | x                      |
| 0                            | 1                     | 0                         | 0                | 0                      |
| 0                            | 1                     | 1                         | 0                | 0                      |
| 1                            | 0                     | 0                         | 0                | 1                      |
| 1                            | 0                     | 1                         | x                | x                      |
| 1                            | 1                     | 0                         | 0                | 1                      |
| 1                            | 1                     | 1                         | 1                | 0                      |
F = AC
Q = AC'


| system start/stop memory (A) | conveyors running (B) | all conveyors running (C) | system stop (S) | system stop blink (T) |
| ---------------------------- | --------------------- | ------------------------- | --------------- | --------------------- |
| 0                            | 0                     | 0                         | 1               | 0                     |
| 0                            | 0                     | 1                         | x               | x                     |
| 0                            | 1                     | 0                         | 0               | 1                     |
| 0                            | 1                     | 1                         | 0               | 1                     |
| 1                            | 0                     | 0                         | 0               | 0                     |
| 1                            | 0                     | 1                         | x               | x                     |
| 1                            | 1                     | 0                         | 0               | 0                     |
| 1                            | 1                     | 1                         | 0               | 0                     |
S = A'B'
T = A'B
