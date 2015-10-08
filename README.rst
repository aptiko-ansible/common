======
common
======

Overview
========

This is an Ansible role for applying common configuration to all Debian
machines. It installs sudo, ntp, pip and ca-certificates, generates
locales en_US.UTF-8 and en_DK.UTF-8, configures firewall to deny all but
allow port 22 (additional allows can be specified by other roles), and
installs the root ssh keys.

Variables
=========

- ``ssh_pub_key``, ``ssh_priv_key``: Root's ssh keys.

Meta
====

Written by Antonis Christofides

| Copyright (C) 2014-2015 Antonis Christofides
| Copyright (C) 2015 National Technical University of Athens

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.
