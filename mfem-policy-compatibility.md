# xSDK Community Policy Compatibility for MFEM

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [PETSc version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/petsc-policy-compatibility.md).

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:**  https://www.mfem.org

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| MFEM is installable via `spack install mfem`. It also has CMake and GNU make support.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| MFEM has a suite of unit tests, examples, and miniapps that are used for Github (https://github.com/mfem/mfem/actions) and internal (LLNL) testing. This suite can also be used to verify proper installation.|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| All parallel MFEM objects support a user specified MPI communicator. MPI-3 features are not used. MPI error-handling is not changed.|
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| MFEM tesing is performed on Linux, macOS, Windows, and several representative LLNL machines. All major compilers are tested.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| MFEM team can be contacted by filing issues or starting discussions on our Github page, https://github.com/mfem/mfem.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| MFEM does not modify floating-point exception and signal handling.|
|**M7.** Come with an open source (BSD style) license. |Full| MFEM uses the BSD-3-Clause license.|
|**M8.** Provide a runtime API to return the current version number of the software. |Full| MFEM provides the function `mfem::GetVersion()`.|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| The macro namespace is prefixed with `MFEM_` and all code is found in the `mfem` namespace. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/mfem/mfem](https://github.com/mfem/mfem) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All MFEM library output is sent to the MFEM defined C++ streams `mfem::out` and `mfem::err` which can be disabled or redirected to any user-defined C++ stream.|
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is the normal approach for MFEM. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| The MFEM install procedure handles this. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| MFEM uses the compiler default pointer size. Options for changing that can be passed down to the compiler.|
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All xSDK compatibility are features are part of the main (`master`) MFEM branch and all release versions.|
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| MFEM has `+debug` variant in Spack, `MFEM_DEBUG=YES` config option for GNU make, and CMake support via the standard option `CMAKE_BUILD_TYPE`. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/mfem/mfem](https://github.com/mfem/mfem) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| None. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Partial| All unrecoverable errors invoke the MFEM error handling routine `mfem::mfem_error()` which can print the source location of the error, optioinal stack trace, and abort; or,alternatively, it can raise a C++ exception. Recoverable errors are typically reported either through a return code or by setting an error flag in the associated C++ object that can be queried by the user. Some of the unrecoverable and recoverable errors are documented.|
|**R4.** Free all system resources acquired as soon as they are no longer needed. |No| MFEM uses a small number of global objects that perform dynamic memory allocation for storing small objects such as quadrature rules. The impact of these on the total memory utilizatioon should be minimal.|
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| In GNU make build system (which is also used by Spack) library dependencies are exported in a file `config.mk`. In the CMake build system, this information is exported, in the standard CMake fashon, in a file `MFEMConfig.cmake`.|
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Partial| Supported packages with required versions are documented in the `INSTALL` file in the MFEM repository/distribution. Most of this dependency information is also expressed in the MFEM Spack package.|
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Full| All required files are present, except `SUPPORT`, the required contact information is in `CONTRIBUTING.md` and on https://mfem.org.|
|**R8.** Each xSDK package should have sufficient documentation to support use and further development.  |Full| https://mfem.org |
