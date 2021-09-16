# xSDK Community Policy Compatibility for *hypre*

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Web site**: http://www.llnl.gov/casc/hypre

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| *hypre* supports xSDK community GNU Autoconf. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| *hypre* provides a script (make checkpar) that runs a subset of the daily regression tests to satisfy this requirement. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Being written entirely in C, *hypre* has generally been very portable, and will continue to be due to strong customer demand. In addition, daily/weekly regression tests are performed on various architectures with different compilers.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The *hypre* team can be contacted via email: hypre-support@llnl.gov . Issues can also be reported at https://github.com/LLNL/hypre . |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| *hypre* is one of the original xSDK packages and uses the LGPL License v. 2.1. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| *hypre* provides a script that returns the version number. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| *hypre* prepends macros, library and include file names with HYPRE_ or hypre_ to avoid namespace collisions with other packages. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| *hypre* releases are mirrored on github. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All hardwired print statements have been removed. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is how *hypre* is generally used. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Every effort is made for *hypre* to be backwards compatible. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| *hypre* is fully supported by spack and the original xSDK install tool. |


### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Partial| The development repository is private, but releases, including test releases as needed, are mirrored on github. https://github.com/LLNL/hypre |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| *hypre* has completely moved to valgrind for memory regression tests. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Partial | *hypre* has a system for error conditions, Which is documented in the users guide, but has not been completely implemented throughout the whole library. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| All resources are freed as soon as they are no longer needed as long as the required functions are used to free them, as described in the users and reference manuals. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| None. |
