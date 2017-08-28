# xSDK Community Policy Compatibility for <enter name of your software>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://docs.google.com/document/d/1DCx2Duijb0COESCuxwEEK1j0BPe2cTIJ-AjtJxt3290/edit#heading=h.2hp5zbf0n3o3)
and should be considered when filling out this form.

Please, provide information on your compability status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.
For current xSDK member packages: If you were not compliant at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**M1.** Support xSDK community GNU Autoconf or CMake options.
```

```

**M2.** Provide a comprehensive test suite for correctness of installation verification.
```

```

**M3.** Employ userprovided MPI communicator (no MPI_COMM_WORLD).
```

```

**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF).
```

```

**M5.** Provide a documented, reliable way to contact the development team.
```

```

**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling).
```

```

**M7.** Come with an open source (BSD style) license.
```

```

**M8.** Provide a runtime API to return the current version number of the software.
```

```

**M9.** Use a limited and well-defined symbol, macro, library, and include file name space.
```

```

**M10.** Provide an xSDK team accessible repository (not necessarily publicly available).
```

```

**M11.** Have no hardwired print or IO statements that cannot be turned off.
```

```

**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software.
```

```

**M13.** Install headers and libraries under \<prefix\>/inlude and \<prefix\>/lib.
```

```

**M14.** Be buildable using 64 bit pointers. 32 bit is optional.
```

```

**M15.** All xSDK compatibility changes should be sustainable.
```

```

**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage.
```

```

**Recommended Policies**


**R1.** Have a public repository.
```

```

**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues.
```

```

**R3.** Adopt and document consistent system for error conditions/exceptions.
```

```

**R4.** Free all system resources acquired as soon as they are no longer needed.
```

```

**R5.** Provide a mechanism to export ordered list of library dependencies.
```

```


