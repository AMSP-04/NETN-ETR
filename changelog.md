## Changelog NETN-ETR

### Changes in 2.0
This version is the initial version of the new NETN-ETR FOM module based on previous (now deprecated) LLBML FOM Module related to C2SIM and part of AMSP-04 Ed. A. modules. 

This version of NETN-ETR was developed by MSG-163.

The NETN ETR module is not backward compatible with the previous NETN LLBML Module and usage require updates to federates to use the new class names and structure.

#### 2020-03-20 - LO
Renamed parameters for UUID reference:
Destination -> LocationUuid, Waypoints -> Path, Path -> PathUuid

#### 2020-03-19 - LO
Moved datatypes to NETN-BASE
Two parameters for specifing Point, at a number of tasks
Two parameters for specifing Path, at a number of tasks
Altitude modelling, datatypes
Identifier -> Id, (naming conventions)

#### 2020-03-05 - LO
Moved Array ArrayOfWorldLocationStruct to NETN-SE
Moved Enum PathTypeEnum32 to NETN-SE
Moved HLAvariantRecord PathVariantStruct to NETN-SE
Moved Enum PointTypeEnum32 to NETN-SE
Moved HLAvariantRecord PointVariantStruct to NETN-SE
Changed datatype at attribute: CreateObstacle.Geometry: ArrayOfWorldLocationStruct
Changed datatype at attribute: Patrol.PatrolRoute: PathVariantStruct
Changed datatype at attribute: EstablishCheckPoint.Location: PointVariantStruct
Added new attribute to ETR_Task: CommunicationNetworkIdentifiers
Added new attribute to ETR_Report: CommunicationNetworkIdentifiers
Added new Task: Jamming
Added new Task: Observe

#### Updated the datatype PathVariantStruct used in parameter Waypoints at MoveToLocation and MoveToEntity

#### Updated datatype for Waypoints at MoveToLocation and MoveToEntity and Destination at MoveToLocation

#### New Task, SetTransmitterStatus 

#### NETN-ETR#3 Move TransactionId Datatype definition to NETN Base
* TransactionId Datatype moved to NETN Base

#### NETN-ERT#4 Add more tasks
* Added EstablishCheckPoint
* Added OperateCheckPoint
* Added RemoveCheckPoint
* Added StopAtSideOfRoad
* Added CreateObstacle
* Added CreateMinefield
* Added ClearObstacle
* Added AddPassage
* Added RemovePassage
* Added Patrol
* Added PatrolRepeating
* Removed FollowRoute
* Renamed MoveToUnit to MoveToEntity 
* Renamed FollowUnit to FollowEntity
* Renamed VehicleMount to Mount
* Renamed VehicleDismount to Dismount
* Renamed FireIndirectWM to FireAtLocationWM
* Renamed FireAtUnit to FireAtEntity
* Renamed FireDirectWM to FireAtEntityWM
* Renamed ChangeOrderedSpeed to SetOrderedSpeed
* Renamed ChangeOrderedAltitude to SetOrderedAltitude
* Added MagicMove
* Added MagicResource

#### NETN-ETR#5 Typo: SensorReport.SpottedEnities
* Changed Parameter SensorReport.SpottedEnities to SpottedEntities.

#### NETN-ETR#6 Typo: MOUNT.EntiityId
* Changed Parameter MOUNT.EntiityId to EntityId



<useHistory>v1.0.0 - First version of the module. It is development of the old NETN-LBML FOM module.</useHistory>
<useHistory>v1.0.1 - Fixed typos.</useHistory>
<useHistory>v2.0.1 - Modified version as described in "LLBML-ChangeProposal-v0.8.docx"</useHistory>
<useHistory>v2.0.2 - Modified version as described in "LLBML-ChangeProposal-v0.9.docx"</useHistory>
<useHistory>v2.0.3 - modified version as described in "LLBML-ChangeProposal-v0.10.docx"</useHistory>
<useHistory>v2.0.4 - Updated model identification descriptions."</useHistory>
<useHistory>v2.0.5 - TransactionId Datatype moved to NETN Base"</useHistory>
<useHistory>v2.0.6 - 2019-11-14 - LO - Updated semantics for EstablishCheckPoint and RemoveCheckPoint"</useHistory>
<useHistory>v2.0.7 - 2019-12-10 - LO - Updated semantics for EstablishCheckPoint and OperateCheckPoint, described implications on passing entities

### Previous structure

The NETN-ETR FOM Module is based on previous released NETN-LLBML FOM module developed by MSG-068, updated by MSG-106 and prepared for release by MSG-134.

The version of LLBML used in AMSP-04 Ed. A. NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD) is:
* NETN-LBML_v1.1.0.xml


