# xSDK Community Policy Compatibility for PLASMA

In this document, we summarize the continuing efforts of the current and future
xSDK packages to achieve compatibility with the xSDK community policies.
What is available below is only a short description of each item of the policy.
The full description is available as an
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

**Website:**  [PLASMA website on Bitbucket](https://github.com/icl-utk-edu/plasma)

**Member:** yes

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| PLASMA versions since 2017 are available in a Spack package with suitable variants and verified dependencies and version conflicts.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| PLASMA has a test for every user-facing routine in the library. In addition, it contains a command-line test harness, build under name `plasmatest`, that is capable of performing additional tests for both correctness and performance. The information on the failed tests is provided in a formatted form that may easily be parsed by automated tools that analyze software development process such as Continuous Integration.|
|**M3.** Employ user-provided MPI communicator (no `MPI_COMM_WORLD`). |Not Applicable| PLASMA does not use MPI. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| PLASMA supports compilers implementing OpenMP 4 and higher and they are available across the DOE platforms: ALCF, NERSC, OLCF. The configuration test is run during the installation to verify the compatibility for the user.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| PLASMA developers can be contacted via issues on its [Github page](https://github.com/icl-utk-edu/plasma) or via email through [Google Mailing list](https://groups.google.com/a/icl.utk.edu/forum/#!forum/plasma-user) that is linked from the PLASMA Github page.|
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| PLASMA supports immediate error reporting as well as gradual error handling across a sequence of asynchronous routine calls. PLASMA provides initialization and finalization routines that may be invoked multiple times program life time to complete setup and clean up the internal state of PLASMA and release the resources allocated for its use.|
|**M7.** Come with an open source (BSD style) license. |Full| All of PLASMA's source code is distributed under 3-clause BSD (AKA modified BSD) license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| PLASMA provides full version information consisting of major, minor, micro, and patch components that can be accessed from the `plasma.h` header file that is installed with the rest of the PLASMA components. |
|**M9.** Use a limited and well-defined symbol, macro, library, and header file name space. |Full| PLASMA header files that are installed on the system are all prefixed with `plasma_`. The two installed libraries use `libplasma` prefix: one library begins with `libplasma` and the other `libplasma_coreblas`. Global symbols begin with `plasma_` or `plasma_coreblas_`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| PLASMA is hosted in a public repository on Github: [ssh://git@github.com:icl-utk-edu/plasma](ssh://git@bgithub.com:icl-utk-edu/plasma) and has publicly accessible release tar-balls. |
|**M11.** Have no hardwired print or I/O statements that cannot be turned off. |Full| Normal operation does not produce any I/O in PLASMA. The amount of I/O is limited to error messages that are fatal in the PLASMA tester execution. These are crucial for debugging in case testing of the installation fails and disabling them would make it hard to fix installation bugs. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is fully implemented as PLASMA may be linked against BLAS, CBLAS, LAPACK, and LAPACKE provided by Intel MKL, Netlib, or OpenBLAS.|
|**M13.** Install headers and libraries under `PREFIX/include` and `PREFIX/lib`. |Full| PLASMA uses the install prefix as a configuration variable. This is available through the CMake's standard behavior by accepting `--prefix`-style command line option. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| PLASMA supports builds with both 32- and 64-bit pointers without changes to the API syntax. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| PLASMA release features have been practiced for many versions and there are plans to continue them for the foreseeable future. The new CMake-enabled configuration is also part of the development process now.|
|**M16.** Any xSDK-compatible package that compiles code should have a configuration option to build in Debug mode. |Full| PLASMA allows debug or release configurations that are provided by its CMake script. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| PLASMA is publicly available at [ssh://git@github.com:icl-utk-edu/plasma](ssh://git@github.com:icl-utk-edu/plasma) |
|**R2.** Possible to run test suite under `valgrind` in order to test for memory corruption issues. |Full| This is possible for tests with the OpenMP runtimes compatible with `valgrind` for reasons of scalability and lack of dead-locks. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full|  The generated errors are available in PLASMA's [documentation pages](http://icl.bitbucket.io/plasma/) generated by Doxygen. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| PLASMA has both initialization and finalization routines that may be used repeatedly throughout the code to limit resource utilization. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| New PLASMA release exports configuration details as a header file that is generated during configuration stage and through CMake's installation process. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| PLASMA depends on number of compiler and library features that are documented through CMake and Spack.|
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| PLASMA has `README.md`, `LICENCE`, and `ChangeLog` files in top directory, support contacts are in `README.md` |
|**R8.** Each xSDK package should have sufficient documentation to support use and further development.  |Full| The majority of PLASMA's public and private functions are extensively documented through Doxygen and the development process uses the common Git flow model that is documented on external sites. |
