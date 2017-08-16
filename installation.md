---
layout: default
---

# Installing KBSecret

## External dependencies

KBSecret uses Keybase and KBFS, so you'll need to have a [Keybase account](https://keybase.io/)
and have the client installed.

You can find installation instructions for your system [here](https://keybase.io/download).

## Installation

KBSecret is available as a Ruby gem, and can be installed via `gem`:

```bash
$ gem install kbsecret
```

Or, if you'd like to try the latest prerelease:

```bash
$ gem install --pre kbsecret
```

## System packages?

KBSecret has *very* experimental packages available for Debian (deb), Fedora (rpm),
and Arch (PKGBUILD). See the [README](https://github.com/kbsecret/kbsecret/blob/master/README.md)
for more information.

Please help us by contributing (real) native packages for your system/distribution!

# Testing your installation

Once you've installed KBSecret, you can test it by running:

```bash
$ kbsecret version
```

If you see something like `kbsecret version 0.8.2.`, you're good to go!

Now, check out the [quick start](quickstart) guide...
