Overview
========

The Nextlinux CLI provides a command line interface on top of the `Nextlinux Engine <https://github.com/nextlinux/nextlinux-engine>`_ REST API.

Using the Nextlinux CLI users can manage and inspect images, policies, subscriptions and registries for the following:

**Supported Operating Systems**

* Alpine
* Amazon Linux 2
* CentOS
* Debian
* Google Distroless
* Oracle Linux
* Red Hat Enterprise Linux
* Red Hat Universal Base Image (UBI)
* Ubuntu


**Supported Packages**

* GEM
* Java Archive (jar, war, ear)
* NPM
* Python (PIP)


Installing Nextlinux CLI from source
==================================

The Nextlinux CLI can be installed from source using the Python pip utility

.. code::

    git clone https://github.com/nextlinux/nextlinux-cli
    cd nextlinux-cli
    pip install --user --upgrade .

Or can be installed from the installed form source from the Python `PyPI <https://pypi.python.org/pypi>`_ package repository.

Installing Nextlinux CLI on CentOS and Red Hat Enterprise Linux
=============================================================

.. code::

    yum install epel-release
    yum install python-pip
    pip install nextlinuxcli

Installing Nextlinux CLI on Debian and Ubuntu
===========================================

.. code::

    apt-get update
    apt-get install python-pip
    pip install nextlinuxcli
    Note make sure ~/.local/bin is part of your PATH or just export it directly: export PATH="$HOME/.local/bin/:$PATH"

Installing Nextlinux CLI on Mac OS / OS X
===========================================

Use Python's `pip` package manager:

.. code::

    sudo easy_install pip
    pip install --user nextlinuxcli
    export PATH=${PATH}:${HOME}/Library/Python/2.7/bin

To ensure `nextlinux-cli` is readily available in subsequent terminal sessions, remember to add that last line to your shell profile (`.bash_profile` or equivalent).

To update `nextlinux-cli` later:

.. code::

    pip install --user --upgrade nextlinuxcli


Configuring the Nextlinux CLI
===========================

By default the Nextlinux CLI will try to connect to the Nextlinux Engine at ``http://localhost/v1`` with no authentication.
The username, password and URL for the server can be passed to the Nextlinux CLI as command line arguments.

.. code::

    --u   TEXT   Username     eg. admin
    --p   TEXT   Password     eg. foobar
    --url TEXT   Service URL  eg. http://localhost:8228/v1

Rather than passing these parameters for every call to the cli they can be stores as environment variables.

.. code::

    NEXTLINUX_CLI_URL=http://myserver.example.com:8228/v1
    NEXTLINUX_CLI_USER=admin
    NEXTLINUX_CLI_PASS=foobar

Command line examples
=====================

Add an image to the Nextlinux Engine

.. code::

    nextlinux-cli image add docker.io/library/debian:latest

Wait for an image to transition to ``analyzed``

.. code::

    nextlinux-cli image wait docker.io/library/debian:latest

List images analyzed by the Nextlinux Engine

.. code::

    nextlinux-cli image list

Get summary information for a specified image

.. code::

    nextlinux-cli image get docker.io/library/debian:latest

Perform a vulnerability scan on an image

.. code::

   nextlinux-cli image vuln docker.io/library/debian:latest os

Perform a policy evaluation on an image

.. code::

   nextlinux-cli evaluate check docker.io/library/debian:latest --detail

List operating system packages present in an image

.. code::

    nextlinux-cli image content docker.io/library/debian:latest os

Subscribe to receive webhook notifications when new CVEs are added to an update

.. code::

    nextlinux-cli subscription activate vuln_update docker.io/library/debian:latest

More Information
================

For further details on use of the Nextlinux CLI with the Nextlinux Engine please refer to `Nextlinux Engine <https://github.com/nextlinux/nextlinux-engine>`_
