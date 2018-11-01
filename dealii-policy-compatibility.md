# xSDK Community Policy Compatibility for deal.II

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** http://www.dealii.org

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| deal.II uses cmake.|
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| deal.II has a testsuite that runs a large number of tests in debug mode, release mode, or both. As of early 2018, the total number of tests when all external dependencies are configured is around 9,500.|
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| All objects take a communicator via the constructor. `MPI_COMM_WORLD` is only used as a default argument, but no part of the library assumes that things *have* to work on `MPI_COMM_WORLD`.  |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| We strive to build on all platforms, and test regularly with GNU, Clang, and other compilers. We consider the inability of building on a platform as a bug. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| Mailing list addresses are provided at http://www.dealii.org . |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| Yes. The only exception that comes to mind is that deal.II enables traps/exceptions when arithmetic operations encounter signaling NaNs. We use signaling NaNs in deal.II to default initialize objects with invalid values to ensure they cannot be used before receiving proper values.|
|**M7.** Come with an open source (BSD style) license. |Full| LGPL. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| Via `Utilities::dealii_version_string()`. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. | Mostly| All header files are prefixed with `deal.II/`. All C++ names are in a namespace `dealii::`. (The exception of a few overloads of `std::pow`, `std::sin`, etc with arguments that are classes in namespace `dealii` -- consequently, these overloads cannot clash with other libraries.) Almost all macros are prefixed with `DEAL_II_`. The exception are a few macros for exception-related things; namely, `Assert`, `AssertThrow`, `AssertNothrow`, and a set of macros with names `DeclException*`. Note: It was decided that these names do not need to be changed since changes would affect hundreds of users, and the risk is considered very low, since there have not been any conflicts for dealii in the past when interoperating with many other packages. Should there be any issues in the future, this will be revisited. What I want to say is that we're reluctant to make a change in the names of macros that are widely used among our users. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| https://github.com/dealii/dealii |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| Yes. All logging is off by default. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| Yes. This is true for all dependencies. We bundle BOOST, TBB, and UMFPACK, but cmake will use an external version if one can be found. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| Yes. The install path is chosen via `CMAKE_INSTALL_PREFIX`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| We make no assumptions. Whatever the compiler wants to use. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Yes. Rather than providing the xSDK options as add ons, we have incorporated them fully into the basic deal.II infrastructure, so that xSDK options get the same maintaince and support as any other feature. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| Yes. deal.II is supported by SPACK. |


### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full | http://github.com/dealii/dealii |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. | Full | Yes, see http://dealii.org/developer/developers/testsuite.html . |
|**R3.** Adopt and document consistent system for error conditions/exceptions. | Yes | Yes, we have a system of macros that is uniformly used for this. Errors either lead to termination of the program if, for example, a function is called with invalid arguments (but this can be switched to reporting C++ exceptions). All other error conditions lead to throwing C++ exceptions. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Yes, that's the goal, with the exception of the GrowingVectorMemory class that keeps a global cache of vectors for re-use in contexts where frequent allocation/deallocation of vectors happens. The cached vectors can, however, be explicitly freed when necessary. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| Via cmake. |
