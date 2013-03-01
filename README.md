plz
===

Simple, hackable, modular deployment system.

Overview
--------

plz is an experiment in automated deployment. It'll deploy Node.JS applications,
install their dependencies, link in some locally-specific config if it exists
and start them in the background with [forever](https://github.com/nodejitsu/forever/).
It can also destroy (deploy in reverse) applications, or restart deployed
applications.

Installation
------------

Right now you just kind of dump everything somewhere in your path. I'll flesh
this out if/when it's required.

You should also put `plz.rc.example` at `~/.plz.rc`. Modify it as you see fit.

Usage
-----

plz has several commands available, all accessed via `plz <command> [arguments]`.

`deploy <application_name> <application_revision>` deploys a specific revision
(or branch, or tag) to the application directory and starts it with `start`.

`destroy <application_name> <application_revision>` will `stop` and remove a
specific revision of an application if it exists.

`update <application_name> <application_revision>` will do `destroy` followed
by `deploy`.

`start <application_name> <application_revision>` will start an application
using `forever start`. It reads a `plz_start` file from the root of the
application if it exists. The uid of any forever processes it creates will be
set to `<application_name>.<application_revision>.<task_name>`.

`stop <application_name> <application_revision>` will stop an application using
`forever stop`. It also reads from the `plz_start` file if it exists.

`restart <application_name> <application_revision>` will do `stop` followed by
`start`.

`link-node`, `link-config`, `npm-install` and `git-export` are used internally
by `deploy` and as such probably shouldn't be used directly.

License
-------

3-clause BSD. A copy is included with the source.

Contact
-------

* GitHub ([deoxxa](http://github.com/deoxxa))
* Twitter ([@deoxxa](http://twitter.com/deoxxa))
* ADN ([@deoxxa](https://alpha.app.net/deoxxa))
* Email ([deoxxa@fknsrs.biz](mailto:deoxxa@fknsrs.biz))
