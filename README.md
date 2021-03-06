JSON.awk
========

A practical JSON parser written in awk.

Introduction
------------

JSON.awk is a self-contained, single-file program with no external dependencies.
It is similar to [JSON.sh](https://github.com/dominictarr/JSON.sh), a JSON
parser written in Bash -- retrieved on 2013-03-13 to form the basis for
JSON.awk. Since then, the two projects have taken separate paths, so you
will not find all of JSON.sh features in JSON.awk, and viceversa.

Features
--------

* Single file without external dependencies
* JSON.sh compatible output format (as of 2013-03-13)
* Can parse one or multiple input files within a single invocation
* Can be embedded in other awk programs
* Invalid JSON input is captured and can be processed on exit
* Written for POSIX awk; does not require GNU gawk extensions;
  works with mawk 1.3.4 20150503 and higher
* Choice of MIT or Apache 2 license 

Supported Platforms
-------------------

All OS platforms where a POSIX awk implementation is available. Special cases:

* FreeBSD [&raquo;10](https://github.com/step-/JSON.awk/issues/10)

Setup
-----

Drop file JSON.awk in your project folder and follow the examples.

Usage Examples
--------------

For full instructions please [read the docs](doc/usage.md).
If you use mawk please read [FAQ 6](FAQ.md#6).

Passing file names as command arguments:

```sh
awk -f JSON.awk file1.json [file2.json...]

awk -f JSON.awk - < file.json

cat file.json | awk -f JSON.awk -
```

Passing file names on stdin:

```sh
echo -e "file1.json\nfile2.json" | awk -f JSON.awk
```

Embedded in another awk program ([FAQ 5](FAQ.md#5)):

```
awk -f your-callbacks.awk -f JSON.awk file.json
```

Projects known to use JSON.awk
------------------------------

* [KindleLauncher](https://bitbucket.org/ixtab/kindlelauncher/overview)
  a.k.a. KUAL, an application launcher for the Kindle e-ink models, uses
  JSON.awk to parse menu descriptions.

License
-------

This software is available under the following licenses:

* MIT
* Apache 2

Credits
=======

Without [JSON.sh](https://github.com/dominictarr/JSON.sh) this software
would not exist.
