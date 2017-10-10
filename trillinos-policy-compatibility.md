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
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Trilinos has over 1000 test examples and a test harness that can be built and executed through CTest. It also collects information on the failures and can display them. |
|**M3.** Employ user provided MPI communicator (no MPI_COMM_WORLD). |Full| All Trilinos class objects take a MPI communicator in the constructor, allowing the user complete control over where each object exists and performs its computations. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| To enable the full capability, Trilinos requires compilers with C++11 support; e.g. GNU 4.8.4 or later. There is an option to disable all C++11 modules. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Trilinos developers developers can be contacted either via email (trilinos-help@software.sandia.gov) or Trilinos-Users ML https://trilinos.org/mailman/listinfo/trilinos-users. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Teucho's debug option uses its specific MPI error handler. Otherwise, all the packages respect the system resources.  |
|**M7.** Come with an open source (BSD style) license. |Full| Either LGPL or BSD, depending on packages. See https://trilinos.org/download/license/ for the detail. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| Teuchos_Version() call returns the version number in string type. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/trilinos/trilinos |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full|  |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Partial| CMake is able to locate some external libraries.   |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full|  |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Packages supports both 32 and 64 bit under same API. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Rather than providing the xSDK options as add ons, we have incorporated them fully into the basic Trilinos infrastructure, so that xSDK options get the same maintenance and support as any other feature of Trilinos.  |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| Trilinos Cmake has full support from Spack. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| https://github.com/trilinos/trilinos  |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Trilinos CTest has this capacity and runs the test suite under valgrind each night. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full|  |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full|  A Valgrind build on the Dashboard is executed regularly. Parts of Trilinos get tested in Valgrind in downstream applications too. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| TriBITS takes care of this both with CMake's FIND_PACKAGE and for Makefule users. |
