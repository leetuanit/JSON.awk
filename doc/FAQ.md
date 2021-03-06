<a name="0"></a>
# Frequently Asked Questions

**Usage**

* [Usage: how to run JSON.awk?](#1)
* [Do I need to care about the she-bang?](#2)
* [How to parse multiple JSON data files as a single unit?](#4)

**Embedding**

* [How to embed JSON.awk in a larger awk program?](#5)

**Mawk**

* [Is mawk supported (Debian/Ubuntu)?](#3)
* [How to fix error: mawk: JSON.awk: line NNN: function cb\_jpaths never defined?](#6)

[top](#0)

<a name="1"></a>
## 1. Usage: how do I run JSON.awk?

TL;DR

```sh
awk  -f JSON.awk 1.json [2.json ...]
gawk -f JSON.awk 1.json [2.json ...]
mawk -f callbacks.awk -f JSON.awk 1.json [2.json ...]

echo -e "1.json\n2.json" | awk -f JSON.awk

cat 1.json | awk -f JSON.awk "-" [2.json ...]

awk -v BRIEF=0 -f JSON.awk 1.json
```

Read [the docs](usage.md)

[top](#0)

<a name="2"></a>
## 2. Do I need to care about the she-bang?

The she-bang is the first line of file JSON.awk and reads

```sh
#!/usr/bin/awk -f
```

but could also be changed to

```sh
#!/bin/awk -f
```

or one of several other forms supported by your operating system.

The default value was chosen for performance reasons.  Both binaries could be
installed on your system.  Many Linux distributions link `/bin/awk` to
`/bin/busybox`, and `/usr/bin/awk` to either `/usr/bin/gawk` or
`/usr/bin/mawk`.  Busybox awk is under-powered and takes much longer to run
JSON.awk than gawk and mawk do on identical data.

[top](#0)

<a name="3"></a>
## 3. Is mawk supported (Debian/Ubuntu)?

Yes. JSON.awk is reported to work with mawk 1.3.4 20150503 and 20161120.
Version 1.3.3 is [known not to work](http://github.com/step-/JSON.awk/issues/6).
Please upgrade mawk to a supported version.

[top](#0)

<a name="4"></a>
## 4. How to parse multiple JSON data files as a single unit?

By default, JSON.awk parses each input file separately from all other input
files.  Therefore, for each input file it resets its internal data structures,
and restarts from zero all ouput array indices.  If your application needs to
parse all data files as a single JSON object, you have two options:
* Pipe all data as a single JSON object as illustrated by the last notation
  shown at the end of [QA 1](#1) section *Piping Data*.
* Modify function `reset()` in file JSON.awk. 

[top](#0)

<a name="5"></a>
## 5. How to embed JSON.awk in another awk program?

TL;DR

```sh
awk -v STREAM=0 -f my-callbacks.awk -f JSON.awk 1.json
```

Read [the docs](embed.md)

[top](#0)

<a name="6"></a>
## 6. How to fix error: mawk: JSON.awk: line NNN: function apply never defined?

Nothing's wrong with mawk nor JSON.awk.  This error message is just an
unfortunate consequence of mawk's parser design. Run

```sh
mawk -f callbacks.awk -f JSON.awk 1.json
```

to shut off the error message. Read note #2 of [the docs](embed.md) to know why
this works.

[top](#0)

