# postgres-client
=================

This role is the counterpart to postgres-server.  It copies over a key which
has the cname "postgres-client", which postgres-server trusts.

There is a script installed: pg-auth.  This can be sourced from a bash script,
and the environment will be set up such that a plain 'psql -h SOMEHOST' will
connect.
