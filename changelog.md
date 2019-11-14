## Changelog NETN-ETR

### Changes in 2.0
This version is the initial version of the new NETN-ETR FOM module based on previous (now deprecated) LLBML FOM Module related to C2SIM and part of AMSP-04 Ed. A. modules. 

This version of NETN-ETR was developed by MSG-163.

The NETN ETR module is not backward compatible with the previous NETN LLBML Module and usage require updates to federates to use the new class names and structure.

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

### Previous structure

The NETN-ETR FOM Module is based on previous released NETN-LLBML FOM module developed by MSG-068, updated by MSG-106 and prepared for release by MSG-134.

The version of LLBML used in AMSP-04 Ed. A. NATO Education and Training Network Federation Architecture and FOM Design (NETN FAFD) is:
* NETN-LBML_v1.1.0.xml


