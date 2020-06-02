# Installation

Waiwera can be run on most operating systems (e.g. Linux, Windows, Mac
OS) using [Docker](install.md#using-docker). For many users this will
be the easiest option. Linux users also have the option of building a
[native Waiwera executable](install.md#native-linux-build).

For full details, see the installation
[instructions](https://waiwera.readthedocs.io/en/latest/installation.html)
in the Waiwera user guide.

## Using Docker

When using [Docker](https://www.docker.com/), Waiwera is run in a
"container" holding the code and all its dependencies, isolated from
the host machine, so that it should always run the same way.

First, Docker itself needs to be installed.

### Installing Docker

For Windows users, the Windows 10 Pro, Enterprise or Education
versions are recommended, in which case **Docker Desktop** can be
used. For other Windows versions, the older **Docker Toolbox** can be
used, but this is less convenient and has a higher performance
overhead than Docker Desktop.

Similarly, users of macOS version 10.13 or later can use Docker
Desktop, but users of older versions can use Docker Toolbox.

Linux users can install Docker from their package management system.

### Installing PyWaiwera

The easiest way to run Waiwera via Docker is by using the
`waiwera-dkr` script, which is supplied as part of the
[PyWaiwera](https://pypi.org/project/pywaiwera) Python library. You
will need to have [Python](https://www.python.org/) installed on your
machine. Then PyWaiwera can be installed from the Python Package Index
(PyPI) using the `pip` package manager, e.g. `pip install pywaiwera`.

### Running using Docker

The `waiwera-dkr` script handles installing and updating the Waiwera
Docker container image, running Waiwera in the container, and managing
the sharing of files between the container and your simulation
directory. For example:

     waiwera-dkr -np 16 model.json

uses Docker to run the model with JSON input file `model.json` on
Waiwera, using 16 parallel processes.

## Native Linux build

Building a native Waiwera executable on Linux systems can be carried
out using [Ansible](https://www.ansible.com/), which manages checking
and installing any necessary tools (compilers, build tools etc.),
building dependency libraries and building Waiwera itself (which is
done using the [Meson](https://mesonbuild.com/) build system).

This is essentially a three-step process: installing Ansible, cloning
or downloading the Waiwera source code, and building the Waiwera
executable.


