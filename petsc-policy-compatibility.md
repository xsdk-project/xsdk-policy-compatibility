# xSDK Community Policy Compatibility for PETSc>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**[Form in progress ... not yet completed.]**

**Website:**  https://www.mcs.anl.gov/petsc 

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| PETSc uses the GNU Autoconf options. The implementation is done with python code|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| PETSc has over 1000 test examples and a test harness that can execute the examples in parallel. It also collects information on the failures and can display them graphically ftp://ftp.mcs.anl.gov/pub/petsc/nightlylogs/archive/2017/09/19/master.html |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| All PETSc objects take a MPI communicator in the constructor allowing the user complete control over where each object exists and performs its computations. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| The PETSc test suite tests all major compilers and several minor ones including solaris and PGI.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| PETSc developers can be contacted via the https://bitbucket.org/petsc/petsc/issues?status=new&status=open issues on Bitbucket or via email petsc-maint@mcs.anl.gov |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Though PETSc, by default does attach its own set of signal handlers, the appropriate function call PetscOptionsSetValue("-no_signal_handler","true") before calling PetscInitialize() leaves the current signal handler in place.  |
|**M7.** Come with an open source (BSD style) license. |Full| Use 2-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| PetscGetVersion() and PetscGetVersionNumber() |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| PETSc include files all begin with petsc. The libraries begin with libpetsc. Macros and symbols begin with PETSc or a small set of other prefixes. The symbol/macro space is larger than it should be.  |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://bitbucket.org/petsc/petsc](https://bitbucket.org/petsc/petsc) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All of PETSc's I/O can be turned of at runtime, in addition one can provide a file pointer to have ASCII output saved to a file instead of stdout/stderr or provide a function pointer that gives the user complete control on how ASCII output is handled. For example, in GUI systems such as Microsoft Windows one can have the text appear in popup windows if desired. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| For each external package xxx, PETSc supports both the configure option --with-xxx-dir to use an externally built version and --download-xxx to install the package. PETSc does not contain any other package's source code within  |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| PETSc's configure uses the usual --prefix option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| PETSc configure and install has full support from Spack. |

M9 details <a id="m9-details"></a>: (Explanation goes here.)

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://bitbucket.org/petsc/petsc](https://bitbucket.org/petsc/petsc) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| PETSc has this capacity and runs the test suite under valgrind each night. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| PETSc uses error codes from Fortran and C/C++ to report all error conditions. After each function is called the error code is checked to determine if the code can continue or must be terminated. It uses this checking to produce stack traces by default when errors are detected. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| PETSc tests use valgrind, MPICH options, and internal code to report any resources or memory that are not freed before the problem completes. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| make getlinklibs lists all dependencies for an install, PETSc also provides pkgconfig and module files.

