# xSDK Community Policy Compatibility for preCICE

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** http://precice.org

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| preCICE implements all requirements in its CMake build script. [Read more](https://github.com/precice/precice/wiki/Building:-Using-CMake#xsdk-compliance)
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| preCICE has an extensive test suite consisting of traditional unit tests, and integration tests based on MPI. We also run system tests to test provided adapters and perform numerical validation. [Read more](https://github.com/precice/precice/wiki/Tests)
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). Don't assume a full MPI 3 implementation without checking. Provide an option to prevent any changes to MPI error-handling if it is changed by default. |Full| One can pass a custom communicator to each `precice::SolverInterface`. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| preCICE is tested with gcc and clang u tested with gcc and clang. It is used on a wide variety of machines and we [maintain information](https://github.com/precice/precice/wiki/Get-preCICE) for relevant HPC systems. |
|**M5.** Provide a documented, reliable way to contact the development team. |Full| We provide support via [GitHub](https://github.com/precice/precice/issues), [Gitter chat](https://gitter.im/precice/Lobby) and an [open mailing list](https://mailman.informatik.uni-stuttgart.de/mailman/listinfo/precice). |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| No signal handlers past 1.5.2 |
|**M7.** Come with an open source (BSD style) license. |Full| preCICE is licensed under the LGPLv3 license |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| `precice::getVersionInformation()` |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| Symbol namespace is `precice::`. Include namespace is `precice/`. Macro prefix is `PRECICE_`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| Our code is hosted on [GitHub](https://github.com/precice/precice) |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| The library provides log configuration via the main XML configuration file and an easy-to-generate `log.conf`. [Read more](https://github.com/precice/precice/wiki/Logging-Configuration) |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| preCICE internally use use `nlohmann/json` and `prettyprint`. For overrides, see **M1**. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| preCICE respects the `CMAKE_INSTALL_PREFIX`. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| preCICE always uses the native pointer size. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All policies are part of the normal releases. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full| preCICE core developers maintain the `precice` Spack package. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| [GitHub](https://github.com/precice/precice) |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Yes |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Partial| [Work in progress!](https://github.com/precice/precice/issues/280) We have strong culture of using assertions. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Yes and we constantly improve the resource management through modernization, clang-tidy, sanitizers and valgrind/heaptrack and code reviews. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| Spack can be used to generate this graph. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Partial| Work in Progress |
