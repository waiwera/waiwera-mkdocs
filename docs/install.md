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

First, Docker itself needs to be installed. The Docker documentation
has instructions on how to install it on
[Windows](https://docs.docker.com/docker-for-windows/install/), [Mac
OS](https://docs.docker.com/docker-for-mac/install/) and various Linux
distributions
(e.g. [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/),
[Debian](https://docs.docker.com/install/linux/docker-ce/debian/)).

The easiest way to run Waiwera is then to use the supplied
`waiwera-dkr.py` Python script, which handles installing and updating
the Waiwera Docker container image, running Waiwera in the container,
and managing the sharing of files between the container and your
simulation directory.

## Native Linux build

Building a native Waiwera executable on Linux systems can be carried
out using [Ansible](https://www.ansible.com/), which manages checking
and installing any necessary tools (compilers, build tools etc.),
building dependency libraries and building Waiwera itself (which is
done using the [Meson](https://mesonbuild.com/) build system).

This is essentially a three-step process: installing Ansible, cloning
or downloading the Waiwera source code, and building the Waiwera
executable.


