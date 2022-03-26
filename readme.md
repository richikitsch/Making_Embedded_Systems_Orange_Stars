### Pointless high availability system that sends data back & forth

No pourpuse system to learn about some ways of communication between MCUs and play a little with high availabilty.
The system would consist in three subsystems:
- "raw data input":  a sensor sends data to an MCU, this tags each value with a time stamp and sends it via bluetooth to a
- a redundant "data process", consisting in two peers MCUs, one active, the other shadowing the state of the active one. The active peer will transmit input data and internal state to the inactive via a CAN bus. The data received via bluetooth will be transformed using some secret exchanged with the third and last susbsystem, "data storage & display" along with seq. number, to check for seq. and data integrity. Case the active node become non available, the inactive would became active and resume the session with the third subsystem and open a new bluetooth conn. with the "data aquiring". 
The active node will open a session with the "data storage & display" where seq. number will be exchanged with the "data process" module ala handshake. The data will be transmitted via IFR.
- "data storage & display" will receive data via IFR, check for seq & data integrity and store it in a FLASH mem. and display in an LCD.

### Topology

![block-diagram](https://github.com/richikitsch/Making_Embedded_Systems_Orange_Stars/blob/master/exercise-1/topoly.svg?raw=true)

### Block Diagram "Data Input"

![block-diagram](https://github.com/richikitsch/Making_Embedded_Systems_Orange_Stars/blob/master/exercise-1/collector-block.svg?raw=true)

### Hierarchy "Data Input"

![block-diagram](https://github.com/richikitsch/Making_Embedded_Systems_Orange_Stars/blob/master/exercise-1/hierarchy-collector.svg?raw=true)
