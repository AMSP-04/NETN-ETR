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
	## Overview
The interaction classes are organized in a root class and four base classes: ETR_Task, ETR_Report, ETR_TaskManagement, and ETR_SimCon. 

* ETR_Root: root interaction class for the Entitiy Tasking and Reporting (ETR) interaction classes.
* ETR_Task: A base interaction class for more specialized task interaction classes.
* ETR_Report: A base interaction class for more specialized report interaction classes.
* ETR_TaskManagement: A base interaction class for more specialized task management interaction classes.
* ETR_SimCon: A base interaction class for more specialized Simulation Control (SimCon) interaction classes

<img src="./images/objectclasses.png" width="50%"/>
      
	
	
### Entity Tasks

This section summarizes the Entity Task interaction classes in the ETR FOM module.

<img src="./images/etr_task.png" width="75%"/>

|Task|Description|
|---|---|
|Move|Tasks an entity to move in the specified direction for the given duration.|
|MoveToLocation|Tasks an entity to move to the specified location.|
|MoveToEntity|Tasks an entity to move to another entity.|
|MoveIntoFormation|Tasks an aggregate entity to move into the given formation with the given heading.|
|FollowEntity|Tasks an entity to follow another entity.|
|TurnToHeading|Tasks an entity to turn to the specified heading.|
|Mount|Task the entity to mount in the specified entity. The taskee entiity should be within a certain distance tolerance of the entiity to mount into. this tolerance must be specified in the federation agreements. Mount includes: embark (vessel), board (plane), and so on.|
|Dismount|Task the entity to dismount from the entity where it is in.|
|FireAtLocation|Tasks an entity to fire at a location.|
|FireAtEntity|Tasks an entity to fire at another specified entity.|
|SetOrderedSpeed|Set/Change the ordered speed. Usually sent in ConcurrentMode to adjust the current move task.|
|SetOrderedAltitude|Set/Change the ordered altitude for a flying entity. Usually sent in ConurrentMode to adjust the current move task.|
|Wait|Tasks an entity to wait a defined duration.|
|SetRulesOfEngagement|Change the rules of engagment for an entity.|
|EstablishCheckPoint|The task defines a location where a checkpoint shall be established and then operated. |
|OperateCheckPoint|The task activates a deactivated check point. |
|StopAtSideOfRoad|Tasks an entity to stop at the side of the road. This task is only relevant for an entity that is moving along a road to a destination. The executing move task is canceled and a new move is defined to a position at the side of the road (the simulator has to calculate this location).|
|RemoveCheckPoint|This task removes the checkpoint that is generated in the EstablishCheckpoint task. |
|CreateObstacle|Tasks an entity to create an obstacle with the given geometry. |
|ClearObstacle|Task an entity to clear the obstacle or minefield with the given ID. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the geometry of the obstacle to make the task possible.|
|AddPassage|Tasks an entity to lay/build a passage between the two given points. The passage can for example be a passage through an obstacle or a bridge over a river. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the passage to make the task possible. |
|RemovePassage|Tasks an entity to remove the pasasage with the given ID. The taskee entiity should be within a certain distance tolerance (specified in the federation aggrement) of one of the points of the passage to make the task possible.|
|Patrol|Defines a patrol, covering the path from the current location to the  start point of the patrol route, and the patrol route itself. The patrol route will be followed from start to end. The entity behaviour at the end point depends on the patrol type.|

	
### Entity Reports
This section summarizes the Entity Report interaction classes in the ETR FOM module, shown in the figure below.
 
<img src="./images/etr_report.png" width="75%"/>

|Report|Description|
|---|---|
|StatusReport|Status report from an entity about its own (perceived) state. This report is generated with a certain frequency specified in the federation agreements.|
|SpotReport|Spot reports are reports used by all entities to transmit intelligence or information about a spotted enemy, neutral, or unknown entity.|
|InWeaponRangeReport|The entities that are in range of a specific weapon.|


### Task Management
This section summarizes the Task Management interaction classes in the ETR FOM module, shown in the figure below.
 
<img src="./images/etr_taskmanagement.png" width="75%"/>


|Task Management|Description|
|---|---|
|CancelSpecifiedTasks|Cancel all specified tasks. Tasks already started are also cancelled.|
|CancelAllTasks|Cancel all tasks. Tasks already started are also cancelled.|
|TaskStatusReport|A report about the status of a task given to an entity. The status of the task defined by the TaskId can be: Accepted, Refused, Cancelled, Executing, Completed or Error.|


### Simulation Control
This section summarizes the Simulaltion Control interaction classes in the ETR FOM module, shown in the figure below.

<img src="./images/etr_simcon.png" width="75%"/>

|Simulation Control|Description|
|---|---|
|MagicMove|Place the entity to the specified location with a given heading. All given task of the entity are cancelled.|
|MagicResource|Changes the resource amount of the entity.|
|QueryCapabilitiesSupported|Query which ETR tasks and ETR reports that the entity supports. The taskee shall respond with a CapabilitiesSupported message.|
|CapabilitiesSupported|Provide the set of ETR tasks and ETR reports that the entity supports. This interaction is in response to a QueryCapabilitiesSupported, using the same Taskee and Tasker.|
