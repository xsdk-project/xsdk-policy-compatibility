# xSDK Community Policy Compatibility for \<package\>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [PETSc version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/petsc-policy-compatibility.md).

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** \<package website\>

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| Uses Spack with CMake for xSDK. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| `make check` does sanity checks of major routines, all precisions; `test/run_tests.py` does comprehensive testing. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Supports major compilers (GNU, Clang, Intel, IBM, etc.) and vendor LAPACK libraries (OpenBLAS, MKL, ESSL, etc.) |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Via Bitbucket ([https://bitbucket.org/icl/lapackpp/issues?status=new&status=open](https://bitbucket.org/icl/lapackpp/issues?status=new&status=open)) or SLATE forum ([https://groups.google.com/a/icl.utk.edu/forum/#!forum/slate-user](https://groups.google.com/a/icl.utk.edu/forum/#!forum/slate-user)), both listed in README. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| Uses 3-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| `lapack::lapackpp_version()` and `lapack::lapackpp_id()`. Also `LAPACKPP_VERSION` compile time macro. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Uses `lapack` C++ namespace. Macros have `lapack_`, `LAPACK_`, or `LAPACKPP_` prefix. Headers are `lapack.hh` and in `lapack/` folder. A couple LAPACK functions logically fit in BLAS (e.g., csymv), so are in `blas` namespace (with ssymv, chemv). |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://bitbucket.org/icl/lapackpp](https://bitbucket.org/icl/lapackpp) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Does not print. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Links with any standard LAPACK library. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Supports standard CMake prefix. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Supports 64-bit pointers. 32-bit is untested, but likely works. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All xSDK changes are integrated into source. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| Via Spack build_type variant and CMAKE_BUILD_TYPE. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://bitbucket.org/icl/lapackpp](https://bitbucket.org/icl/lapackpp) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |None| Not tested. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Throws C++ exceptions by default (can be disabled). |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Workspaces are freed in function that allocated them. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Exports dependencies via CMake. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| Via Spack. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| Has README.md, LICENSE, CHANGELOG.md. |
