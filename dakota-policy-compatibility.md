# xSDK Community Policy Compatibility for Dakota

**Website:** https://dakota.sandia.gov

**Member:** no

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. | Full | Dakota maintains its spack package spec |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. | Full | Dakota has an extensive regression test suite and unit tests |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. | Full | None |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). | Full | As part of routine testing, Dakota is built with Clang, MSVS, GNU, and Intel compilers |
|**M5.** Provide a documented, reliable way to contact the development team. | Full | Available from [our website](https://dakota.sandia.gov) |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). | Full | Library-mode Dakota does not alter these settings. |
|**M7.** Come with an open source (BSD style) license. |Full | Dakota is licensed under the LGPL. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full | None. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full | All Dakota components are in the `Dakota` namespace. |
|**M10.** Provide a publicly available repository. |Full| Available at https://github.com/snl-dakota |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. | Full | Dakota-native components can be redirected, but the output of some TPLs cannot. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. | Partial | Some TPLs are vendored. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full | None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full | None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full | None. |
|**M16.** Have a debug build option. |Full | None. |
|**M17.** Each xSDK package should have sufficient documentation to support use and further development.  |Full | User and developer documenation is available at https://snl-dakota.github.io/. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** At least one validation (smoke) test that can be invoked through the Spack package. |Full| None. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| None. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. | None| None. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. | Partial | None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| None. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Partial| None. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| None. |
|**R8.** Provide version comparison preprocessor macros.  |None| None. |
