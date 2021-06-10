# xSDK Community Policy Compatibility for ForTrilinos

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

**Website:** \<package website\>

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| Standard CMake flags are supported.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Unit tests are included, and deployment tests are part of the regular CI.|
|**M3.** Employ user-provided MPI communicator (no `MPI_COMM_WORLD`). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| ForTrilinos uses the standard MPI module's communicators and integrates with Trilinos-defined communicators. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). | Partial | A variety of systems and compilers have been tested, but some (such as IBM XLF) have compiler bugs or standards compliance issues. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Add a github issue or contact authors. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Not applicable |
|**M7.** Come with an open source (BSD style) license. |Full| Use 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. | Full | Includes build, link, and runtime-accessible version strings. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Fortran modules with `for` + Trilinos package name. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Public github repository. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| None. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Trilinos is built externally. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Uses standard CMake GNUInstallDirs. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| None. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. | Full | Repo is housed on GitHub. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. | Partial | Can be manually executed with `ctest -D ExperimentalMemCheck` |
|**R3.** Adopt and document consistent system for error conditions/exceptions. | Full | Errors available through `fortrilinos_ierr` variable. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. | Partial | Implemented through Spack package definition (`spack graph`) |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  | Full | Documentation in text and in spack |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  | Partial | Readme and license only. |
