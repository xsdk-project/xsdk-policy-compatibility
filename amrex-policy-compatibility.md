# xSDK Community Policy Compatibility for AMReX

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**Website:**  https://github.com/AMReX-Codes/amrex

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| AMReX uses the CMake options.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| "make test install" tests the installation of AMReX. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| AMReX can take a user-provided MPI communicator.|
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| AMReX is tested nightly with GNU compilers on Linux machines, and regularly with other compilers. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| AMReX developers can be contacted via issues on github (https://github.com/AMReX-Codes/amrex)|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| |
|**M7.** Come with an open source (BSD style) license. |Full| AMReX is released with modified BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>PetscGetVersion()</tt> and <tt>PetscGetVersionNumber()</tt> |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| PETSc include files all begin with <tt>petsc</tt>. The libraries begin with <tt>libpetsc</tt>. Macros and symbols begin with <tt>PETSc</tt> or a small set of other prefixes. The symbol/macro space is larger than it should be since it has prefixes such as <tt>Vec</tt>, <tt>Mat</tt>, <tt>KSP</tt>. These have not been removed since it would require changes to all PETSc codes. Surprisingly we have not had reports of symbol conflicts, which is why we have not fixed this potential problem. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/AMReX-code/amrex] |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All of AMReX's I/O can be turned of at runtime. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is the standard approach taken by AMReX.|
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full|  AMReX CMake uses the usual CMAKE_INSTALL_PREFIX variable.|
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| AMReX support 64 bit pointers. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| We have incorporated the xSDK compatibility changes fully into the basic AMReX infrastructure, so that xSDK options get the same maintenance and support as any other feature of AMReX.  |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| AMReX can be configured and installed with Spack. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/AMReX-Codes] |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| AMReX tests and tutorials can be run under valgrind.|
|**R3.** Adopt and document consistent system for error conditions/exceptions. |No| |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| 
|**R5.** Provide a mechanism to export ordered list of library dependencies.  No| None.|

