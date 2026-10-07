**Task 1**  **Identify Constraints**

**System: Automated Railway Level-Crossing Control System (ARLCCS) Role: Software Verification Team**

**The constraints below are rules the system must always satisfy. Each one restricts what the system is allowed or not allowed to do, and covers barrier control, warnings, train passage, and component failures.**

C1: The barrier must not open while a train is present in the crossing. Reason: Opening the barrier could allow road traffic to enter the crossing while the train is passing.

C2: Whenever a train is approaching, the warning lights and audible alarm must be active. Reason: Road users must be warned early enough to stop and clear the crossing before the train arrives.

C3: The barrier may be commanded to open only after the train has completely cleared the crossing. Reason: If the barrier opens when only the front of the train has passed, vehicles could hit the remaining carriages.

C4: If a train is inside the danger zone, the barrier must be closed. Reason: The barrier must block road traffic before the train reaches the crossing.

C5: The train may be given a "proceed" signal only if the barrier is closed. Reason: Allowing a train to pass over an open crossing would put road users at risk.

C6: While the barrier is closed, the warning lights and alarm must stay active. Reason: If warnings stop while the barrier is down, drivers may think it is safe and try to cross.

C7: Whenever the barrier is closed, the road traffic signal must show red. Reason: The barrier and the traffic signal must give the same "stop" instruction to drivers.

C8: If a sensor failure is detected, the system must close the barrier and alert the control center. Reason: A failed sensor may hide a real train, so the system must assume the dangerous case.

C9: If a barrier failure is detected, the system must alert the control center and keep the road signal red. Reason: A faulty barrier cannot be trusted to block traffic, so other safeguards and human action are needed.

C10: If communication is lost, the system must close the barrier and alert the control center (using a backup channel). Reason: Without communication the train status cannot be verified, so the system must default to the safe state.

