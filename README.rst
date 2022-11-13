======
common
======

Overview
========

This is an Ansible role for applying common configuration to all Debian
machines. It installs sudo, ntp, pip and ca-certificates, generates
locales en_US.UTF-8 and en_DK.UTF-8, configures firewall to deny all but
allow port 22 (additional rules can be specified by other roles; see
below), installs the root ssh keys and authorized keys, configures ssh
to allow root to login without password, and sets some options for
root's shell in ``.profile`` and ``.bashrc``.

Variables
=========

- ``ssh_pub_key``, ``ssh_priv_key``: Optional. Root's ssh keys.
- ``root_authorized_keys``: Optional. A list of strings. Any other keys
  are removed from root's authorized_keys. If unspecified, the root's
  authorized keys are not touched.
- ``command_line_editing_mode``: Optional. Set it to "vi" to enable vi
  editing mode in bash.

Firewall
========

The role installs ferm. If, in another role or play, you need to add a
firewall rule, add a line to ``/etc/ferm/ansible-late``, like this::

    - name: Allow http and https through firewall
      lineinfile:
        path: /etc/ferm/ansible-late
        line: "proto tcp dport (http https) ACCEPT;"
      notify: Reload ferm

You also need to create a "Reload ferm" handler::

    - name: Reload ferm
      service: name=ferm state=reloaded

The file ``/etc/ferm/ansible-late`` is appropriate for such additional
ACCEPT rules. If you want a rule to be applied early, use
``/etc/ferm/ansible-early`` instead. This is useful for DROP rules.
Example::

    - name: Cut misbehaving machine at the firewall
      lineinfile:
        path: /etc/ferm/ansible-early
        line: "saddr (18.19.20.21 2a01:4f8:2a01:4f8::/32) DROP;"
      notify: Reload ferm

OBVIOUS WARNING: Make an error and you're locked out!

Meta
====

Written by Antonis Christofides

| Copyright (C) 2022 IRMASYS
| Copyright (C) 2015-2019 National Technical University of Athens
| Copyright (C) 2014-2016 Antonis Christofides

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
