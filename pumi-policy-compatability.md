# xSDK Community Policy Compatibility for PUMI, the Parallel Unstructured Mesh Infrastructure

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

**Website:** https://github.com/SCOREC/core/wiki

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| PUMI can be installed via CMake using Spack. [M1 details](#m1-details)|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. | Full | PUMI has over 100 regression tests; a significant portion of the tests exercise parallel functionality. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| PUMI builds with GNU, XL, Intel, and Clang compilers. |
|**M5.** Provide a documented, reliable way to contact the development team.  |Full| None. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| [BSD 3-Clause "New" or "Revised" License](https://github.com/SCOREC/core/blob/master/LICENSE). |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| None. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| None. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/SCOREC/core/ |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| None. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| We have not recently tested a 32 bit build. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| PUMI is a spack package. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| None. |

M1 details <a id="m1-details"></a>:
Following the numbering in [Version 0.6.0 of the xSDK Spack Variant Guidelines](http://dx.doi.org/10.6084/m9.figshare.13096334)

<item #>. [supported=[yes|no],description]

1. yes, `int64` is provided to enable 64 mesh entity ids
2. no, the precision of data attached to the mesh is controlled at runtime via apis
3. yes, `shared` is provided to build shared libraries using pic
4. yes, supported by default through the Spack `CMakePackage`

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| None. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| There are cmake options to enable valgrind when running the ctest test suite. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |None| None. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |partial| We provide a CMake package for other users of CMake; [example](https://github.com/SCOREC/core/blob/master/doc/user_CMakeLists.cmake). |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  | Partial | We specify the required versions of Omega_h and Simmetrix SimModSuite in our CMake files.  The required ParMETIS, Zoltan, and BZip versions are not specified.  |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  | Partial | We provide README and LICENSE but not SUPPORT and CHANGELOG files. |
|**R8.** Each xSDK member package should have sufficient documentation to support use and further development.  |Partial| We provide a [developer guide](https://github.com/SCOREC/core/wiki/Developer-Guide). |
