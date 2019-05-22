# LOW LEVEL BML FOM MODULE
## Purpose
The NETN-LBML FOM module is simulation oriented and focuses on tasks with a fine granularity:
* It helps the simulation in understanding the C-BML message and it also introduces some concepts about "Command & Control" that simulations could use between themselves (for example during the disaggregation process).
* It contains compact low level tasks and commands that can easily be interpreted and executed by CGF tools.
* It reflects the capabilities commonly found in COTS CGF tools, but it is independent of one specific COTS CGF tool and one specific agent framework or agent modelling paradigm.
* It is independent of any specific doctrine or tactics.
* It defines status reports needed for the agent decision making and for producing C-BML reports.

### Module Objects
This module contains no HLA object classes.

### Module Interactions

Figure 7-6: Interactions from the LBML FOM Module.

This module contains the following HLA interactions:
* LBMLMessage: abstract root class of low level BML interactions.
* LBMLTask: root class of low level BML tasks.
* ChangeOrderedAltitude: Change the ordered altitude. Usually sent with TaskType InterruptCurrentTask to adjust the current move task.
* ChangeOrderedSpeed: Change the ordered speed. Usually sent with TaskType InterruptCurrentTask to adjust the current move task.
* FireAtLocation: tasks a unit to fire at a location:
 * FireIndirectWM: Tasks a unit to fire at a location with the specified weapon and munition.
* FireAtUnit: tasks a unit to fire at a specified unit:
 * FireDirectWM: The weapon type and the munition type to use.
* FollowRoute: Tasks a unit to follow the specified route.
* FollowUnit: tasks a unit to follow another unit.
* Move: Tasks a unit to move in the specified direction. The unit will keep on moving until the specified end time or when ordered otherwise.
* MoveIntoFormation: tasks an aggregate unit to move into the given formation with the given heading.
* MoveToLocation: tasks a unit to move to the specified destination.
* MoveToUnit: Tasks a unit to move to another unit.
* SetRulesOfEngagement: tasks a unit to change the rules of engagement.
* TurnToHeading: Tasks a unit to turn to the specified heading:
 * TurnToOrientation: Pitch and roll parameters.
* VehicleDismount: Tasks a unit to dismount.
* VehicleMount: Tasks a unit to mount the specified vehicle.
* Wait: tasks a unit to wait until the specified end time. Wait indefinitely if no end time is specified.
* LBMLTaskManagement: Task management interactions. For now only used to cancel tasks. Can be extended to reschedule tasks:
 * CancelAllTasks: Cancel all tasks. Tasks already started have to be aborted immediately.
 * CancelSpecifiedTasks: Cancel all specified tasks. Tasks already started have to be aborted immediately.
* LBMLReport: root class of low level BML reports:
* StatusReport: root class of reports from blue units about their status:
* ActivityStatusReport: Base class for an activity report (absolute truth):
 * CurrentActivityStatusReport: Time and status of the current task.
 * NextActivityStatusReport: Time and start condition of the next activity.
* AmmunitionStatusReport: a report about the amount of ammunition the unit still has.
* DamageStatusReport: a report from a unit that has been damaged or destroyed.
* FuelStatusReport: a report about the amount of fuel the unit still has.
* PositionStatusReport: Report about the position, speed, and heading of the unit.
* TaskStatusReport: A report about the status of a task the unit was ordered to execute.
* UnderAttackStatusReport: a report that the unit is under attack.
* SpotReport: a report from a blue unit about a spotted enemy, neutral, or unknown unit:
 * ActivitySpotReport: The information here is based on perception information which is determined from situation awareness, intel or potentially instinct:
 * CurrentActivitySpotReport: Elapsed time and status of the current task.
 * NextActivitySpotReport: Time and start condition of the next activity.
 * InSensorReport: Sensor type and sensed entities identifiers.
 * InWeaponRangeReport: Weapon type and entity identifiers of entities in weapon range.
