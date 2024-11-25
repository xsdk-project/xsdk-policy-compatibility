# xSDK Community Policy Compatibility for \<package\>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies version 1.0.0. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [hypre version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/hypre-policy-compatibility.md).

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** https://github.com/SCOREC/pcms

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| Spack repo contained here https://github.com/jacobmerson/pcms-spack.git. Instructions on how to build in pcms repo. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Supports ctest
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| None. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Can be contacted through github or the contact information in SUPPORT.md. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| Using BSD 3-Clause License. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full/Partial/None| None. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| None. |
|**M10.** Provide a publicly available repository. |Full| None. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| None. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| This can be done with the standard configuration variable in CMake. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Package supports 64 bit. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** Have a debug build option. |Full| None. |
|**M17.** Each xSDK member package should have sufficient documentation to support use and further development.  |Full/Partial/None| While documentation for users is mandatory, developer documentation is recommended, but not yet required. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** At least one validation (smoke) test that can be invoked through the Spack package. |Full/Partial/None| None. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| None. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Partial| Made all IO statements optional. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Done through cmake. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| Done through cmake. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| No CHANGELOG. |
|**R8.** Provide version comparison preprocessor macros.  |Full| None. |
