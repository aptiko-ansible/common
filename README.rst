======
common
======

Overview
========

This is an Ansible role for applying common configuration to all Debian
machines. It installs sudo, ntp, pip and ca-certificates, generates
locales en_US.UTF-8 and en_DK.UTF-8, configures firewall to deny all but
allow port 22 (additional allows can be specified by other roles), 
installs the root ssh keys and authorized keys, configures ssh to allow
root to login without password, and sets some options for root's shell
in ``.profile`` and ``.bashrc``.

Variables
=========

- ``ssh_pub_key``, ``ssh_priv_key``: Optional. Root's ssh keys.
- ``root_authorized_keys``: Optional. A list of strings. Any other keys
  are removed from root's authorized_keys. If unspecified, the root's
  authorized keys are not touched.
- ``command_line_editing_mode``: Optional. Set it to "vi" to enable vi
  editing mode in bash.

Meta
====

Written by Antonis Christofides

| Copyright (C) 2014-2016 Antonis Christofides
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
