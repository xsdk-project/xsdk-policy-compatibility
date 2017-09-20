# xSDK Community Policy Compatibility for SUNDIALS

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Partial| Use CMake. [M1 details](#m1-details)|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |None| Test suite not released. [M2 details](#m2-details) |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Partial| Need to doucment compatible versions of thrid party libraries. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| None. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| Use BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |None| Need to add runtime API. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| None. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |None| Will mirror future releases on GitHub. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |None| Need to remove hardwired error messages to stdout/stderr from all ranks. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| None. |

M1 details <a id="m1-details"></a>: Compliant with all policies except 3b (handeling CPP and CPPFLAGS environment variables) and 12 (providing make test_install functionality).

M2 details <a id="m2-details"></a>: The SUNDIALS test suite is not currently released to users as it relies on comparing outputs against reference files which may differ depending on the configuration/architecture. We are working on improving the portability of the test suite.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |None| Will mirror releases on GitHub. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |None.| Will update test suite to allow for automatically running tests under valgrind. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |None| None. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| None. |
