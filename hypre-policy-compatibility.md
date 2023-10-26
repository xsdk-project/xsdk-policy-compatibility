# xSDK Community Policy Compatibility for *hypre*

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [hypre version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/hypre-policy-compatibility.md).

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Web site**: http://www.llnl.gov/casc/hypre

### Mandatory Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support portable installation through Spack. |Full| *hypre* supports and provides a Spack package. |
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| *hypre* provides a script (make checkpar) that runs a subset of the daily regression tests to satisfy this requirement. |
|**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD). |Full| None. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| Being written entirely in C, *hypre* has generally been very portable, and will continue to be due to strong customer demand. In addition, daily/weekly regression tests are performed on various architectures with different compilers.|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The *hypre* team can be contacted via email: hypre-support@llnl.gov . Issues can also be reported at https://github.com/hypre-space/hypre . |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| None. |
|**M7.** Come with an open source (BSD style) license. |Full| *hypre* is one of the original xSDK packages and uses the LGPL License v. 2.1. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| *hypre* provides a script and a macro that returns the version number. |
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| *hypre* prepends macros, library and include file names with HYPRE_ or hypre_ to avoid namespace collisions with other packages. |
|**M10.** Provide a publicly available repository. |Full| *hypre*'s repository is publically available at https://github.com/hypre-space/hypre. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full| All hardwired print statements have been removed. |
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| This is how *hypre* is generally used. |
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| None. |
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| None. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| Every effort is made for *hypre* to be backwards compatible. |
|**M16.** Have a debug build option. |Full| *hypre* provides such an option with --enable-debug. |
|**M17.** Each xSDK member package should have sufficient documentation to support use and further development.  |Partial| There is full documentation for usage as well as example codes, there is an old developer manual, which needs to be updated or completely replaced. |

### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** At least one validation (smoke) test that can be invoked through the Spack package. |Full| hypre provides such a smoke test. |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| *hypre* has completely moved to valgrind for memory regression tests. |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Partial | *hypre* has a system for error conditions, Which is documented in the users guide, but has not been completely implemented throughout the whole library. |
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| All resources are freed as soon as they are no longer needed as long as the required functions are used to free them, as described in the users and reference manuals. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |None| None. |
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |None| None. |
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Full| None. |
|**R8.** Provide version comparison preprocessor macros. |Full| None. |
