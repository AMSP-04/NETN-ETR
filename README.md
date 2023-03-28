# NETN-ETR


|Version| Date| Dependencies|
|---|---|---|
|3.0 |2023-03-28|NETN-BASE, RPR-SE|

> [Full Documentation](NETN-ETR.md)

The NETN-ETR FOM module provides a common standard interface for sending tasks to simulated entities represented in a federated distributed simulation. NETN-ETR contains common low-level tasks that can easily be interpreted and executed by simulators that model the behaviour of entities. It also defines a set of reports to provide status information, including the status of the tasks being executed by simulated entities.

The NATO Education and Training Network (NETN) Entity Tasking and Reports (ETR) Module is a specification of how to represent simulation task requests provided to participants in a federated distributed simulation and simulator reports sent during the execution of tasks. 
        
The specification is based on IEEE 1516 High Level Arhitecture (HLA) Object Model Template (OMT) and is primarily intended to support interoperability in a federated simulation (federation) based on HLA. An HLA-based Federation Object Model (FOM) is used to specify types of data and how it is encoded on the network. The NETN-ETR FOM module is available as an XML file for use in HLA-based federations.
        

 The NETN-ETR FOM module is simulation oriented and focuses on tasks with fine granularity: 
    
* It enables the transformation of command and control messages into tasks that can be executed by a simulator. 
* It defines status reports that can be used for producing command and control reports needed for decision-making. 
* It supports the modelling of simulated command and control interactions between federates in a distributed simulation, for example during an MRM disaggregation process. 
* It contains a comprehensive set of tasks and reports that can easily be interpreted and executed by simulators. 
* It reflects the capabilities commonly found in COTS Computer Generated Forces (CGF) tools, but it is independent of a specific COTS CGF tool, agent framework, or agent modelling paradigm. 
* It is independent of any specific doctrine or tactics. 

An entity in ETR can be either a physical entity (e.g. platform or lifeform) or an aggregate entity. If a task or report relates to only a physical entity or to only an aggregate entity, then this is specified in the definition of the task. In the definition of each task, it is not specified how an entity (physical or aggregate) will / should perform the task. 	

## License

Copyright (C) 2020 NATO/OTAN. This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md).

The work includes the NETN-ETR.xml FOM Module and documentation.

The licence gives you the right to use and redistribute the NETN FOM Module (XML file and Documentation) in its entirety without modification. You are also allowed to develop new FOM Modules (in separate XML files and separate documentation) that build on or extend the NETN module by referencing and including necessary scaffolding classes. You are NOT allowed to modify this FOM Module or its documentation without prior permission from the NATO Modelling and Simulation Group.

## Versions, updates and extensions

All updates and versioning of this work are coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of this FOM Module please contact your national NMSG representative.

Version numbering of this FOM Module and associated documentation is based on the following principles:

* A new official version number is in effect only when a new release is made in the Master branch.
* An update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or covers entirely new concepts.
* An update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|
|---|
|v1.1 - NETN-LBML. Developed by MSG-106 and MSG-134 for NETN-FOM v2.0.|
|v2.0 - Renamed and updated by MSG-163 for NETN-FOM v3.0|
|3.0 - Updated by MSG-191 for NATO-FOM v4.0|

> [Changelog](changelog.md)

