**Task 2  Formalize Constraints**

**All 12 constraints from Task 1 are converted into logical expressions (the task requires at least 8).**

**Notation: ∧ AND | ∨ OR | ¬ NOT | → implies (if-then)**

**Boolean Variables**
Variable	Meaning
Train_Approaching	A train is detected approaching the crossing
Train_In_Zone	A train is inside the danger zone near the crossing
Train_Present	A train is currently on the crossing
Train_Cleared	The train has completely cleared the crossing
Barrier_Open	The barrier is open
Barrier_Closed	The barrier is fully closed
Open_Command	The controller commands the barrier to open
Proceed_Signal	The train is given permission to pass
Warning_Active	Warning lights and alarm are on
Signal_Red	The road traffic signal is red
Sensor_Fault	A sensor failure is detected
Barrier_Fault	A barrier failure is detected
Comm_Loss	Communication loss is detected
Sensor_Conflict	Sensor readings are incorrect or conflicting
Emergency	An emergency condition exists
Alert_Control	The control center has been alerted
