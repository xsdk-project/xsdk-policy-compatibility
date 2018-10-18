# xSDK Community Policy Compatibility for DataTransferKit

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** https://github.com/ORNL-CEES/DataTransferKit

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| DTK currently uses CMake with TriBITs.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| DTK includes a broad unit test suite for all delivered components that can be run with ctest after building if tests are enabled in the configuration (`by passing -D DataTransferKit_ENABLE_TESTS=ON` to cmake).|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 2 or MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| DTK operates on arbitrary MPI communicators. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| DTK has been tested at ALCF, OLCF, and with avariety of platforms (Linux, Mac OSX) and compilers (Clang, GNU, NVCC, IBM, etc.) |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The DTK GitHub homepage includes instructions for contacting developers, asking questions, and filing issues. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| DTK does not register any signal handlers and does not initialize or finalize MPI. DTK uses Kokkos as the on-node programming model. DTK will initialize Kokkos if it has not yet been initialized. If it initializes Kokkos it will also finalze Kokkos.|
|**M7.** Come with an open source (BSD style) license. |Full| DTK has a 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| We have an API for both the version number and Git repository hash if accessible (namely `DataTransferKit::version()` and `DataTransferKit::gitCommitHash()`). |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All DTK classes and functions are defined in the `DataTransferKit` namespace. All DTK source files and macros are prefixed with `DTK_`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Open GitHub repository: https://github.com/ORNL-CEES/DataTransferKit |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| None. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| All DTK dependicies are handled through outside installations. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| DTK installs in a user-specified prefix directory (via the standard `CMAKE_INSTALL_PREFIX`) variable. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| DTK supports 64 bit systems. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All xSDK compatibility changes are part of the main DTK repository. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| DTK has a Spack install. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| Open GitHub repository: https://github.com/ORNL-CEES/DataTransferKit |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| DTK tests run under valgrind. We also have static analysis with clang in our continuous integration system. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| DTK uses C++ exceptions for error handling in the library and error codes for error handling in the C interface. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Heap-allocated objects are managed via smart pointers. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| A CMake configuration file with this information is generated during installation. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| The DTK spack build documents dependencies in a machine readable format. |
