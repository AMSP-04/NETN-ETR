## Entity Tasks
This section summarizes the Entity Task interaction classes in the ETR FOM module.

![](./etr_task.png)

The following interaction classes are defined:

* Move: Tasks an entity to move in the specified direction for the given duration.
* MoveToLocation: Tasks an entity to move to the specified location.
* MoveToEntity: Tasks an entity to move to another entity.
* MoveIntoFormation: Tasks an aggregate entity to move into the given formation with the given heading.
* FollowEntity: Tasks an entity to follow another entity.
* TurnToHeading: Tasks an entity to turn to the specified heading.
    *	TurnToOrientation: Tasks an entity to turn to a specified orientation, including pitch and roll.
* Mount: Task the entity to mount in the specified entity .
* Dismount: Task the entity to dismount from the entity where it is in.
* FireAtLocation: Tasks an entity to fire at a location.
    *	FireAtLocationWM: Tasks an entity to fire at a location with the specified weapon and munition.
* FireAtEntity: Tasks an entity to fire at another specified entity.
    *	FireAtEntityWM: Tasks an entity to fire at a specified entity with the specified weapon and munition.
* SetOrderedSpeed: Set/Change the ordered speed.
* SetOrderedAltitude: Set/Change the ordered altitude for a flying entity..
* Wait: Tasks an entity to wait a defined duration.
* SetRulesOfEngagement: Change the rules of engagment for an entity.
* EstablishCheckPoint: The task defines a location where an check point shall be established and then operated.
* OperateCheckPoint: The task activates a deactivated check point.
* StopAtSideOfRoad: Tasks an entity to stop at the side of the road.
* RemoveCheckPoint: This task removes the check point that is generated in the EstablishCheckpoint task.
* CreateObstacle: Tasks an entity to create an obstacle with the given geometry.
    *	CreateMinefield: Tasks an entity to create a minefield within the specified geometry.
* ClearObstacle: Task an entity to clear the obstacle or minefield with the given ID.
* AddPassage: Tasks an entity to lay/build a passage between the two given points.
* RemovePassage: Tasks an entity to remove the pasasage with the given ID.
* Patrol: Defines a patrol, covering the path from the current location to the start point of the patrol route, and the patrol route itself.
    *	PatrolRepeating: Task an entity to repeat a patrol task for the given duration.

The following table provides a grouping of tasks per function.

|Functional group|Interactions|
|---|---|
|Movement Tasks| Move<br/>MoveToLocation<br/>MoveToEntity<br/>MoveIntoFormation<br/>FollowEntity<br/>TurnToHeading<br/>TurnToOrientation<br/>Patrol<br/>PatrolRepeating<br/>StopAtSideOfRoad<br/>SetOrderedSpeed<br/>SetOrderedAltitude|
|Engineering Tasks|CreateObstacle<br/>CreateMinefield<br/>ClearObstacle<br/>CreatePassage<br/>RemovePassage|
|Engagement Tasks|FireAtLocation<br/>FirAtLocationWM<br/>FireAtEntity<br/>FireAtEntityWM<br/>SetRulesOfEngagement|
|Other Tasks|Mount<br/>Dismount<br/>Wait<br/>EstablishCheckPoint<br/>OperateCheckPoint<br/>RemoveCheckPoint|