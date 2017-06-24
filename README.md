Munin Plugin for Freebox
========================

Overview
--------

This can only be useful to you if you are:

1. Client of French ISP Free and have a Freebox v6.
2. Use Munin for monitoring your server.

If _both_ of these conditions are true, you may find this plugin useful to
add the display of Freebox data to your Munin graphs, please read on.


Installation
------------

This plugin relies on php5-cli and php5-curl.

You need to run the authconf, before using this plugin, in order to obtain the
authorization token needed to connect to the Freebox:

	$ munin-run freeboxv6_ authconf

Keep this token secret as it is sufficient to connect to the Freebox (i.e. no
password is required)!


Configuration
-------------

Add the following section to `/etc/munin/plugin-conf.d/munin-node` file:

	[freeboxv6_*]
	env.app_token token-obtained-above

Add a symbolic link from `/etc/munin/plugins/freebox_temp` to wherever you put
the file `freeboxv6_` itself, e.g. `/usr/local/share/munin/plugins`.

As with any Munin plugin, check that it works manually:

	$ munin-run --debug freebox_temp

If everything looks correctly, restart munin to start using it:

	$ service munin-node restart


Copyright and Licence
---------------------

This plugin is distributed under the terms of GPLv2.

Authors
-------

Damien Broqua <dbroqua@mousur.org>
