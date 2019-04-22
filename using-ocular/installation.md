# Installing ShiftLeft Ocular

Before installing ShiftLeft Ocular, make sure you have [met all requirements](../introduction/requirements).

Begin by decompressing the provided ZIP file `ocular-distribution.zip`. This creates the directory `ocular-distribution`.

```bash
unzip ocular-distribution.zip
cd ocular-distribution
```

Run the installer and follow the prompts:

```bash
bash ./install.sh
```

The install script:

* asks you where you want to install ShiftLeft Ocular (defaults to `~/bin/ocular`).
* checks if there is an existing installation, and if so, offers to delete it.
* unpacks the ShiftLeft dynamic policy to `~/.shiftleft/policy/dynamic`, and if it already exists, offers to delete it.
* unpacks the ShiftLeft static policy to `~/.shiftleft/policy/static`, and if it already exists, offers to delete it.

**Note**: Do not make any changes outside the installation and policy directories.

# Additional Configuration for Large Projects

Code analysis can require lots of memory, and unfortunately, the Java virtual machine does not automatially allocate the necessary amount of memory. Though tuning Java memory usage is a discipline in its own right, you can specify the maximum available amount of heap memory using the Java virtual machine's `-Xmx` flag. The easiest way to so is by setting the environment variable `_JAVA_OPTS` as:

```bash
export _JAVA_OPTS="-Xmx$NG"
```
where `$N` is the amount of memory in gigabytes. You can add this line to your shell startup script, e.g., `~/.bashrc` or `~/.zshrc`.
