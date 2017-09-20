# xSDK Community Policy Compatibility for MFEM>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**[Form in progress ... not yet completed.]**

**Website:**  https://www.mfem.org

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Partial| MFEM uses CMake, but currently does not support the XSDK specific CMAKE variables.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| MFEM has a significant number of unit tests and regression tests that can be used to verify proper installation. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| In all normal situations a user provided comm can be provided.  During fatal error conditions a call to MPI_Abort is made in MPI_COMM_WORLD.  If this is a problem we can update it.|
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| MFEM compilation is currently tested on GNN and Clang compilers on linux and OSX, as well as numerous LLNL clusters.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| MFEM team can be contacted by filing issues and request on our Github page. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| MFEM utilizes LGPL2.1 with a clause that specifically allows it to utilized by commercial entities without any "viral" licences clauses. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| get_version_str() and get_config_str() have recently been added to MFEM. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| The macro namespace is prefixed with MFEM_ and all code is found in the mfem namespace. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/mfem/mfem](https://github.com/mfem/mfem) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| The team is considering a solution which replaces all our output statments with a redirectable/supressible logger. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is the normal approach for MFEM. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| The mfem install procedure handles this. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Changes are being targeted to the master branch of MFEM.|
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| MFEM configure and install has full support from Spack. |

M9 details <a id="m9-details"></a>: (Explanation goes here.)

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/mfem/mfem](https://github.com/mfem/mfem) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| None. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |No| None. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |No| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Does spack do this? |

