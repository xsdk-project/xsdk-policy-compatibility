# xSDK Community Policy Compatibility for heFFTe

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:** https://mkstoyanov.bitbucket.io/heffte/

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| heFFTe uses Spack and all CMake options are exposed. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| heFFTe provides a comprehensive correctness testing suite using ctest, and benchmarks in `heffte/build/benchmarks/` for scalability and performance comparisons.|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| heFFTe API requires user to provide the MPI communicator. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| heFFTe requires a C++11 capable compiler. We test on GNU, Clang, and vendor compilers (xl and icc). |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Developers can be contacted directly, through heffte@icl.utk.edu, and issues can be reported on Bitbucket. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| heFFTe does not modify any system defaults. |
|**M7.** Come with an open source (BSD style) license. |Full| heFFTe is distributed under 3-clause BSD (AKA modified BSD) license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| heFFTE provides version number through the `Heffte_VERSION_MAJOR`, `Heffte_VERSION_MINOR`, and `Heffte_VERSION_PATCH` macros. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| heFFTe uses name space `heffte`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Open Bitbucket repo https://bitbucket.org/icl/heffte/. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| heFFTe runs silently. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Standard CMake `find_package()` conventions are used to specify the dependencies. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| heFFTe uses CMake `-D CMAKE_INSTALL_PREFIX=<prefix>`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| 64 bit pointers are supported and tested, 32 bit pointers are not tested. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All compatibility comments relate to the master branch. |
|**M16.** Have a debug build option. |Full| The Spack package for heFFTe accepts build_type=debug. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| heFFTe has a publicly available Git repository accessible at [https://bitbucket.org/icl/heffte/](https://bitbucket.org/icl/heffte/). |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| heFFTe runs under valgrind. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Using consistent set of C++ exceptions and compile time static assets. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| heFFTe uses RAII style of memory management and minimal internal cache data-structures. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Mechanisms available through CMake and spack. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| All tested library versions are well documented. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| There is README and LICENSE. SUPPORT and CHANGELOG are provided in README. |
|**R8.** Provide sufficient documentation to support use and further development.  |Full| heFFTe has fully documented internal and external API. |

