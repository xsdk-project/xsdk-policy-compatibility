# xSDK Community Policy Compatibility for SUNDIALS

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compatibility status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:**  https://computing.llnl.gov/projects/sundials

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| SUNDIALS can be installed with `spack install sundials`. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| The SUNDIALS utilizes CTest to run a set of regression tests using the 'make test' command after building. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| SUNDIALS MPI vector constructors take an MPI communicator as input. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| SUNDIALS is tested with GNU compilers on Linux and and LLNL clusters. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The SUNDIALS development team can be reached through the user mailing list via email to sundials-users@llnl.gov or the contact information at https://computation.llnl.gov/projects/sundials/team. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| SUNDIALS uses the 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| The functions SUNDIALSGetVersion and SUNDIALSGetVersionNumber provide SUNDIALS version information. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| SUNDIALS include files are located in subdirectores (e.g. sundials/xxx.h, cvode/xxx.h, etc.) and macros are prefixed with with SUN or a solver/module specific prefix. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| SUNDIALS releases are mirrored on GitHub at https://github.com/LLNL/sundials. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All hardwired print statements to stdout have been removed. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This the normal approach for SUNDIALS. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| SUNDIALS CMake uses the usual CMAKE_INSTALL_PREFIX variable. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All xSDK related changes will be merged into the SUNDIALS master branch for release. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| SUNDIALS can be installed in debug mode via spack with the `build_type=Debug` variant. |

**M1 details**: 

All SUNDIALS features are configurable through spack variants, including CUDA and HIP/ROCm support. For example, for CUDA-enabled SUNDIALS one can do `spack install sundials+cuda`, or for HIP/ROCm, `spack install sundials+rocm`.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| https://github.com/LLNL/sundials |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |No| We plan to update the test suite to allow for automatically running tests under valgrind. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| SUNDIALS functions return positive/negative error codes to report recoverable/unrecoverable failures. User callable functions are provided to get the last returned flag value and name. Error codes are documented in the SUNDIALS user guides.|
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| The SUNDIALS user guides document the necessary function calls to free any allocated memory by SUNDIALS solvers. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| SUNDIALS exports a CMake config file which details library dependencies. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Partial| The SUNDIALS user guides document versions of dependencies it works with. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| SUNDIALS has a README.md, CHANGELOG.md and LICENSE file. |
|**R8.** Each xSDK member package should have sufficient documentation to support use and further development. |Full| SUNDIALS has extensive user documentation with examples. Developer documentation is internal only.|
