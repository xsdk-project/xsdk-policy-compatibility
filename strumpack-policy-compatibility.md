# xSDK Community Policy Compatibility for STRUMPACK

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [PETSc version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/petsc-policy-compatibility.md).

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** http://portal.nersc.gov/project/sparse/strumpack/

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| STRUMPACK uses CMake. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| See below. [M2 details](#m2-details)|
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| We mostly test on GNU and Intel compilers on Linux, Mac and NERSC. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Developers can be contacted directly, issues can be reported on GitHub. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| Use 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| None. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Everything is included in the (C++) strumpack namespace. Headers are organized in subfolders. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Open GitHub repo: https://github.com/pghysels/STRUMPACK |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Some warning messages are printed to sterr. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| No libraries are bundled with STRUMPACK. External dependencies are METIS, BLAS, LAPACK, ScaLAPACK/BLACS (required), and optional: ParMETIS, (PT)Scotch, PAPI. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| CMAKE_INSTALL_PREFIX=directory. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| A spack package is available (spack develop branch). |


M2 details <a id="m2-details"></a>: STRUMPACK builds 4 test programs, (seq, par) x (dense, sparse). About 200 tests are run to verify correctness.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| https://github.com/pghysels/STRUMPACK. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Partial| Not tested on the actual test suite. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |None| Code will simply abort in certain failure cases, return error code in other cases. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Partial| Running STRUMPACK CMake generates an example Makefile. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |None| None. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Full| None. |
