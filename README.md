# NETN ETR	
NATO Education and Training Network (NETN) Entity Tasking and Reports (ETR) Module. 
        
This module is a specification of how to represent simulation tasks requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. An HLA OMT based Federation Object Model (FOM) is used to specify types of data and how it is encoded on the network. The NETN ETR FOM module is available as a XML file for use in HLA based federations.
        ## PurposeThe NETN ETR module provides a common standard interface for sending tasks to simulated entities represented in a federated distributed simulation. ETR contains common low level tasks that can easily be interpreted and executed by simulators that model the behavior of entities. It also defines a set of reports to provide status information, including the status of the tasks being executed by simulated entities.## Scope
The NETN ETR FOM module is simulation oriented and focuses on tasks with a fine granularity:
* It enables the transformation of command and control messages into tasks that can be executed by a simulator.
* It defines status reports that can be used for producing command and control reports needed for decision making.
* It supports the modelling of simulated command and control interactions between federates in a distributed simulation, for example during a MRM disaggregation process.
* It contains a comprehensive set of tasks and reports that can easily be interpreted and executed by simulators.
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) tools, but it is independent of a specific COTS CGF tool, agent framework, or agent modelling paradigm.
* It is independent of any specific doctrine or tactics.
An entity in ETR can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. If a task or report relates to only a physical entity or to only an aggregate entity, then this is specified in the definition of the task. In the definition of each task it is not specified how an entity (physical or aggregate) will / should perform the task.
	
### MoveTasks an entity to move in the specified direction for the given duration.
### MoveToLocationTasks an entity to move to the specified location.
### MoveToEntityTasks an entity to move to another entity.
### MoveIntoFormationTasks an aggregate entity to move into the given formation with the given heading.
### FollowEntityTasks an entity to follow another entity.
### TurnToHeadingTasks an entity to turn to the specified heading.
### TurnToOrientationTasks an entity to turn to a specified orientation, including pitch and roll.
### MountTask the entity to mount in the specified entity. The taskee entiity should be within a certain distance tolerance of the entiity to mount into. this tolerance must be specified in the federation agreements. Mount includes: embark (vessel), board (plane), and so on.
### DismountTask the entity to dismount from the entity where it is in.
### FireAtLocationTasks an entity to fire at a location.
### FireAtLocationWMTasks an entity to fire at a location with the specified weapon and munition.
### FireAtEntityTasks an entity to fire at another specified entity.
### FireAtEntityWMTasks an entity to fire at a specified entity with the specified weapon and munition.
### SetOrderedSpeedSet/Change the ordered speed. Usually sent in ConcurrentMode to adjust the current move task.
### SetOrderedAltitudeSet/Change the ordered altitude for a flying entity. Usually sent in ConurrentMode to adjust the current move task.
### WaitTasks an entity to wait a defined duration.
### SetRulesOfEngagementChange the rules of engagment for an entity.
### EstablishCheckPointThe task defines a location where a checkpoint shall be established and then operated. 
 
If the Taskee entity is not at the specified location, it has to move to that location with a seperate move task. 
The taskee entiity should be within a certain distance tolerance (specified in the federation agreements) of the location where the checkpoint should be established to make the task possible. 
 
A checkpoint instance (NETN-SE FOM) shall be created and registerd when the entity reaches the location for the checkpoint. The attribute CheckPoint.Deactivated (from RPR_v2) shall show the status of the checkpoint. 
 
The modelling federate decides when the checkpoint shall be activated, it may be direct at the creation or when the attribute PercentComplete has reached a threshold level. 
 
The modelling federate may register a NETN_CulturalFeature instance to model the checkpoint. 
Set the attribute CheckPoint.ReferencedObjectIdentifier to the NETN_CulturalFeature instance. 
The attribute NETN_CulturalFeature.Status shall be ActiveStatusEnum8.Active when the checkpoint is operated. 
 
The duraction defines when the checkpoint is deactivated unless another entity from the modelling federate Operates the checkpoint. 
 
The federation agreements shall specify how the ownership of the dynamic attribute at the checkpoint shall be managed when the checkpoint is deactivated. One of the following cases shall be managed in the federation: 
 
1. Dynamic attributes of the checkpoint are released with the HLA Ownership Management services unconditionalAttributeOwnershipDivestiture at deactivation. 
 
2. Only one federate may establish and operate a specific checkpoint. 
 
3. Use NETN TMR Pattern, the federate modelling the entity that shall operate the checkpoint requests the ownership from the current owner of the dynamic attributes.
### OperateCheckPointThe task activates a deactivated check point. 
 
If the Taskee entity is not at the checkpoint location, it has to move to that location with a seperate move task. 
The taskee entiity should be within a certain distance tolerance (specified in the federation agreements) of the location of the checkpoint to make the task possible. 
 
The attribute CheckPoint.Deactivated (from RPR_v2) shall show the status at the checkpoint. 
 
If a NETN_CulturalFeature is accociated with the checkpoint the status shall be displayed for the NETN_CulturalFeature instance. 
 
See semantics for the interaction EstablishCheckPoint how ownership of the dynamics attribute at the checkpoint instance shall be managed.
### StopAtSideOfRoadTasks an entity to stop at the side of the road. This task is only relevant for an entity that is moving along a road to a destination. The executing move task is canceled and a new move is defined to a position at the side of the road (the simulator has to calculate this location).
### RemoveCheckPointThis task removes the checkpoint that is generated in the EstablishCheckpoint task. 
 
If the Taskee entity is not at the specified location, it has to move to that location with a seperate move task. 
The taskee entiity should be within a certain distance tolerance (specified in the federation agreements) of the location of the checkpoint to make the task possible. 
 
A checkpoint instance (NETN-SE FOM) shall be removed from the Federation Execution when the entity reaches the location for the checkpoint. 
 
If a NETN_CulturalFeature instance is assigned to the checkpoint is shall be deleted.
### CreateObstacleTasks an entity to create an obstacle with the given geometry. 
The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the geometry of the obstacle to make the task possible. 
The corresponding Environment Object instance  in the RPR-FOM should be created.
### CreateMinefieldTasks an entity to create a minefield within the specified geometry. The taskee should publish the minefield as a RPR-FOM object when finished. This interaction should not be confused with the MinefieldObjectTransaction interaction of the RPR-FOM, which asks a federate directly to “magic create” a minefield. Warning: The RPR-FOM contains several ways of representing a minefield, and the taskee may decide which representation to use. It is recommended to agree on this in advance, through the use of a Federation Agreement. 
Allowed values for attributes of the parent (CreateObstacle): 
- ObstacleType = (5.1.0.5.10.*.* or 5.1.0.5.11.*.* or 5.1.0.5.12.*.*) 
- GeometryType = Area
### ClearObstacleTask an entity to clear the obstacle or minefield with the given ID. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the geometry of the obstacle to make the task possible.
### AddPassageTasks an entity to lay/build a passage between the two given points. The passage can for example be a passage through an obstacle or a bridge over a river. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the passage to make the task possible. 
The corresponding Environment Object instance in the RPR-FOM should be created.
### RemovePassageTasks an entity to remove the pasasage with the given ID. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the passage to make the task possible.
### PatrolDefines a patrol, covering the path from the current location to the  start point of the patrol route, and the patrol route itself. The patrol route will be followed from start to end. The entity behaviour at the end point depends on the patrol type.
### PatrolRepeatingTask an entity to repeat a patrol task for the given duration. For this task the patrol type other is not allowed. 
 
When the duration time has elapsed then the last cycle of the patrol will be completed before the task ends. 
 
If the time of a cycle takes longer then the interval time then the cylce starts directly (without delay). If the time of a cylce takes less then the interval time then the entiy waits in the first point for the remaining time before the next cycle is started.
### StatusReportStatus report from an entity about its own (perceived) state. This report is generated with a certain frequency specified in the federation agreements.
### PositionStatusReportReport about the position, speed, and heading of the entity.
### DamageStatusReportDamage status report of an entity. The possible damage staets are possible: NoDamage, SlightDamage, ModerateDamage, SignificantDamage, Destroyed.
### ResourceStatusReportReport about the remaning amount of a resource.
### UnderAttackStatusReportReport that the entity is under attack.
### SpotReportSpot reports are reports used by all entities to transmit intelligence or information about a spotted enemy, neutral, or unknown entity.
### SensorReportThe entities that have been observed by a specific sensor. The attributes can be: Detected, Recognized or Identified.
### InWeaponRangeReportThe entities that are in range of a specific weapon.
### CancelSpecifiedTasksCancel all specified tasks. Tasks already started are also cancelled.
### CancelAllTasksCancel all tasks. Tasks already started are also cancelled.
### TaskStatusReportA report about the status of a task given to an entity. The status of the task defined by the TaskId can be: Accepted, Refused, Cancelled, Executing, Completed or Error.
### MagicMovePlace the entity to the specified location with a given heading. All given task of the entity are cancelled.
### MagicResourceChanges the resource amount of the entity.
### QueryCapabilitiesSupportedQuery which ETR tasks and ETR reports that the entity supports. The taskee shall respond with a CapabilitiesSupported message.
### CapabilitiesSupportedProvide the set of ETR tasks and ETR reports that the entity supports. This interaction is in response to a QueryCapabilitiesSupported, using the same Taskee and Tasker.

[objectclasses]: ./objectclasses.png
