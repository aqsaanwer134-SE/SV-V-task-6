# Task 3 — Identify Constraint Violations

One violation scenario for each of the 12 formalized constraints (the task requires at least 8).

**Detection rule:** A → B is violated when A = TRUE and B = FALSE.

## Violation Scenarios

| ID | Constraint | Violation Scenario | Violating Values | What Went Wrong | How We Know It Is Violated |
|---|---|---|---|---|---|
| **V1** | F1: Train_Present → ¬Barrier_Open | A relay sticks and the barrier lifts while the train is on the crossing. | Train_Present = TRUE<br>Barrier_Open = TRUE | The barrier is open while a train occupies the crossing, so vehicles can enter the tracks. | ¬Barrier_Open = FALSE, so TRUE → FALSE = FALSE. |
| **V2** | F2: Train_Approaching → Warning_Active | The warning-light controller loses power while a train is approaching. | Train_Approaching = TRUE<br>Warning_Active = FALSE | A train is coming but road users get no warning. | Condition is TRUE and required result is FALSE, so the implication is FALSE. |
| **V3** | F3: Open_Command → (Train_Cleared ∧ ¬Train_Present) | The software sends an open command when the train's front has left but its last carriages are still on the crossing. | Open_Command = TRUE<br>Train_Cleared = FALSE<br>Train_Present = TRUE | The barrier was told to open before the whole train cleared. | Train_Cleared ∧ ¬Train_Present = FALSE ∧ FALSE = FALSE, so TRUE → FALSE = FALSE. |
| **V4** | F4: Train_In_Zone → Barrier_Closed | A fast train enters the danger zone but the barrier is still moving down because of a mechanical delay. | Train_In_Zone = TRUE<br>Barrier_Closed = FALSE | The barrier is not fully closed when the train is close. | The barrier-closed sensor reads FALSE while the train is in the zone. |
| **V5** | F5: Proceed_Signal → Barrier_Closed | The train signal turns to "proceed" because of a logic error while the barrier is still open. | Proceed_Signal = TRUE<br>Barrier_Closed = FALSE | The train may pass over an unprotected crossing. | TRUE → FALSE = FALSE. |
| **V6** | F6: Barrier_Closed → Warning_Active | A warning timer expires during a long train stop and switches off the lights while the barrier stays down. | Barrier_Closed = TRUE<br>Warning_Active = FALSE | Warnings are off while the crossing is blocked, so drivers may go around the barrier. | Barrier is closed (TRUE) but warnings are off (FALSE). |
| **V7** | F7: Barrier_Closed → Signal_Red | The road signal shows green because of a controller software fault, although the barrier is down. | Barrier_Closed = TRUE<br>Signal_Red = FALSE | The signal says go while the barrier says stop. | TRUE → FALSE = FALSE. |
| **V8** | F8: Sensor_Fault → (Barrier_Closed ∧ Alert_Control) | A track sensor stops responding and the system treats "no data" as "no train", leaving the barrier open with no alert. | Sensor_Fault = TRUE<br>Barrier_Closed = FALSE<br>Alert_Control = FALSE | The system did not switch to fail-safe behavior after the sensor failure. | Barrier_Closed ∧ Alert_Control = FALSE, so TRUE → FALSE = FALSE. |
| **V9** | F9: Barrier_Fault → (Alert_Control ∧ Signal_Red) | The barrier arm jams halfway. The fault is detected, but no alert is sent and the signal stays green. | Barrier_Fault = TRUE<br>Alert_Control = FALSE<br>Signal_Red = FALSE | A known barrier failure was not reported and traffic is not stopped by other means. | Alert_Control ∧ Signal_Red = FALSE while Barrier_Fault = TRUE. |
| **V10** | F10: Comm_Loss → (Barrier_Closed ∧ Alert_Control) | A cable fault cuts the link to the control center and the crossing keeps operating with the barrier open. | Comm_Loss = TRUE<br>Barrier_Closed = FALSE<br>Alert_Control = FALSE | The system runs unsupervised and does not enter the safe state. | Required result is FALSE while Comm_Loss is TRUE. |
| **V11** | F11: Sensor_Conflict → (Barrier_Closed ∧ ¬Open_Command) | Sensor A reports a train present and Sensor B reports the track clear. The software trusts Sensor B and sends an open command. | Sensor_Conflict = TRUE<br>Barrier_Closed = FALSE<br>Open_Command = TRUE | The conflict was resolved in the unsafe direction. | Barrier_Closed ∧ ¬Open_Command = FALSE ∧ FALSE = FALSE. |
| **V12** | F12: Emergency → (Warning_Active ∧ Signal_Red ∧ Barrier_Closed ∧ Alert_Control) | A vehicle is stuck on the tracks and an emergency is triggered. The barrier closes but warnings stay off and no alert is sent. | Emergency = TRUE<br>Barrier_Closed = TRUE<br>Signal_Red = TRUE<br>Warning_Active = FALSE<br>Alert_Control = FALSE | The emergency response was only partly carried out. | The result is a conjunction, so one FALSE part makes it FALSE: TRUE → FALSE = FALSE. |

## Expected System Response

| ID | Expected Correct Behavior |
|---|---|
| V1 | Close the barrier, activate warnings, set signal red, alert the control center. |
| V2 | Switch to backup power, close the barrier early, alert the control center. |
| V3 | Cancel the open command, keep the barrier closed until the tail-end sensor confirms clearance. |
| V4 | Treat as barrier fault, set signal red, send a train-stop alert, alert the control center. |
| V5 | Revoke the proceed signal, set the train signal to stop, alert the control center. |
| V6 | Re-enable warnings immediately, remove the timer-based shutdown. |
| V7 | Force the signal to red, log the fault, notify the control center. |
| V8 | Close the barrier, activate warnings, set signal red, alert the control center, require inspection. |
| V9 | Set the signal red, alert the control center, stop approaching trains, dispatch maintenance. |
| V10 | Enter fail-safe mode and alert the control center through a backup channel. |
| V11 | Close the barrier, treat as train present, keep it closed until the conflict is resolved manually. |
| V12 | Complete all four emergency actions: warnings on, signal red, barrier closed, control center alerted. |
