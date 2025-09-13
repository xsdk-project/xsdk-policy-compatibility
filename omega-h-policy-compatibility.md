# xSDK Community Policy Compatibility for Omega_h

This document summarizes the efforts of current and future xSDK packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

**Website:** https://github.com/sandialabs/omega_h

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| Omega\_h follows all xSDK Community Installation Policies|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| Omega_h supports `make test_install`. |
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Partial| `Omega_h::Library` takes an `MPI_Comm` argument, nothing uses `MPI_COMM_WORLD`. A PR was created to address [MPI 3 version checking](https://github.com/sandialabs/omega_h/pull/374). |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Omega_h supports GNU, Clang, NVCC, Intel, and other compilers, and optionally uses MPI, OpenMP, and/or CUDA for parallelism through Kokkos.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| GitHub provides the mechanism for contacting the developer. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| We do. |
|**M7.** Come with an open source (BSD style) license. |Full| Omega_h is released under the 2-clause BSD license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| `const char* version = Omega_h::Library::static_version()`. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| All linkable symbols are in C++ namespace `Omega_h`, all macros begin with `OMEGA_H`, all files begin with `Omega_h`, all executables include `osh` in a non-abiguous way as part of the name, and the library is called `libomega_h`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| We provide a GitHub repository. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Omega_h has some prints that are on by default, but all print statements can be turned off by various API inputs. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is the only way Omega_h brings in software which is separately available. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| We do. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Omega_h builds with 64-bit pointers. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| They are. |
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| None. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| GitHub repository. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| `-DOmega_h_VALGRIND="valgrind <args>"` to CMake. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| Omega_h has a compile option `-DOmega_h_THROW:BOOL=ON` that enables consistent exceptions. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| We do. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Omega_h's build system exports such text files. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  | Partial | For packages in Spack, this is documented in the Spack package file. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  | Partial | We have README and LICENSE. |
|**R8.** Each xSDK package should have sufficient documentation to support use and further development.  |Partial| There are usage examples but no developer docs. |
