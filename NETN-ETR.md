# NETN-ETR

Copyright (C) 2019 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

## Introduction

This module is a specification of how to represent simulation tasks requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. An HLA OMT based Federation Object Model (FOM) is used to specify types of data and how it is encoded on the network. The NETN ETR FOM module is available as an XML file for use in HLA based federations.
        

### Purpose
The NETN ETR module provides a common standard interface for sending tasks to simulated entities represented in a federated distributed simulation. ETR contains common low-level tasks that can easily be interpreted and executed by simulators that model the behaviour of entities. It also defines a set of reports to provide status information, including the status of the tasks being executed by simulated entities.

### Scope
The NETN ETR FOM module is simulation oriented and focuses on tasks with a fine granularity:
* It enables the transformation of command and control messages into tasks that can be executed by a simulator.
* It defines status reports that can be used for producing command and control reports needed for decision making.
* It supports the modelling of simulated command and control interactions between federates in a distributed simulation, for example during an MRM disaggregation process.
* It contains a comprehensive set of tasks and reports that can easily be interpreted and executed by simulators.
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) tools, but it is independent of a specific COTS CGF tool, agent framework, or agent modelling paradigm.
* It is independent of any specific doctrine or tactics.

An entity in ETR can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. If a task or report relates to only a physical entity or to only an aggregate entity, then this is specified in the definition of the task. In the definition of each task, it is not specified how an entity (physical or aggregate) will / should perform the task.
	

## Overview
The interaction classes are organized in a root class and four base classes: `ETR_Task`, `ETR_Report`, `ETR_TaskManagement`, and `ETR_SimCon`. 

* `ETR_Root`: root interaction class for the Entitiy Tasking and Reporting (ETR) interaction classes.
* `ETR_Task`: A base interaction class for more specialized task interaction classes.
* `ETR_Report`: A base interaction class for more specialized report interaction classes.
* `ETR_TaskManagement`: A base interaction class for more specialized task management interaction classes.
* `ETR_SimCon`: A base interaction class for more specialized Simulation Control (SimCon) interaction classes

<img src="./images/etr_baseclasses.png" width="75%"/>
      
	
	
### Entity Tasks

This section summarizes the Entity Task interaction classes in the ETR FOM module.

<img src="./images/etr_task.png" width="90%"/>

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
|SetTransmitterStatus|Task entity to switch on/off all of its transmitters.|
|Observe|Observation to cover area with sensors. |
|Jamming|Jamming of a communication network in a specified area.|


### Entity Reports
This section summarizes the Entity Report interaction classes in the ETR FOM module, shown in the figure below.

<img src="./images/etr_report.png" width="85%"/>

|Report|Description|
|---|---|
|StatusReport|Status report from an entity about its own (perceived) state. This report is generated with a certain frequency specified in the federation agreements.|
|SpotReport|Spot reports are reports used by all entities to transmit intelligence or information about a spotted enemy, neutral, or unknown entity.|
|InWeaponRangeReport|The entities that are in range of a specific weapon.|


### Task Management
This section summarizes the Task Management interaction classes in the ETR FOM module, shown in the figure below.

<img src="./images/etr_taskmanagement.png" width="85%"/>


|Task Management|Description|
|---|---|
|CancelSpecifiedTasks|Cancel all specified tasks. Tasks already started are also cancelled.|
|CancelAllTasks|Cancel all tasks. Tasks already started are also cancelled.|
|TaskStatusReport|A report about the status of a task given to an entity. The status of the task defined by the TaskId can be: Accepted, Refused, Cancelled, Executing, Completed or Error.|


### Simulation Control
This section summarizes the Simulation Control interaction classes in the ETR FOM module, shown in the figure below.

<img src="./images/etr_simcon.png" width="85%"/>

|Simulation Control|Description|
|---|---|
|MagicMove|Place the entity to the specified location with a given heading. All given task of the entity are cancelled.|
|MagicResource|Changes the resource amount of the entity.|
|QueryCapabilitiesSupported|Query which ETR tasks and ETR reports that the entity supports. The taskee shall respond with a CapabilitiesSupported message.|
|CapabilitiesSupported|Provide the set of ETR tasks and ETR reports that the entity supports. This interaction is in response to a QueryCapabilitiesSupported, using the same Taskee and Tasker.|

## ETR Task Handling

The following sections define how tasks shall be handled.

### ETR Task Modes

The ETR FOM module defines two modes for a task: non-concurrent mode and concurrent mode.

In the non-concurrent mode, the task is placed on the task list for the entity, which serves as a waiting list. Once the task is at the head of the task list, and the currently executing task completes, it is removed from the task list and started. Using this task mode, tasks are executed one after the other.

In the concurrent mode, the task is executed concurrently with other tasks. With this task mode, there is no task list involved.

The mode value is provided for each task. So, at any point in time, an entity has zero or more concurrent mode tasks executing and at most one non-concurrent mode task executing, with zero or more non-concurrent mode tasks waiting on the task list.

### ETR Task States

The following states are defined for a task:

* TaskStatus.Received: the task is received;
* TaskStatus.Waiting: the task is waiting for execution;
* TaskStatus.Executing: the task is executing.

The task state diagram is shown below.

<img src="./images/etr_taskstates.png" width="85%"/>

#### Received State
A task in the Received state shall be handled in the following way:

1. Determine if the task is supported. The determination is made by the federate application in accordance with section 8.4.3.
2. If the task is not supported then
    * A `TaskStatusReport` (refused) shall be returned to the Tasker.
    * The task is removed.
3. Else
    * For a non-concurrent mode task:
        * The task shall be placed in the entity task list in accordance with section 8.3.3.
    * A `TaskStatusReport` (accepted) shall be returned to the Tasker.
    * The task shall transition to the Waiting state.

#### Waiting State
A task in the Waiting state shall be handled in the following way:
1.	Determine if the task can start using the following conditions:
    * For a non-concurrent mode task:
        * The task’s taskee is not executioning a task, and
        * The task is at head of the task list, and
        * The task has no `StartWhen` time (i.e. the StartWhen is undefined), or the task has a StartWhen time and this time is less than or equal to the current time.
    * For a concurrent mode task:
        * The task has no `StartWhen` time (i.e. the StartWhen is undefined), or the task has a StartWhen time and this time is less than or equal to the current time, and
        * The task does not conflict with other executing tasks (see section 8.3.4).
2.	If the task can start then
    * For a non-concurrent mode task:
        * The task shall be removed from the task list.
        * A `TaskStatusReport` (executing) shall be returned to the Tasker.
        * The task shall transition to the Executing state.
3.	Else
    * The task shall remain in the Waiting state, even if the current time has passed the time specified in the `StartWhen` parameter of the task.

#### Executing State
A task in the Executing state shall be handled in the following way:

1.	Determine if the task has completed. The conditions are scenario specific and the determination is up to the federate application.
2.	If the task has completed then
    * A `TaskStatusReport` (completed) shall be returned to the Tasker.
    * The task is removed.
3.	Else
    * The task shall remain in the Executing state.

#### TaskStatus State
A task in the TaskStatus state shall be handled as specified in the substates, and also in the following way:

1.	If the task is cancelled by either a `CancelAllTasks` or `CancelSpecifiedTask` then
    * A `TaskStatusReport` (cancelled) shall be returned to the Tasker.
    * The task is removed.
2.	If the task cannot be handled due to an internal federate application error then
    * A `TaskStatusReport` (error) shall be returned to the Tasker and a description of the error shall be included in the message.
    * The task is removed.

### Task List Order
Each entity has a task list for non-concurrent mode tasks. The task at the head of the list is the first task to be started once the currently executing task completes. The ordering of tasks in the task list shall be according to the following figure.

<img src="./images/etr_tasklist.png" width="85%"/>

The tasklist shall be divided in two parts: a left part that contains tasks where the StartWhen is specified, and a right part that contains tasks where no StartWhen is specified. The division point shall mark the head of the left part and the tail of the right part. A part is empty if there are no tasks for that part.

A task shall be placed in the task list as follows:

1.	If the StartWhen time of the task is specified then the task shall be placed in the left part of the task list, using the StartWhen time to order the tasks in this part (with decreasing StartWhen value towards the head of the list).
2.	If the StartWhen time of the task is not specified then the task shall be placed at the tail of the right part of the task list.

###	Concurrent Tasks
The following table defines which tasks for the same entity can execute concurrently. The table shows which tasks can transition from the Waiting state to the Execution state given another task that is already in Execution state for the same entity. 

|Number|Task in Execution state|Tasks allowed to go to Execution state|
|---|---|---|
|1|Move|6, 7, 10, 11, 12, 13, 14, 15, 17, 22|
|2|MoveToLocation|10, 11, 12, 13, 14, 15, 17, 22|
|3|MoveToEntity|10, 11, 12, 13, 14, 15, 17, 22|
|4|MoveIntoFormation|10, 11, 12, 13, 14, 15, 17|
|5|FollowEntity|10, 11, 12, 13, 14, 15, 17|
|6|TurnToHeading|1|
|7|TurnToOrientation|1|
|8|MountVehicle| |
|9|DismountVehickle| |
|10|FireAtLocation|1, 2, 3, 4, 5, 18, 19|
|11|FireAtLocationWM|1, 2, 3, 4, 5, 18, 19|
|12|FireAtEntity|1, 2, 3, 4, 5, 18, 19|
|13|FireAtEntityWM|1, 2, 3, 4, 5, 18, 19|
|14|SetOrderedSpeed|1, 2, 3, 4, 5, 18, 19|
|15|SetOrderedAltitude|1, 2, 3, 4, 5, 18, 19|
|16|Wait| |
|17|SetRulesOfEngagement|1, 2, 3, 4, 5, 18, 19|
|18|Patrol|10, 11, 12, 13, 14, 15, 17|
|19|PatrolRepeating|10, 11, 12, 13, 14, 15, 17|
|20|EstablishCheckPoint| |
|21|OperateCheckPoint| |
|22|StopAtSideOfRoad|1, 2, 3|
|23|RemoveCheckPoint| |
|24|CreateObstacle| |
|25|CreateMinefield| |
|26|ClearObstacle| |
|27|AddPassage| |
|28|RemovePassage| |

## ETR SimCon Handling
A Simulation Control message for an entity shall be executed immediately, regardless of the presence of any (concurrent or non-concurrent) executing task.

### Magic Move
A `MagicMove` for an entity shall implicitly cancel all tasks for the entity. A TaskStatusReport (cancelled) shall be issued for each task in accordance with the task state diagram.

### Magic Resources
A `MagicResource` shall update the entity resources. Waiting or executing tasks of the entity are affected in the sense that these tasks have more or less resources available after the MagicResource.

### Entity Task and Reporting Capabilities
It shall be possible to query an entity for the ETR tasks and ETR reports that it supports. The set of tasks and reports that an entity supports is implementation-specific, and shall be used in the Received state of a task to determine if the task is supported.

With the interaction class `QueryCapabilitiesSupported` an entity can be queried for the supported ETR tasks and ETR reports. The result is provided via the interaction class `CapabilitiesSupported`.

## Implementation Requirements
This section lists the requirements for applications that implement Entity Tasking and Reporting. The requirements are provided from receiver point of view (entity taskee, the federate application modelling the entity) and sender point of view (entity tasker, the federate application sending a task or receiving a report for an entity).

The receiver:
1.	SHALL support all ETR TaskManagement and ETR SimCon classes.
2.	MAY support a subset of the ETR Task and ETR Report classes.
3.	SHALL provide all interaction class parameters when sending an ETR interaction.

The sender:
1.	SHALL provide all interaction class parameters when sending an ETR interaction.

In addition, for the receiver, the following SHALL be documented in the federation agreements:
1.	Distance tolerances of supported tasks (for the tasks `Mount`, `EstablishCheckPoint`, `OperateCheckPoint`, `RemoveCheckPoint`, `CreateObstacle`, `ClearObstacle`, `CreateMinefield`, `AddPassage`, and `RemovePassage`).
2.	Entities that provide ETR Reports.
3.	Time frequencies and conditions for the supported ETR Reports.
4.	Modelling agreements related to checkpoints (if supported, see `EstablishCheckPoint`, `OperateCheckPoint`, and `RemoveCheckPoint`).
5.	Modeling agreements related to minefields (if supported, see `CreateMineField`).
