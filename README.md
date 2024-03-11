ncs-raftsim
===========

This repository hosts the `ncs-raftsim` script, used for setting up a local
Cisco NSO HA Raft cluster.

The script makes it easy to stand up a new cluster that you can use for
testing and development. All nodes run locally, using different network
ports. This is of little value for production but is super fast (takes
about 3 seconds to get a working cluster on author's modest machine).


Usage
-----

Before running the script, ensure you have a working local install of NSO
and you have sourced the `ncsrc` file (which sets the NCS_DIR). You can
likely use a system install as well but you need to make sure `ncs-setup`
is available, which is not the case by default.

Create, start, and join the cluster:

    ncs-raftsim up

Start the CLI on the current leader:

    ncs-raftsim cli

You can also start the CLI on a specific node and add arguments:

    ncs-raftsim cli 2 -C -u admin

If you wish to change the default CLI style, set the NCS_RAFTSIM_JCLI to
some non-zero value.

Create a cluster with some initial packages by creating and populating the
`raftsim/packages/` folder beforehand.

Start and stop individual nodes:

    ncs-raftsim stop 3
    ncs-raftsim start 2 3

To start from scratch, you can reset all nodes and stand up the cluster
with a single command, while also starting the CLI:

    ncs-raftsim reup cli

Once done, stop the nodes:

    ncs-raftsim stop

Or, alternatively, stop the cluster and delete all the files:

    ncs-raftsim purge


License
-------

Licensed under the Apache License 2.0, see LICENSE.
