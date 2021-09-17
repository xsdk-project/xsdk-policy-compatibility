# xSDK Community Policy Compatibility for ButterflyPACK

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compatibility status for each mandatory policy, and if possible also for recommended policies. If you are not compatible, state what is lacking and what are your plans on how to achieve compliance. For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:**  https://github.com/liuyangzhuan/ButterflyPACK

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| ButterflyPACK uses CMake and can be installed with `spack install butterflypack`. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| ButterflyPACK has over 20 Travis test example runs for code verification. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| Both the Fortran and C++ interfaces of ButterflyPACK require a user-provided communicator. CMake will automatically check the MPI 3 support. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| ButterflyPACK test suites are run on a number of different platforms.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| ButterflyPACK developers can be contacted via issues on github (https://github.com/liuyangzhuan/ButterflyPACK/issues/) or via email to liuyangzhuan@lbl.gov.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None.|
|**M7.** Come with an open source (BSD style) license. |Full| Use the 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>BPACK_GetVersionNumber(v_major,v_minor,v_bugfix)</tt> for Fortran and something similar for C++|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All module names begin with <tt>Bplus_</tt>, <tt>BPACK_</tt> or <tt>MISC_</tt>. The libraries begin with <tt>libdbutterflypack</tt> or <tt>libzbutterflypack</tt>. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/liuyangzhuan/ButterflyPACK](https://github.com/liuyangzhuan/ButterflyPACK) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full|The amount of IO can be controlled by a runtime parameter verbosity=-1,0,1,2. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None.|
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| CMAKE_INSTALL_PREFIX=directory. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| ButterflyPACK only supports 64 bit pointers. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None.  |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode.. |Full| ButterflyPACK can be installed in debug mode via CMake -DCMAKE_BUILD_TYPE=Debug |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/liuyangzhuan/ButterflyPACK](https://github.com/liuyangzhuan/ButterflyPACK) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |No|  |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |No|  |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Partial| Most allocated resources are deallocated once no longer needed. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |No| |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |No|  |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| ButterflyPACK has a README and LICENSE file. |
|**R8.** Each xSDK member package should have sufficient documentation to support use and further development. |No| The user document is under development. |

