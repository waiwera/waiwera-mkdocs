# What's new?

## Waiwera 1.4.0 released

**30 June 2023** - Waiwera version 1.4.0 is now released.

The changes in this version include:

- **source networks**, representing interacting networks of sources
  and sinks, for modelling e.g. multi-feed wells, borefields with
  grouped production wells (and optional limits or targets imposed on
  the group), or reinjection

- **salt equation of state modules** - Waiwera now includes three new
  EOS modules for modelling mixtures of non-isothermal water, salt
  (sodium chloride) and non-condensible gases (currently carbon
  dioxide or air). These new EOS modules are `wse` (water, salt,
  energy), `wsae` (water, salt, air, energy) and `wsce` (water, salt,
  carbon dioxide, energy).

- allowing sources with no associated cell (e.g. for reinjection outside
  the model)

- allowing unlimited number of time steps (by setting
  `time.step.maximum.number` to `null`)

- various minor code modifications to allow building Waiwera using
  newer versions (10, 11) of `gfortran`

## Waiwera 1.3.1 released

**29 June 2022** - Waiwera version 1.3.1 is now released.

The changes in this version include:

- **time-dependent rock properties** - rock permeabilities and
  porosities can now be assigned prescribed time-dependent values.

- modified handling of **Dirichlet boundary conditions** - equations
  for boundary ghost cells are no longer included in the Jacobian
  matrix (used to solve the non-linear flow equations at each time
  step). This makes the Jacobian significantly less ill-conditioned
  and slightly smaller.

- **Jacobian output** - Jacobian matrices can now be optionally output
  to a binary file. These may be used e.g. for inverse modelling or
  uncertainty quantification.
- added ability to set Jacobian **differencing parameters** in input
  (rather than as PETSc arguments).

- Modified time stepping behaviour around **checkpoints** - the
  pre-checkpoint time step size is now restored after hitting a
  checkpoint.

- **PETSc update** - PETSc version 3.15.5 will be downloaded and built
  if PETSc is not found on the system.

## Waiwera 1.3.0 released

**8 September 2021** - Waiwera version 1.3.0 is now released.

The changes in this version include:

- **tracers** - Waiwera can now simulate passive tracers. Any number
  of tracers can be simulated, in conjunction with any equation of
  state. Tracers may be either liquid-phase or vapour-phase, and the
  effects of diffusion and decay can be included. Decay can be
  constant or temperature-dependent. The tracer equations are solved
  independently of the flow equations, with only one additional linear
  solve needed per time step.

- **output at faces** - Waiwera can now optionally output results on
  mesh faces, e.g. component or phase mass or energy fluxes, and also
  face geometry (areas etc.) to the output HDF5 file. Face output is
  fully configurable by the user. It is also now possible to control
  (e.g. omit) the output of cell geometry data.

- **PETSc update** - PETSc version 3.15.2 or later is now required,
  and PETSc 3.15.4 will be downloaded and built if PETSc is not found
  on the system.

- new output datasets in the HDF5 file to simplify post-processing
  **MINC** simulations - these contain the MINC level and parent cell
  index for each cell in the output

- the Waiwera **Docker** images should now run on older
  CPUs. Previously the Docker images contained a PETSc library built
  using compiler settings which prevented it from running on older
  CPUs. This is now built using more generic settings so it should run
  on any x86 CPU capable of running Docker.

- a fix for a minor issue which prevented **native Linux builds** on
  distributions which no longer have Python 2 installed by default
  (e.g. Ubuntu 20.04)

- the user guide has new material on using the recently-released
  [Layermesh](https://github.com/acroucher/layermesh) library to
  create meshes for Waiwera models, and use them for pre- and
  post-processing

- the Waiwera **continuous integration** (CI) pipeline has been
  transferred from Travis CI to Github Actions

## Waiwera 1.2.1 released

**20 July 2020** - Waiwera version 1.2.1 is now released.

The main change in this version is that the installation process will
now install [MPICH](https://www.mpich.org/) instead of
[OpenMPI](https://www.open-mpi.org/), if it does not detect any
existing MPI on the system.

This change was prompted by an apparent memory leak (possibly [this
one](https://github.com/open-mpi/ompi/issues/4567)) in some versions
of OpenMPI, including version 3.1.3 which was used in the Waiwera 1.2
Docker image.

That version of OpenMPI also has [another
bug](https://github.com/open-mpi/ompi/issues/4948) which causes error
messages when running in Docker containers. Waiwera 1.2 introduced a
workaround for this bug in the `waiwera-dkr` script, but with the
change to MPICH this is no longer needed, and has now been removed.

## Waiwera 1.2 released

**8 June 2020** - Waiwera version 1.2 is now released.

The changes in this version include:

- **PETSc update**: PETSc version 3.13.2 or later is now required, and
    PETSc 3.13.2 will be downloaded and built if PETSc is not found on
    the system.

- this new version of PETSc includes substantial modifications to the
    DMPlex class, including the ability to handle **hybrid meshes**
    with arbitrary mixes of cell types (8-node hexahedron, 6-node
    wedge, etc.). This means Waiwera is also now able to handle these
    meshes.

- a modification to the behaviour of the **deliverability** source
  control when a threshold pressure is specified. The deliverability
  control will now deactivate if the computed flow rate is larger in
  magnitude than the specified production rate (which can happen for
  time-dependent specified flow rates).

- the Waiwera executable now has `--version` and `--help` **command
  line arguments**. Running with no arguments now gives the more
  common behaviour of printing the help information, rather than
  prompting for a filename.

- the Travis continuous integration (**CI**) pipeline now includes the
  full suite of **benchmark tests** as well as just the unit tests.

- users can now run the **benchmark tests** via **Docker**, by passing
  the `--docker` argument to the benchmark test script.

- Waiwera Docker images are now based on a **Debian 10** base image
  (was Debian 9 in previous versions).

- the `waiwera-dkr` utility now has `--version` and revised `--help`
  arguments, and its default number of parallel processes is now 1
  (rather than the maximum available).

## Waiwera journal article published

** 23 May 2020** - the journal Computers and Geosciences has just
   published a [research
   article](https://doi.org/10.1016/j.cageo.2020.104529) titled
   **"Waiwera: a parallel open-source geothermal flow simulator"**.

This contains details on why Waiwera was written, the governing
   equations used, numerical formulation and other implementation
   details, as well as results from various test problems.

## Waiwera 1.1 released

**31 January 2020** - Waiwera version 1.1 is now released. This is a significant update and includes the following changes:

- **MINC mesh rebalancing**: after MINC processing, the mesh is
  redistributed to regain optimal load balancing, and hence better
  scaling behaviour for large parallel MINC problems. This entailed a
  substantial rewrite of parts of the Waiwera MINC code.
- **PETSc update**: PETSc version 3.12 or later is now required (some
  of its new features and bugfixes are needed for the MINC mesh
  rebalancing). If PETSc is not found on the system, version 3.12.3
  will be downloaded and built.
- **PyWaiwera**: this is a new Python library for working with Waiwera
  simulations. Its source is in the main Waiwera source tree under
  `/utils/pywaiwera`, and it can be installed from PyPI using
  `pip`. For now, it contains only code related to running Waiwera via
  Docker, either from Python scripts or from the command line, for
  which it installs an executable `waiwera-dkr` script (which replaces
  the previous `waiwera-dkr.py` script). In future it is invisaged
  that other modules will be added to PyWaiwera, for assisting with
  pre- and post-processing.
- the new **`waiwera-dkr`** script includes many improvements and some
  new features, for example downloading example model input files
  using the `--examples` option.
- **continuous integration** (CI) using [Travis](https://travis-ci.org/)
  for automated building/testing of Waiwera.
- additional **log file** messages for reporting simulation degrees of
  freedom and imbalance statistics, as well as linear solver iteration
  counts

## Waiwera 1.0 released

**24 November 2019** - Waiwera version 1.0 has just been released, after five years of development and testing.

The Waiwera team would like to thank everyone who contributed to making this possible, including [MBIE](https://www.mbie.govt.nz/) and [Contact Energy](https://contact.co.nz/) for financial support; Matt Knepley and others on the [PETSc](https://www.mcs.anl.gov/petsc/) team, for invaluable advice and support; and [Joseph Levin](https://github.com/josephalevin) for developing the [FSON](https://github.com/josephalevin/fson) library.
