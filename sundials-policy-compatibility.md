# xSDK Community Policy Compatibility for SUNDIALS

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:**  https://computation.llnl.gov/projects/sundials

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Partial| SUNDIALS uses CMake and supports most xSDK CMake variables. [M1 details](#m1-details)|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |No| SUNDIALS test suite is not currently released to users. [M2 details](#m2-details) |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| SUNDIALS MPI vector constructors take an MPI communicator as input. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Partial| SUNDIALS is tested with GNU compilers on Linux and and LLNL clusters. User documentation needs to be updated with compatible versions of (optional) thrid party libraries. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The SUNDIALS development team can be reached through the user mailing list via email to sundials-users@llnl.gov or the contact information at https://computation.llnl.gov/projects/sundials/team. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| SUNDIALS uses the 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |No| SUNDIALS does not currently provide an API for returning the current version number. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Partial| SUNDIALS include files are located in subdirectores (e.g. sundials/xxx.h, cvode/xxx.h, etc.) and macros are prefixed with with SUN or a solver/module specific prefix. One excpetion is TRUE and FALSE macros that will be renamed. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |No| The SUNDIALS development repository is not currently accessable. Future SUNDIALS releases will be mirrored on GitHub. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |No| SUNDIALS currently has hardwired error messages that print to stdout/stderr from all ranks. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This the normal approach for SUNDIALS. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| SUNDIALS CMake uses usal the usual CMAKE_INSTALL_PREFIX variable. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All xSDK related changes will be merged into the SUNDIALS master branch for release. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| SUNDIALS can be configured and installed with Spack. |

M1 details <a id="m1-details"></a>: SUNDIALS is compliant with all installation policies except 3b (handeling CPP and CPPFLAGS environment variables) and 12 (providing 'make test_install' functionality).

M2 details <a id="m2-details"></a>: The SUNDIALS test suite is not currently released to users as it relies on comparing test program outputs against reference files which may differ depending on the configuration/architecture. We are working on improving the portability of the SUNDIALS test suite.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |No| The SUNDIALS development repository is not publically available but future releases will be mirrored on GitHub. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |No| We plan to update the test suite to allow for automatically running tests under valgrind. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| SUNDIALS functions return positive/engative error codes to report recoverable/unrecoverable failures. User callable fucntions are provided to get the last returned flag value and name. Error codes are documented in the SUNDIALS user guides.|
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| The SUNDIALS user guides document the necessary function calls to free any allocated memory by SUNDIALS solvers. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |No| None. |
