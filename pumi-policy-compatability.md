# xSDK Community Policy Compatibility for PUMI, the Parallel Unstructured Mesh Infrastructure

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

**Website:** https://github.com/SCOREC/core/wiki

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. | Full | PUMI uses CMake. [M1 details](#m1-details)|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. | Full | PUMI has over 100 regression tests; a significant portion of the tests exercise parallel functionality. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). | Full | None. [(patch)](https://github.com/cwsmith/core/commit/3896c203d2cfd489917be5329cd25e6460303b20) |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| PUMI builds with GNU, XL and Clang compilers on ALCF Mira, Intel and GNU on ALCF Theta, and Intel and GNU on NERSC Cori. |
|**M5.** Provide a documented, reliable way to contact the development team.  |Full| None. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| [BSD 3-Clause "New" or "Revised" License](https://github.com/SCOREC/core/blob/master/LICENSE). |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| None. [(patch)](https://github.com/cwsmith/core/commit/1e64d7d761ec195f04c071a11e419cd4a361aaf1)|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| None. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/SCOREC/core/ |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. | Full | None. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| None. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| We have not recently tested a 32 bit build. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| None. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| PUMI is a spack package. |

M1 details <a id="m1-details"></a>:
Following the numbering in [draft 0.3.0 of the xSDK Community Installation Policies:
GNU Autoconf and CMake Options](https://figshare.com/articles/xSDK_Community_Installation_Policies_GNU_Autoconf_and_CMake_Options/4495133)

<item #>. [supported=yes|no|description]

1. yes
2. yes
3. yes
4. yes
5. yes
6. not needed, we have a fortran interface specific for PHASTA interactions
7. we only support double precision
8. we don't support this - it could be used to control `MDS_ID_TYPE`, but that seems like a stretch
9. we don't use blas/lapack
10. yes
11. yes
12. yes (https://github.com/cwsmith/core/commit/2b12df439deb581805272d87cfc0cb6b96e60054)
13. yes - this is provided by the SCORECConfig.cmake file in the <install_prefix>/lib/cmake/SCOREC/ and build directory

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| None. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| There are cmake options to enable valgrind when running the ctest test suite. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |None| None. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| None. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |partial| We provide a CMake package for other users of CMake; [example](https://github.com/SCOREC/core/blob/master/doc/user_CMakeLists.cmake). |
