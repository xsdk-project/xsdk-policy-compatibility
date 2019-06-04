# xSDK Community Policy Compatibility for Ginkgo

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** [ginkgo-project.github.io](https://ginkgo-project.github.io/)

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| Ginkgo uses CMake.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Ginkgo contains a comprehensive set of unit tests which can be run individually, or all at once via CTest.|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 2 or MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full|Ginkgo is an on-node library, so it does not utilize MPI. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Ginkgo supports any C++11 compliant compiler. Compatibility with the newest versions of GNU and Clang compilers is automatically verified via CI. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The developers can be contacted via [github issues](https://github.com/ginkgo-project/ginkgo/issues) or through the ginkgo.library@gmail.com address. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full|  Ginkgo uses 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| Ginkgo provides the `gko::version_info` class which can be used to query version details. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All ginkgo functions and classes are in the `gko::` namespace. All macros have a `GKO_` prefix. All header files are installed in the `ginkgo/` subidrectory. All shared libraries have a `ginkgo` prefix.|
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| github.com/ginkgo-project/ginkgo](https://github.com/ginkgo-project/ginkgo). |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Everything is handled through exceptions or the user controlled `gko::Log` class. A few direct IO statements are used in case of important failure and can be disabled at compile time. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Done through CMake's `find_package`. By default, Ginkgo uses its own version of the subpackages but this behavior can be overridden by using the CMake option `-DGINKGO_USE_EXTERNAL_<PACKAGE\>=ON` or with `-DTPL_ENABLE_<PACKAGE\>=ON`. See [M1 details](#m1-details) for more information. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| We use the standard `CMAKE_INSTALL_PREFIX` option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Ginkgo aims to be fully xSDK compatible with its first 1.0.0 release. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| Ginkgo has a spack package available. |


M1 details <a id="m1-details"></a>: Ginkgo supports all relevant CMake flags.
Particularly, the `TPL_ENABLE_<PACKAGE\>`, `TPL_<PACKAGE\>_LIBRARIES` and
`TPL_<PACKAGE\>_INCLUDE_DIRS` flags are supported.
When building ginkgo benchmarks, tests, examples or documentation Ginkgo relies
on some external tools (such as gtest and gflags). Instead of automatically
installing these tools, the user can use a local version either by using
Ginkgo's CMake flags or the TPL specific flags. These packages are required only
when building Ginkgo, but not during the installation step which only installs
Ginkgo's core libraries.


M2 details <a id="m2-details"></a>: There is an extensive unit test suite
available at build time completed with a smoke test which can be ran by calling
`make test_install`.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [github.com/ginkgo-project/ginkgo](https://github.com/ginkgo-project/ginkgo) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Ginkgo uses CTest which has this feature. A suppressions list is also provided for convenience. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Ginkgo reports errors through exceptions inherited from `std::exception`. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| This information is available through a pkg-config file and the CMake exported targets. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |None|None. | 
