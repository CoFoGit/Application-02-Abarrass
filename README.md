# Application-02-Abarrass
Todo Q1: The equation is correctly presented given the information in the assignment and wiki as far as I can tell
Todo Q2: the simpler version of this equation is to substitute Vsource with 3.3 becuase that is our source's voltage so: (2000*Vmeasure)/(1-(Vmeasured/3.3))

Engineering Analysis:
1. Because the sensor task used vTaskDelayUntil, it was using a fixed time interval between activating the task and blocking it, the other two tasks, LED and print, both used only vTaskDelay which uses relative timing and can be subject
to drift due to the inconsitency with CPU time dedication during multiple tasks.

2. The scheduling behavior behind this system when runnning multiple tasks at the same time is that it will ALWAYS run a higher priority task including an interruption and then move onto lower priority tasks once the higher is blocked.
This means that if we were in the middle of blinking the LED or printing a update, the sensor would still take CPU time priority once the blocking of it ended due to a time interval.

3. Having mismanaged execution times and delays can lead to the jumbling of priorities for our CPU and occasionally, cause massive overtime and starvation of the system, if we were running a 300ms cycle on a 500ms period,
then the system would be running the CPU 3/5 times solely focused on the sensor task. This massive dedication to CPU time will starve lower priority tasks like toggling the LED according to it's delay and properly printing the update.
A system designer should either focus on properly optimizing their tasks so that the overuse of CPU time does not impact other lower priority tasks or include necessary delays for each task that allow correct information and performance.

4. We use vTaskDelayUntil for tasks that require very specified timing, why does the sensor require this hard timing? Because the effects of drift on this task can cause massive effects on the reading of the sensor and ultimately,
ruin the purpose of the program, meanwhile less important tasks, like the printing of current value uptime and LED toggling, while important, can be impacted minorly by drift without causing significant damage to the value of these
processes.

5. The task of sensing in this project has been applied to my Application 1's responsiblity of "monitoring an anomaly in containment", the way this has been incorporated is by transmuting the "anomaly" into a phenomenon that can be
observed by it's radiance of visible light. The sensor acts as a "detector" for the anomaly's presence within it's containment. The LED maintains it's role with the uptime of the system being visible by researchers and guards while
the print task gives researchers valuable information about the uptime of the system and the anomaly's undistrubed containment process.

Alexander Barrass
5346980
EEL 4775 Summer 2025
