# xSDK Community Policy Compatibility for SuperLU

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**Website:**  http://crd-legacy.lbl.gov/~xiaoye/SuperLU/

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| SuperLU uses CMake. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| SuperLU ahs over 800 test examples and a test harness that can execute the examples in parallel. It also collects information on the failures and can display them graphically (http://my.cdash.org/index.php?project=SuperLU_DIST). |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| Each SuperLU solver instance takes a MPI communicator, allowing the user complete control over on which processes the linear system is defined and solved in the parallel computations. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| SuperLU test suites are run on a number of different platforms.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| SuperLU developers can be contacted via issues on github (https://github.com/xiaoyeli/superlu_dist/issues/) or via email to xsli@lbl.gov.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| The routines return an error flag when encountering a failure.|
|**M7.** Come with an open source (BSD style) license. |Full| Use 2-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| <tt>SuperLU_DIST_GetVersionNumber()</tt> |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| SuperLU include files all begin with <tt>superlu_</tt>. The libraries begin with <tt>libsuperlu</tt>. Macros and symbols begin with <tt>SUPERLU</tt> or a small set of other prefixes. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| [https://github.com/xiaoyeli/superlu_dist](https://github.com/xiaoyeli/superlu_dist) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full|Currently, amount of IO is controlled by CPP -DPRNTlevel= 1,2, .... In the future, will change it to be controlled at runtime. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Yes. No other package's source code is contained within SuperLU.|
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Use the standard CMake --prefix path. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| SuperLU supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Yes.  |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| SuperLU configure and install has full support from Spack. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [https://github.com/xiaoyeli/superlu_dist](https://github.com/xiaoyeli/superlu_dist) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full|  |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full|  |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full|  |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| |

