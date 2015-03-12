# docker-client

## Introduction

Implementation of the docker [client API][1] in Tcl. At present, this
covers only a subset of the API.  You will be able to introspect your
components, control them and attach to them.  There is no support for
images or execution contexts, nor to start components.

  [1]: https://docs.docker.com/reference/api/docker_remote_api/

## Quick Tutorial

The library provides an object-based API: you will get a token for a
connection to the docker daemon, and this token is also a command with
which you will perform most of all other calls, Tk-style!

### Connect

To get a token, call a command similar to the following.  Note that
when specifying a UNIX socket, the library will pipe back and forth
all commands through the `nc` executable.  This is because Tcl has no
native support for UNIX sockets.

    set docker [docker connect unix:///var/run/docker.sock]

### Other Commands

This is undocumented for now, but follows more or less the original
API.  For example, to ping the server, call the following, which
should return the string `OK`.

    $docker ping


