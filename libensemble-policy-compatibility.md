# xSDK Community Policy Compatibility for libEnsemble>

This document summarizes the efforts of current and future xSDK member packages to achieve compatibility with the xSDK community policies. Below only short descriptions of each policy are provided. The full description is available [here](https://github.com/xsdk-project/xsdk-community-policies)
and should be considered when filling out this form.

*** A good example of how to complete this form can be found in the [PETSc version](https://github.com/xsdk-project/xsdk-policy-compatibility/blob/master/petsc-policy-compatibility.md).

Please, provide information on your compatibility status for each mandatory policy, and if possible also for recommended policies.
If you are not compatible, state what is lacking and what are your plans on how to achieve compliance.

For current xSDK member packages: If you were not fully compatible at some point, please describe the steps you undertook to fulfill the policy. This information will be helpful for future xSDK member packages.

**Website:** https://github.com/Libensemble/libensemble

### Mandatory Policies

[General libEnsemble Note](#liben-note)

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**M1.** Support xSDK community GNU Autoconf or CMake options. |Full| libEnsemble is in the Spack repository and can be installed with `spack install py-libensemble`. The build tool used is `pip`, and the package is installed either from PyPI, for released versions, or GitHub, for the development version. GNU Autoconf or CMake are not typical for a Python package. Recommendation: `pip install` is required for Python packages.
|**M2.** Provide a comprehensive test suite for correctness of installation verification. |Full| libEnsemble has a test suite that includes both unit tests and regression tests that are run on every push to GitHub via Travis CI. In addition to this test suite, further scaling tests are run, currently manually, on HPC platforms including Theta and Summit. [M2 details](#m2-details)
|**M3.** Employ user-provided MPI communicator (no MPI_COMM_WORLD). |Full as of v0.5.2|libEnsemble takes an MPI communicator as an option; if libEnsemble is configured for MPI mode, this provided communicator will be employed. If no communicator is given, a duplicate of MPI_COMM_WORLD is taken as a default. |
|**M4.** Give best effort at portability to key architectures (standard Linux distributions, GNU, Clang, vendor compilers, and target machines at ALCF, NERSC, OLCF). |Full| libEnsemble is tested regularly on ALCF (Theta) and OLCF (Summit) platforms. NERSC (Cori) will be tested in the near future, although a Slurm-based system has been tested (ANL/Bebop). [M4 details](#m4-details)|
|**M5.** Provide a documented, reliable way to contact the development team. |Full| The libEnsemble team can be contacted through: 1) The public [issues page on GitHub](https://github.com/Libensemble/libensemble/issues). 2) [Slack](https://libensemble.slack.com). 3) The public email list libensemble@mcs.anl.gov. |
|**M6.** Respect system resources and settings made by other previously called packages (e.g. signal handling). |Full| libEnsemble does not override signal handling. |
|**M7.** Come with an open source (BSD style) license. |Full| libEnsemble uses a 3-clause BSD license stated in the LICENSE file in the top level of the GitHub repository. |
|**M8.** Provide a runtime API to return the current version number of the software. |Full| The version can be returned within python via: `libensemble.__version__`|
|**M9.** Use a limited and well-defined symbol, macro, library, and include file name space. |Full| libEnsemble functions and variables begin with `libensemble.`. |
|**M10.** Provide an xSDK team accessible repository (not necessarily publicly available). |Full| The libEnsemble repository is public and can be found at https://github.com/Libensemble/libensemble. Gitflow is used, along with pull requests, whereby only those with administrator privileges can accept pull requests into the master or develop branches. The workflow guidelines are provided in a CONTRIBUTING.rst file at the top level of the repository and a release process is given in the documentation. |
|**M11.** Have no hardwired print or IO statements that cannot be turned off. |Full as of v0.5.2| All output from the libEnsemble core package, except for the raising of exceptions, is routed through a libEnsemble logger, which is isolated from the Python root logger. Log messages of type `warning` or above are duplicated to standard error by default to ensure they are not missed. This can be turned off through the API. The API also allows the user to change the logging verbosity level and the name of the log file. This would allow a user, for example, to append logging to an existing log file, or to keep it separate. libEnsemble contains no interactive input. [M11 details](#m11-details)|
|**M12.** For external dependencies, allow installing, building, and linking against an outside copy of external software. |Full| libEnsemble does not contain any other package's source code within. Note that Python packages are imported using the conventional `sys.path` system. Alternative instances of a package can be used by, for example, including in the PYTHONPATH environment variable.|
|**M13.** Install headers and libraries under \<prefix\>/include and \<prefix\>/lib. |Full| The standard Python installation is used for Python dependencies. This installs external Python packages under `<install-prefix>/lib/python<X.Y>/site-packages/`|
|**M14.** Be buildable using 64 bit pointers. 32 bit is optional. |Full| There are no explicit uses of pointers in libEnsemble, as Python handles pointers internally and depends on the install of Python (e.g., CPython), which will generally be 64-bit on supported systems. |
|**M15.** All xSDK compatibility changes should be sustainable. |Full| All the changes here should be sustainable. |
|**M16.** The package must support production-quality installation compatible with the xSDK install tool and xSDK metapackage. |Full|libEnsemble configure and install has full support from Spack. |


M2 details<a id="m2-details"></a>: There are plans to replace manual HPC testing with GitLab CI under the ECP Continuous Integration Testing and Release project.

M4 details <a id="m4-details"></a>: libEnsemble is a Python code and so does not directly use compilers. It does, however, use NumPy, SciPy and mpi4py which use compiled extensions. The current CI tests of libEnsemble use the standard Cpython compatible builds of these extensions(which are built using the GNU compilers).

libEnsemble is currently supported on Linux platforms and macOS. Windows platforms are currently not supported. Testing supports Python versions >=3.4 (mirroring NumPy's support of Python 3).

Recommendation: For Python packages, we should consider policies for support of Python versions and possibly Python interpreter/compiler implementations (e.g. Cpython, pypy).
We should also consider support for Python software stacks (e.g. Intel distribution for Python).


M11 details <a id="m11-details"></a>: Note: The sub-packages in the libensemble directory structure such as `sim_specs` and `gen_specs` may contain print statements. These are considered examples for users, rather than core libEnsemble packages.

A special exception exists in the `node_resources.py` module; part of libEnsemble's resource detection infrastructure. The routine `_print_local_cpu_resources()` can be launched by libEnsemble to probe resources on a target node, and the output of this independent program is captured by libEnsemble.



### Recommended Policies

| Policy                 |Support| Notes                   |
|------------------------|-------|-------------------------|
|**R1.** Have a public repository. |Full| Yes (see M10 above). |
|**R2.** Possible to run test suite under valgrind in order to test for memory corruption issues. |Full| Since it is a Python code, there is no explicit memory allocation in libEnsemble; memory safeguards such as bounds checking are a part of Python. Flake8 is run as part of the test suite, which performs both static syntax checking and style checks for PEP 8 compliance (with a few selected guidelines ignored). |
|**R3.** Adopt and document consistent system for error conditions/exceptions. |Full| libEnsemble defines and raises exceptions according to module. All exceptions on workers are passed to the manager for processing.  Warnings are handled by the logger. [R3 details](#r3-details)||
|**R4.** Free all system resources acquired as soon as they are no longer needed. |Full| Python has in-build garbage collection when memory becomes unreferenced. When opening files, wherever possible, the`with` expressions or `try/finally` block, is used to ensure file handles are closed, even in the case of an error. The specific mechanism for freeing up resources depends on the communication mechanism employed. We intend to add to our test suite in order to include this check for all types of supported communications. |
|**R5.** Provide a mechanism to export ordered list of library dependencies. |Full as of v0.5.2| The dependencies for libEnsemble are given in `setup.py` and when pip install or pip setup.py egg_info are run, a file is created `libensemble.egg-info/requires.txt` containing the list of required and optional dependencies. If installing through pip, these will automatically be installed if they do not exist (`pip install libensemble` installs req. dependencies, while `pip install libensemble[extras]` installs both required and optional dependencies.|
|**R6.** Document versions of packages that it works with or depends upon, preferably in machine-readable form.  |Full| Dependencies are given in the documentation. In some cases, this includes a lower bound on version number.|
|**R7.** Have README, SUPPORT, LICENSE, and CHANGELOG files in top directory.  |Full as of v0.5.2| Files have been moved/created to meet this policy.|


R3 details <a id="r3-details"></a>: libEnsemble catches all exceptions (explicitly raised and unexpected) from the manager and worker processes at the libEnsemble level, resulting in libEnsemble dumping the key ensemble state to files. In mpi4py mode, the default is to then call MPI_ABORT to prevent a hang. However, this can be turned off (via the libE_specs argument). In the case it is turned off, or if other comms modes are used, the exception is then raised. The user can in turn catch these exceptions from their calling script. In future, alternative options may be provided for the ensemble to recover from some exceptions. E.g. by removing a worker.


libEnsemble Note <a id="liben-note"></a>: The nature of libEnsemble's interoperability with other libraries is different from typical xSDK libraries. libEnsemble is a Python code and interaction with other libraries may take several forms. These include: libEnsemble calling other libraries through Python bindings, libEnsemble launching applications (possibly providing a sub-communicator), libEnsemble being called from a Python level infrastructure, libEnsemble being launched as part of a campaign level workflow, or libEnsemble potentially being activated via a system call or embedded interpreter; a more unconventional approach.

This is, therefore, a good opportunity to consider interoperability from a Python and broader workflow perspective.
