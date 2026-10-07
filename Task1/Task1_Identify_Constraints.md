# Task 1 — Identify Constraints

**System:** Automated Railway Level-Crossing Control System (ARLCCS)

| Constraint ID | Constraint in Simple English | Why the Constraint Is Necessary |
|---|---|---|
| **C1** | The barrier must not open while a train is present in the crossing. | Opening the barrier could allow road traffic to enter the crossing while the train is passing. |
| **C2** | Whenever a train is approaching, the warning lights and audible alarm must be active. | Road users must be warned early enough to stop and clear the crossing. |
| **C3** | The barrier may be commanded to open only after the train has completely cleared the crossing. | If the barrier opens when only the front of the train has passed, vehicles could hit the remaining carriages. |
| **C4** | If a train is inside the danger zone, the barrier must be closed. | The barrier must block road traffic before the train reaches the crossing. |
| **C5** | The train may be given a "proceed" signal only if the barrier is closed. | Letting a train pass over an open crossing puts road users at risk. |
| **C6** | While the barrier is closed, the warning lights and alarm must stay active. | If warnings stop while the barrier is down, drivers may think it is safe and try to cross. |
| **C7** | Whenever the barrier is closed, the road traffic signal must show red. | The barrier and the signal must give the same "stop" instruction to drivers. |
| **C8** | If a sensor failure is detected, the system must close the barrier and alert the control center. | A failed sensor may hide a real train, so the system must assume the dangerous case. |
| **C9** | If a barrier failure is detected, the system must alert the control center and keep the road signal red. | A faulty barrier cannot be trusted to block traffic, so other safeguards and human action are needed. |
| **C10** | If communication is lost, the system must close the barrier and alert the control center (using a backup channel). | Without communication the train status cannot be verified, so the system must default to the safe state. |
| **C11** | If sensor readings are incorrect or conflicting, the system must keep the barrier closed and must not issue an open command. | When information is uncertain, the safe assumption is that a train may be present. |
| **C12** | In an emergency, the system must activate warnings, turn the signal red, close the barrier, and alert the control center. | An emergency needs the safest state immediately, and operators must be informed. |

## Constraint Groups

| Group | Constraints |
|---|---|
| Barrier open/close rules | C1, C3, C4 |
| Warnings and signals | C2, C6, C7 |
| When a train may pass | C5 |
| Failure and emergency handling | C8, C9, C10, C11, C12 |
