# What's new?

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
