# xSDK Community Policy Compatibility for Ginkgo

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** [github.com/ginkgo-project/ginkgo](https://github.com/ginkgo-project/ginkgo)

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| Ginkgo uses the CMake options. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Ginkgo contains a comprehensive set of unit tests which can be run individually, or all at once via CTest. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| Ginkgo is an on-node library, so it does not utilize MPI. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Ginkgo supports any C++11 compliant compiler. Compatibility with the newest versions of GNU and Clang compilers is automatically verified via CI. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The developers can be contacted via [github issues](https://github.com/ginkgo-project/ginkgo/issues). |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| Ginkgo uses 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |__TODO__| None. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All ginkgo functions and classes are in the `gko::` namespace. All macros have a `GKO_` prefix (__TODO__: fix some problems with this). All header files are installed in the `ginkgo/` subidrectory. All shared libraries have a `ginkgo` prefix. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [github.com/ginkgo-project/ginkgo](https://github.com/ginkgo-project/ginkgo). |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| None. __TODO__: there's 1 or 2 of those that output an error message on `stderr` before everything crashes - in cases of an unrecoverable exception. Not sure if this is a problem. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Done through CMake's `find_package`. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |__TODO__| None. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [github.com/ginkgo-project/ginkgo](https://github.com/ginkgo-project/ginkgo) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| None.  __TODO__: verify this. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Ginkgo reports errors through exceptions inherited from `std::exception`. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |__TODO__| None. |
