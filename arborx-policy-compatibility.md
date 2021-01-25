# xSDK Community Policy Compatibility for ArborX

**Website:** https://github.com/arborx/ArborX

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| `ArborX` is a `spack` package: https://github.com/spack/spack/blob/develop/var/spack/repos/builtin/packages/arborx/package.py| 
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| `ArborX` uses `CTest` for running comprehensive tests. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| Only user-provided communicators are used. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| `ArborX` requires C++14 and supports all upcoming backends (`CUDA`, `HIP`, `OpenMPTarget`, and `SYCL`)  |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| https://github.com/arborx/ArborX/blob/master/CONTRIBUTING.md |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| `ArborX` doesn't interfere with that. |
|**M7.** Come with an open source (BSD style) license. |Full| [BSD 3-Clause](https://github.com/arborx/ArborX/blob/master/LICENSE) |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| `ArborX::version()` and `ArborX::gitCommitHash()` |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All `ArborX` functionality is wrapped in the `ArborX` namespace, macros start with `ARBORX_`, header files have the format `ArborX_*`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/arborX/ArborX |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| `ArborX` doesn't use any IO statements. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| All dependencies have to be provided externally. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Yes, the install path is chosen via `CMAKE_INSTALL_PREFIX`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Yes, whatever the compiler uses. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| The xSDK compatibility requirements are fulfilled by the default branch. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| Via `CMake`. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| https://github.com/arborX/ArborX |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |None| |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| We use `assert()` for critical errors. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full | `ArborX` requires `Kokkos` which needs to be initialized and finalized at before using `ArborX` resp. after using `ArborX` |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Via `CMake`. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  | Full | Via `CMake`. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| https://github.com/arborx/ArborX/blob/master/README.md, https://github.com/arborx/ArborX/blob/master/LICENSE. |
|**R8.** Each xSDK member package should have sufficient documentation to support use and further development. |Full| https://github.com/arborx/ArborX/wiki |
