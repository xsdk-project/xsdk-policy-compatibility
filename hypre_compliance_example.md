# xSDK Community Policy Compatibility for <enter name of your software>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**M1.** Support xSDK community GNU Autoconf or CMake options.
```
hypre is compliant. We had to modify Autoconf script options to use blas and lapack libraries were called in the standard way (--with-lapack-lib=LIBS or --with-blas-lib=LIBS, where LIBS is space-separated linkable list (enclosed in quotes) of libraries needed for lapack or blas. OK to use -L and -l flags in the list). We also had to ensure that user-provided paths to these options *were* used (not the system installed versions). 
```

**M2.** Provide a comprehensive test suite for correctness of installation verification.
```
hypre provides a script that can run a subset of the daily regression tests to satisfy this requirement.
```

**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD).
```
hypre is compliant.
```

**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF).
```
hypre is compliant.
```

**M5.** Provide a documented, reliable way to contact the development team.
```
hypre is compliant.
```

**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling).
```
hypre is compliant.
```

**M7.** Come with an open source (BSD style) license.
```
hypre is subject to the LGPL license version 2.1, which is considered acceptable since hypre is one of the original xSDK members.
```

**M8.** Provide a runtime API to return the current version number of the software.
```
hypre provides a script that prints the version number, date, and time.
```

**M9.** Use a limited and well-defined symbol, macro, library, and include file name space.
```
hypre satisfies this requirement by pre-pending macros, libraries and include file names with "HYPRE_" and "_hypre" to avoid namespace collisions with other packages.
```

**M10.** Provide an xSDK team accessible repository (not necessarily publicly available).
```
hypre is compliant. hypre releases are mirrored on github, which is accessible by the xSDK team.
```

**M11.** Have no hardwired print or IO statements that cannot be turned off.
```
hypre is compliant
```

**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software.
```
hypre is compliant.
```

**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib.
```
hypre is compliant.
```

**M14.** Be buildable using 64 bit pointers. 32 bit is optional.
```
hypre is compliant.
```

**M15.** All xSDK compatibility changes should be sustainable.
```
hypre is compliant
```

**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage.
```
hypre is compliant
```

**Recommended Policies**


**R1.** Have a public repository.
```
hypre does not have a public development repository, but mirrors hypre versions, including test versions as needed, on github.
```

**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues.
```
hypre is compliant
```

**R3.** Adopt and document consistent system for error conditions/exceptions.
```
hypre is approaching compliance. Error checking framework exists, but is not consistent everywhere in the library.
```

**R4.** Free all system resources acquired as soon as they are no longer needed.
```
hypre is compliant
```

**R5.** Provide a mechanism to export ordered list of library dependencies.
```

```


