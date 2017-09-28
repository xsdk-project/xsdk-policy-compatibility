# xSDK Community Policy Compatibility for Trilinos

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your Compatibility status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**Website:**  https://trilinos.github.io

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| Trillinos uses the CMake options. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Trilinos has over 1000 test examples and a test harness that can be built and executed through CTest. It also collects information on the failures and can display them, e.g., ??? |
|**M3.** Employ user provided MPI communicator (no MPI_COMM_WORLD). |Full| All Trilinos class objects take a MPI communicator in the constructor, allowing the user complete control over where each object exists and performs its computations. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| The PETSc test suite tests all major compilers and several minor ones, including solaris and PGI.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| PETSc developers can be contacted via issues on Bitbucket (https://bitbucket.org/petsc/petsc/issues?status=new&status=open) or via email to petsc-maint@mcs.anl.gov.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Although by default PETSc attaches its own set of signal handlers, the appropriate function call <tt>PetscOptionsSetValue("-no_signal_handler","true")</tt> before calling <ttt>PetscInitialize()</tt> leaves the current signal handler in place.  |
|**M7.** Come with an open source (BSD style) license. |Full| Use 2-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>PetscGetVersion()</tt> and <tt>PetscGetVersionNumber()</tt> |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| PETSc include files all begin with <tt>petsc</tt>. The libraries begin with <tt>libpetsc</tt>. Macros and symbols begin with <tt>PETSc</tt> or a small set of other prefixes. The symbol/macro space is larger than it should be since it has prefixes such as <tt>Vec</tt>, <tt>Mat</tt>, <tt>KSP</tt>. These have not been removed since it would require changes to all PETSc codes. Surprisingly we have not had reports of symbol conflicts, which is why we have not fixed this potential problem. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://bitbucket.org/petsc/petsc](https://bitbucket.org/petsc/petsc) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All of PETSc's I/O can be turned of at runtime. In addition, one can provide a file pointer to have ASCII output saved to a file instead of stdout/stderr or provide a function pointer that gives the user complete control on how ASCII output is handled. For example, in GUI systems such as Microsoft Windows, one can have the text appear in popup windows if desired. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| For each external package xxx, PETSc supports both the configure option <tt>--with-xxx-dir</tt> to use an externally built version and <tt>--download-xxx</tt> to install the package. PETSc does not contain any other package's source code within  |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| PETSc's configure uses the usual <tt>--prefix</tt> option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Rather than providing the xSDK options as add ons, we have incorporated them fully into the basic PETSc infrastructure, so that xSDK options get the same maintaince and support as any other feature of PETSc.  |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| PETSc configure and install has full support from Spack. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://bitbucket.org/petsc/petsc](https://bitbucket.org/petsc/petsc) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| PETSc has this capacity and runs the test suite under valgrind each night. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| PETSc uses error codes from Fortran and C/C++ to report all error conditions. After each function is called the error code is checked to determine whether the code can continue or must be terminated. It uses this checking to produce stack traces by default when errors are detected. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| PETSc tests use valgrind, MPICH options, and internal code to report any resources or memory that are not freed before the program completes. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| The command <tt>make getlinklibs</tt> lists all dependencies for an install; PETSc also provides pkgconfig and module files.
