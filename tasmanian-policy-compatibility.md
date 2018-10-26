# xSDK Community Policy Compatibility for Tasmanian

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your Compatibility status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy.This information will be helpful for future xSDK member packages.

**Website:**  https://tasmanian.ornl.gov/

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| Tasmanian uses the CMake options. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Tasmanian has a comprehensive test suites covering all major functionality, code coverage is checked daily. |
|**M3.** Employ user provided MPI communicator (no MPI_COMM_WORLD). |Full| Overall, Tasmanian provides little MPI functionaily, but all of it is restricted to a user specified `MPI_COMM` |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Tasmanian CI includes both gcc and clang, all releases are tested on the aforementioned DoE machines. In addition, Mac OSX and MS Windows are fully supported as well. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The manual and the web-page list the Lead Developer e-mail. Github issues are also accepted. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Currently Tasmanian doesn't modify anything related to signal handling. |
|**M7.** Come with an open source (BSD style) license. |Full| Tasmanian is distributed under 3-Clause BSD license with an additional UT-Battelle disclaimer (redundantly confirming that the software is provided *AS IS*). |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| Tasmanian has `static int TasGrid::TasmanianSparseGrid::getVersionMajor()`, also `getVersionMinor()`, `getGitCommitHash()`, and `getCmakeCxxFlags()`. The information is also provided by the CLI tool `tasgrid -version`. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Everything in Tasmanian is encapsulated in C++ `TasGrid` and `TasDREAM` namespaces, the ANSI C and Fortran 90 interfaces use the prefix `tsg`. Similarly, files use `tsg` (Tasmanian Sparse Grids) `tdr` (Tasmanian DREAM), or just `Tasmanian` prefixes. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/ORNL/TASMANIAN is publicly available. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Tasmanian is silent, unless the user explicitly asks for output. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Tasmanian uses CMake `find_package()` modules, and external libraries such as BLAS and MAGMA can be specified directly. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Libraries and headers go in `<prefix>/lib` and `<prefix>/include`, CLI tools sit in `<prefix>/bin`, scripts and auxilary files go in `<prefix>/share/Tasmanian`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| CI and nighly builds are done in 64-bit mode, 32-bit might work but is not tested or supported. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| XSDK optins are integrated in the build system and will be supported in the foreseeable futire. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| The Spack package for Tasmanian accepts `+xsdkflags`, and is already included in the xSDK `package.py`. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| https://github.com/ORNL/TASMANIAN  |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Tasmanian is tested under `valgrind` on a daily basis. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |*Partial*| The Python interface has comprehensive error handling, C++ has a basic set of consistency checks. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Memory leaks tested daily with valgrind. Prompt release of resource is integrated in the library design. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| The spack package provides a full list of dependencies, the manual lists all tested compilers and libraries. |

