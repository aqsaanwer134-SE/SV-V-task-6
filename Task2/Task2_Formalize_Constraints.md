**Task 2  Formalize Constraints**

**All 12 constraints from Task 1 are converted into logical expressions (the task requires at least 8).**
Symbol	Meaning
∧	      AND
∨	      OR
¬     	NOT
→     	Implies (if-then)

Boolean Variables
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
Formal Expressions
ID	From	Formal Expression	Meaning
F1	C1	Train_Present → ¬Barrier_Open	If a train is present, the barrier is not open.
F2	C2	Train_Approaching → Warning_Active	If a train is approaching, warnings are active.
F3	C3	Open_Command → (Train_Cleared ∧ ¬Train_Present)	An open command is allowed only if the train has cleared and none is present.
F4	C4	Train_In_Zone → Barrier_Closed	If a train is in the danger zone, the barrier is closed.
F5	C5	Proceed_Signal → Barrier_Closed	The train may proceed only if the barrier is closed.
F6	C6	Barrier_Closed → Warning_Active	If the barrier is closed, warnings stay active.
F7	C7	Barrier_Closed → Signal_Red	If the barrier is closed, the road signal is red.
F8	C8	Sensor_Fault → (Barrier_Closed ∧ Alert_Control)	A sensor fault closes the barrier and alerts the control center.
F9	C9	Barrier_Fault → (Alert_Control ∧ Signal_Red)	A barrier fault alerts the control center and keeps the signal red.
F10	C10	Comm_Loss → (Barrier_Closed ∧ Alert_Control)	Communication loss closes the barrier and alerts the control center.
F11	C11	Sensor_Conflict → (Barrier_Closed ∧ ¬Open_Command)	Conflicting readings keep the barrier closed and block open commands.
F12	C12	Emergency → (Warning_Active ∧ Signal_Red ∧ Barrier_Closed ∧ Alert_Control)	An emergency activates warnings, red signal, closed barrier and an alert.
Truth Table for A → B
A	B	A → B	Result
TRUE	TRUE	TRUE	Holds
TRUE	FALSE	FALSE	Violation
FALSE	TRUE	TRUE	Holds
FALSE	FALSE	TRUE	Holds
Safe State
Name	Expression
SAFE_STATE	Barrier_Closed ∧ Signal_Red ∧ Warning_Active ∧ Alert_Control

A safety monitor evaluates F1–F12 in every control cycle. If any expression becomes FALSE, a violation is reported and the system must move to SAFE_STATE.
