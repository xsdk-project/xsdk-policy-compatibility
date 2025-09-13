# xSDK Community Policy Compatibility for MAGMA

In this document, we present a summary the continuing efforts of the current
and future xSDK packages to achieve compatibility with the xSDK
community policies.  What is available below is only a short description of
each item of the policy.  The full description is available as an
[online document](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be consulted while filling out or cross-checking this form.

Information on the compatibility status for each mandatory policy (M1, M2, ...)
is provided below.  Recommended policies (R1, R2, ...) are addressed as well as
their are applicable or have been implemented.  If the package is not
compatible, it is stated what is lacking and what are the specific plans on how
to achieve compliance.

For current xSDK packages: non-compliance at some point in time should
be described and the steps that were undertaken to fulfill the policy. This
information should be helpful for future xSDK packages.

An xSDK compatible package is considered to be a member package if it uses, or can be used by another package in the xSDK.

**Website:**  [MAGMA website on GitHub](https://github.com/icl-utk-edu/magma/)

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| MAGMA uses CMake for configuration with `CMakeLists.txt` files in all build directories. These files are used in a standard fashion during and integrated into the Spack package for MAGMA. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| MAGMA has a test for every user-facing routine in the library. In addition, it contains a command-line test harness that is capable of performing additional tests for both correctness and performance. The failed tests are reported in a formatted form that may be used in automated tools that analyze software development process such as Continuous Integration such as [Bitten](https://bitten.edgewall.org/), [TinderBox](http://www.mozilla.org/tinderbox.html), or [BuildBot](http://buildbot.sourceforge.net/). |
|**M3.** Employ user-provided MPI communicator (no `MPI_COMM_WORLD`). |Not-Applicable| MAGMA does not use MPI. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| MAGMA CI includes both gcc and clang, and all releases are tested on the aforementioned DoE machines. The GPU-enabled DOE platforms have support for recent CUDA and HIP versions that are also supported by MAGMA. The configuration test is run during the installation to test and inform the user about the compatibility.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| MAGMA developers can be contacted via [web forum](https://groups.google.com/a/icl.utk.edu/g/magma-user) that is linked from the [MAGMA](http://icl.utk.edu/magma/) web page. The forum is active and receives steady flow of web traffic (human, not bot-related) and is cross-referenced by major web search engines.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| MAGMA supports immediate error reporting. MAGMA provides initialization and finalization routines that may be invoked multiple times during the program execution to complete setup and clean up the internal state of MAGMA.|
|**M7.** Come with an open source (BSD style) license. |Full| MAGMA is distributed under 3-clause BSD (AKA modified BSD) license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| MAGMA has `magma_version()` function that returns version number (major, minor, micro) at runtime. API version number is defined in the MAGMA header files as `MAGMA_API` macro.|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| MAGMA header files are prefixed with `magma` string. The library names begin with `libmagma`. Global linker symbols begin with `magma_` prefix and C preprocessor macros begin with `MAGMA`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| MAGMA is hosted in a public repository on GitHub: [https://github.com/icl-utk-edu/magma/](https://github.com/icl-utk-edu/magma/). |
|**M11.** Have no hardwired print or I/O statements that cannot be turned off. |Full| MAGMA library reports errors as return values from function calls only (no I/O). The tester is a standalone executable that links against the MAGMA libraries and prints test results but the tester is not necessary to use the MAGMA library.|
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is fully implemented as MAGMA may be linked against BLAS, CBLAS, LAPACK, and LAPACKE provided by Intel MKL, Netlib, or OpenBLAS.|
|**M13.** Install headers and libraries under `PREFIX/include` and `PREFIX/lib`. |Full| MAGMA uses the install prefix as a configuration variable. This is available through the CMake's standard behavior by accepting `--prefix` command line option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| MAGMA supports builds with both 32- and 64-bit pointers without changes to the API syntax. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| MAGMA has been under continuous development with most of the xSDK practices maintained across many releases and there are no plans to stop them.  |
|**M16.** Have a debug build option. |Full| MAGMA has had a Spack package for some time now and is available from within xSDK Spack package for GPU-enabled (debug or release) builds. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| MAGMA has a publicly available GitHub repository accessible at [https://github.com/icl-utk-edu/magma/](https://github.com/icl-utk-edu/magma/) |
|**R2.** Possible to run test suite under `valgrind` in order to test for memory corruption issues. |Partial| This might be possible but has not been tested with the newer releases with newer CUDA and HIP versions. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full|  Available in MAGMA's [documentation pages](http://icl.cs.utk.edu/projectsfiles/magma/doxygen/) generated automatically by Doxygen. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| MAGMA has both initialization and finalization routines that may be used repeatedly throughout the code to limit resource utilization. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Partial| MAGMA releases produces configuration hooks for `pkg-config` but the newest releases might not support this functionality consistently across DOE sites. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form. |Partial| MAGMA has detailed installation instructions with a full list of tested external dependencies and examples (available on GitHub and doxygen). |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory. |Partial| MAGMA has README, SUPPORT (part of README), LICENSE (in COPYRIGHT), and CHANGELOG (in ReleaseNotes) in top directory. |
|**R8.** Provide sufficient documentation to support use and further development. |Full| MAGMA is fully documented and provides a Cotributors' guide (in MAGMA doxygen documentation). |
