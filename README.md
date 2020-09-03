# NETN ETR

NATO Education and Training Network (NETN) Entity Tasking and Reports (ETR) Module. 

## Introduction

This module is a specification of how to represent simulation task requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. An HLA OMT based Federation Object Model (FOM) is used to specify types of data and how it is encoded on the network. The NETN-ETR FOM module is available as an XML file for use in HLA based federations.
        

### Purpose
The NETN-ETR FOM module provides a common standard interface for sending tasks to simulated entities represented in a federated distributed simulation. ETR contains common low-level tasks that can easily be interpreted and executed by simulators that model the behaviour of entities. It also defines a set of reports to provide status information, including the status of the tasks being executed by simulated entities.

### Scope
The NETN-ETR FOM module is simulation oriented and focuses on tasks with a fine granularity:
* It enables the transformation of command and control messages into tasks that can be executed by a simulator.
* It defines status reports that can be used for producing command and control reports needed for decision making.
* It supports the modelling of simulated command and control interactions between federates in a distributed simulation, for example during an MRM disaggregation process.
* It contains a comprehensive set of tasks and reports that can easily be interpreted and executed by simulators.
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) tools, but it is independent of a specific COTS CGF tool, agent framework, or agent modelling paradigm.
* It is independent of any specific doctrine or tactics.

An entity in ETR can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. If a task or report relates to only a physical entity or to only an aggregate entity, then this is specified in the definition of the task. In the definition of each task, it is not specified how an entity (physical or aggregate) will / should perform the task.	

## Licence

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes the [NETN-ETR.xml](NETN-ETR.xml) FOM Module and [documentation](NETN-ETR.md).

Above licence gives you the right to use and redistribute the NETN FOM Module (XML file and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN module by reference and including necessary scaffolding classes. You are NOT allowed to modify this FOM Module or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extensions

All updates and versioning of this work is coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of this FOM Module please contact your national NMSG representative.

Version numbering of this FOM Module and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when a new release is made in the Master branch.
* Updates in the Develop branch will not change the version number.
* In the FOM Module `useHistory` information includes only information on official releases.
* Update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.1.0 |NETN-LBML included in NETN FOM v2.0|
|v2.0|Release of renamed module based on NETN LLBML FOM Module with updated structure and additional capabilities. Included in NETN FOM v3.0|

[Changelog](changelog.md)

## Documentation

[Full Documentation](NETN-ETR.md)