% ramalama-daemon 1

## NAME
ramalama\-daemon - run a RamaLama REST server

## SYNOPSIS
**ramalama daemon** [*options*] [start|run]

## DESCRIPTION
Run a RamaLama REST server (daemon) to manage and serve AI models.

## COMMANDS

#### **start**
Prepares to run a new RamaLama REST server so it will be run either inside a RamaLama container or on the host.

#### **run**
Start a new RamaLama REST server.

## OPTIONS


[//]: # (BEGIN included file options/help.md)
#### **--help**, **-h**
Show this help message and exit

[//]: # (END   included file options/help.md)


[//]: # (BEGIN included file options/host.md)
#### **--host**="127.0.0.1"
IP address for the model server to listen on. Defaults to "127.0.0.1", so the
served model is only reachable from the local machine. To expose it on the
network, set this to a wildcard address such as "0.0.0.0" (IPv4) or "::"
(dual-stack).

[//]: # (END   included file options/host.md)

#### **--image**=IMAGE
OCI container image to run with the specified AI model. Defaults to the standard `quay.io/ramalama/ramalama` image. See **[ramalama(1)](ramalama.1.md)** for details on default and GPU-accelerated container images.


[//]: # (BEGIN included file options/port.md)
#### **--port**, **-p**
port for AI Model server to listen on. It must be available. If not specified,
a free port in the 8080-8180 range is selected, starting with 8080.

The default can be overridden in the `ramalama.conf` file.

[//]: # (END   included file options/port.md)


[//]: # (BEGIN included file options/pull.md)
#### **--pull**=*policy*
Pull image policy. The default is **missing**.

- **always**: Always pull the image and throw an error if the pull fails.
- **missing**: Only pull the image when it does not exist in the local containers storage. Throw an error if no image is found and the pull fails.
- **never**: Never pull the image but use the one from the local containers storage. Throw an error when no image is found.
- **newer**: Pull if the image on the registry is newer than the one in the local containers storage. An image is considered to be newer when the digests are different. Comparing the time stamps is prone to errors. Pull errors are suppressed if a local image was found.

[//]: # (END   included file options/pull.md)

## EXAMPLES

Start a RamaLama REST server in a container:
```
$ ramalama daemon start
```

Start a RamaLama REST server listening on port 8080 and accessible on all network interfaces:
```
$ ramalama daemon start --host 0.0.0.0 --port 8080
```

Run a RamaLama REST server directly on the host:
```
$ ramalama daemon run --port 8080
```

## SEE ALSO
**[ramalama(1)](ramalama.1.md)**

## HISTORY
Feb 2025, Originally compiled by Michael Engel <mengel@redhat.com>
