# Task 1 — Identify Constraints

**System:** Automated Railway Level-Crossing Control System (ARLCCS)

**C1:** The barrier must not open while a train is present in the crossing.<br>
**Reason:** Opening the barrier could allow road traffic to enter the crossing while the train is passing.

**C2:** Whenever a train is approaching, the warning lights and audible alarm must be active.<br>
**Reason:** Road users must be warned early enough to stop and clear the crossing.

**C3:** The barrier may be commanded to open only after the train has completely cleared the crossing.<br>
**Reason:** If the barrier opens when only the front of the train has passed, vehicles could hit the remaining carriages.

**C4:** If a train is inside the danger zone, the barrier must be closed.<br>
**Reason:** The barrier must block road traffic before the train reaches the crossing.

**C5:** The train may be given a "proceed" signal only if the barrier is closed.<br>
**Reason:** Letting a train pass over an open crossing puts road users at risk.

**C6:** While the barrier is closed, the warning lights and alarm must stay active.<br>
**Reason:** If warnings stop while the barrier is down, drivers may think it is safe and try to cross.

**C7:** Whenever the barrier is closed, the road traffic signal must show red.<br>
**Reason:** The barrier and the signal must give the same "stop" instruction to drivers.

**C8:** If a sensor failure is detected, the system must close the barrier and alert the control center.<br>
**Reason:** A failed sensor may hide a real train, so the system must assume the dangerous case.

**C9:** If a barrier failure is detected, the system must alert the control center and keep the road signal red.<br>
**Reason:** A faulty barrier cannot be trusted to block traffic, so other safeguards and human action are needed.

**C10:** If communication is lost, the system must close the barrier and alert the control center.<br>
**Reason:** Without communication the train status cannot be verified, so the system must default to the safe state.

**C11:** If sensor readings are incorrect or conflicting, the system must keep the barrier closed and must not issue an open command.<br>
**Reason:** When information is uncertain, the safe assumption is that a train may be present.

**C12:** In an emergency, the system must activate warnings, turn the signal red, close the barrier, and alert the control center.<br>
**Reason:** An emergency needs the safest state immediately, and operators must be informed.
