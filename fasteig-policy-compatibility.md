# xSDK Community Policy Compatibility for fasteig

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies version 1.0.0. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:** https://github.com/BerkeleyLab/fasteig

**Member:** no

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| fastEig supports and provides a Spack package installer.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| "make test install" tests the functionality of the various eigensolvers provided by fastEig.|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |None| The current implementation support single CPU and GPU. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| fastEig has been tested with the common production compilers (GNU, clang, icc for CPU platforms, and NVCC for NVIDIA platforms). |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| fastEig developers can be contacted from the github page. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| fastEig handles the most exceptions and if enabled the information is exposed to the users. |
|**M7.** Come with an open source (BSD style) license. |Full| fastEig is released with the 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| fastEig provides fasteig::version() to return the current version of the code. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All classes, algorithms and definitions are contained in the fasteig namespace. |
|**M10.** Provide a publicly available repository. |Full| https://github.com/BerkeleyLab/fasteig. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All fastEig I/O can be turned off at runtime. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| The installation allows user to specify the location of the dependencies. In addition, if dependencies are not specified the build process tries to download and install the necessary libraries. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| fastEig CMake uses the usual CMAKE_INSTALL_PREFIX variable.. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| fastEig support 64 bit pointers.. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| We have incorporated the xSDK compatibility changes fully into the basic fastEig infrastructure, so that xSDK options get the same maintenance and support as any other feature of fastEig. |
|**M16.** Have a debug build option. |Full| fastEig provides such an option with -DCMAKE_BUILD_TYPE=Debug. |
|**M17.** Each xSDK package should have sufficient documentation to support use and further development.  |Partial| fastEig provides documentation for the installation and use. We are also documenting the classes and installation mechanisms. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** At least one validation (smoke) test that can be invoked through the Spack package. |Full| fastEig provides testing of the developed algorithms, which can be enabled or disabled through the Spack and CMAKE build systems. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| The tests can be ran under valgrind if targeting CPU only. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |None|  |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |None| |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Full| This is provided in the main repository. |
|**R8.** Provide version comparison preprocessor macros.  |Partial| We are currently working on a doxygen documentation for usage of the library. |
