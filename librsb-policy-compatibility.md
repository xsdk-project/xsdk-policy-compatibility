# xSDK Community Policy Compatibility for librsb

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** http://librsb.sourceforge.net/

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| librsb uses GNU Autoconf and Automake. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| librsb relies on 'make qtests', 'make tests', 'make devtests' for triggering respectively quick, long, and devel-oriented tests. Sample results can be seen in routine builds on e.g. the Debian Build system,  [see 'status' link next to each platform](https://buildd.debian.org/status/package.php?p=librsb)|
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| librsb does not use MPI or MPI communicators in any way. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| (librsb is widely available on many platforms already, please see the Debian Package Auto-Building status for librsb)[https://buildd.debian.org/status/package.php?p=librsb]. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| (This way:)[http://librsb.sourceforge.net/#a_contacts]. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Library functions of librsb do not not call signal() or similar functions. |
|**M7.** Come with an open source (BSD style) license. |Full| librsb is licensed under the LGPLv3 license. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| `RSB_LIBRSB_VER_STRING`,`RSB_HEADER_VERSION_STRING`,`RSB_LIBRSB_VER`,`RSB_LIBRSB_VER_MAJOR`,`RSB_LIBRSB_VER_MINOR` from `rsb.h`. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Symbols exported by librsb begin with `rsb_`; tests in `make devtests` enforce that. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Public GIT repository access planned; current non-public repository read-only access available on xSDK team request. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| There are several verbosity levels; quiet mode is one of those. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Optional dependencies are `libhwloc` and `rpc/xdr.h`. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Yes, you can specify that via the `configure`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| Yes: librsb: supports both 32 and 64 bit under the same API (example again on the Debian Package Auto-Building status)[https://buildd.debian.org/status/package.php?p=librsb]. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Sure: he xSDK compatibility changes seem reasonable and good software practices. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| Sure: apart from being distributed on many platforms,  (librsb is also in Spack already)[https://github.com/spack/spack/tree/develop/var/spack/repos/builtin/packages/librsb]. |

M1 details <a id="m1-details"></a>: optional: provide more details about approach to addressing topic M1.

M2 details <a id="m2-details"></a>: optional: provide more details about approach to addressing topic M2.

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Partial| Repo is currently access controlled but available as release tarfile. It shall soon in a publically readable GIT repository. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Sure, see the `scripts/callgrind.sh` script. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| There is a `rsb_perror()` function, and many numerical return error codes, and many more options for that, including verbosity levels and optional stack tracing . |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Sure: debug-enabled librsb has `rsb_lib_exit` finalization routine even check for correct deallocation of memory resources. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full| Sure: invoking `librsb-config --ldflags`. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| It depends on a C/Fortran compiler with OpenMP, plus `libhwloc` and `rpc/xdr.h`, and that is being checked by the `configure` script. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| README is there, LICENSE no but COPYNG yes, and CHANGELOG empty but changelog info is in the README. A SUPPORT file may be added. |
