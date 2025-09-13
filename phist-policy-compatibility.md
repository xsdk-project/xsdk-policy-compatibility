# xSDK Community Policy Compatibility for PHIST

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:** https://bitbucket.org/essex/phist

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| phist uses CMake and implements the XSDK flags. [M1 details](#m1-details)|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| There is an extensive suite of unit and integration tests. [M2 details](#m2-details)|
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| See phist_set_default_comm function i phist_tools.h |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| We have nightly builds with different compilers, LAPACK and MPI versions. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Contact E-Mail in source files and the [wiki](https://bitbucket.org/essex/phist). |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| See related functions in phist_tools.h |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| None. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://bitbucket.org/essex/phist |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Can set cmake option PHIST_OUTLEV=0 or redirect output to a C++ stream or C FILE (cf. phist_tools.h). |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Supports only 64-bit pointers. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| None. |

M1 details <a id="m1-details"></a>: PHIST provides the variants suggested by xSDK.

M2 details <a id="m2-details"></a>: There is an extensive suite of unit and integration tests, which can be run using 'make test' after building the libraries (using 'make'). A `smoke test' after installation can be performed using 'make test_install'. The extensive test suite is an essential feature of phist because it also tests the underlying kernel library for correctness, trying e.g. to detect hard-to-find errors due to lack of data alignment.


### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| Repo is publicly accessible (read-only), contributions are welcome via pull requests. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| This is possible but we recommend using the gcc address sanitizer (cmake option GCC_SANITZE=address). |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| All functions return an error code via the last argument (similar to MPI), the C++ interface optionally throws an exception in addition. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| installs phistLibraries.cmake and a pkg-config file phist.pc, and provides an API call (cf. phist_tools.h)|
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.	|Partial| Only available in CMake files and via spack. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory. | Partial |SUPPORT file is missing (information available in README.md) |
|**R8.** Each xSDK package should have sufficient documentation to support use and further development.  |Full| None. |
