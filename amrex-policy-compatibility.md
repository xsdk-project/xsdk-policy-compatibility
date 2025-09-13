# xSDK Community Policy Compatibility for AMReX

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:**  https://github.com/AMReX-Codes/amrex

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| AMReX supports and provides a Spack package. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| "make test install" tests the installation of AMReX. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). |Full| AMReX can take a user-provided MPI communicator.|
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| AMReX is tested nightly with GNU and nvcc compilers on Linux machines, and regularly with other compilers on various architectures. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| AMReX developers can be contacted via issues on github (https://github.com/AMReX-Codes/amrex)|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| By default, AMReX installs its own signal handler for SIGSEGV, SIGFPE, etc. and saves the previously set handlers in `amrex::Initialize()`.  When `amrex::Finalize` is called, AMReX's signal handler is removed and the previous ones are restored.  Moreover, applications can use an AMReX runtime boolean parameter `amrex.signal_handling` to disable signal handling by AMReX.  This parameter can be set by a function call, or in an inputs file, or passed in command line. |
|**M7.** Come with an open source (BSD style) license. |Full| AMReX is released with the 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>amrex::Version()</tt> returns the current version of AMReX.|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full|All AMReX header file names start with `AMReX_`.  All C++ symbols are inside `namespace amrex`, and all C and Fortran symbols are prefixed with `amrex_` or `bl_`.  All preprocessor macros begin with `AMREX_` or `BL_`.  The library is named libamrex. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/AMReX-codes/amrex] |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All of AMReX's I/O can be turned off at runtime. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is the standard approach taken by AMReX.|
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full|  AMReX CMake uses the usual CMAKE_INSTALL_PREFIX variable.|
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| AMReX supports 64 bit pointers. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| We have incorporated the xSDK compatibility changes fully into the basic AMReX infrastructure, so that xSDK options get the same maintenance and support as any other feature of AMReX.  |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| AMReX provides such an option with -DCMAKE_BUILD_TYPE=Debug. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/AMReX-Codes/amrex] |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| AMReX tests and tutorials can be run under valgrind.|
|**R3.** Adopt and document consistent system for error conditions/exceptions. |No| |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. | No| None.|
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |None| None. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| None. |
|**R8.** Each xSDK package should have sufficient documentation to support use and further development.  |Partial| There are sphinx and doxygen documentations for usage as well as tutorial codes. |
