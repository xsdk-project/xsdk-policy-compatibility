# xSDK Community Policy Compatibility for SLEPc

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compatibility status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:**  http://slepc.upv.es

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| SLEPc inherits all PETSc configuration (compilers, BLAS, etc.), and in addition it provides its own python script for additional configuration including prefix installation and configuration with third-party packages.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| SLEPc has more than 150 test examples. The test suite is run every night for different configurations, see [buildbot](http://slepc.upv.es/buildbot/grid). The code coverage is more than 85%, see [coverage report](http://slepc.upv.es/buildbot/coverage/).  |
|**M3.** Employ user provided MPI communicator (no MPI_COMM_WORLD). |Full| All SLEPc objects take an MPI communicator in the constructor, allowing the user complete control over where each object exists and performs its computations. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| The SLEPc nightly builds test GNU, Clang, and Intel compilers, including C89 compatibility. Portability is mostly guaranteed by strict adherence to PETSc conventions.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| SLEPc developers can be contacted via [issues on Bitbucket](https://bitbucket.org/slepc/slepc/issues) or via email to slepc-maint@upv.es.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Inherits PETSc behavior regarding signal handlers. |
|**M7.** Come with an open source (BSD style) license. |Full| Use 2-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>SlepcGetVersion()</tt> and <tt>SlepcGetVersionNumber()</tt> |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| SLEPc include files all begin with <tt>slepc</tt>. The libraries begin with <tt>libslepc</tt>. Macros and symbols begin with <tt>SLEPC</tt> or a small set of other prefixes. The symbol/macro space is larger than it should be since it has prefixes such as <tt>EPS</tt>, <tt>PEP</tt>, <tt>ST</tt>. These are not namespaced, following a similar philosophy as in PETSc. We have not had reports of symbol conflicts with other libraries. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://bitbucket.org/slepc/slepc](https://bitbucket.org/slepc/slepc) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Same behavior as PETSc, with output turned off by default. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| For most external packages xxx, SLEPc supports both the configure option <tt>--with-xxx-dir</tt> to use an externally built version and <tt>--download-xxx</tt> to install the package. SLEPc does not contain any other package's source code within. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| SLEPc's configure uses the usual <tt>--prefix</tt> option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Any functionality required by xSDK will be incorporated as necessary in the base source code. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| SLEPc configure and install has full support from Spack. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://bitbucket.org/slepc/slepc](https://bitbucket.org/slepc/slepc) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| SLEPc has this capacity and runs the test suite under valgrind each night. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Similar to PETSc, SLEPc uses error codes from Fortran and C/C++ to report all error conditions. After each function is called the error code is checked to determine whether the code can continue or must be terminated. It uses this checking to produce stack traces by default when errors are detected. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Similar to PETSc, SLEPc tests use valgrind, and internal code to report any resources or memory that are not freed before the program completes. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| The command <tt>make getlinklibs_slepc</tt> lists all dependencies for an install; SLEPc also provides pkgconfig and module files.

