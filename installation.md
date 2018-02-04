---
layout: default
---

# Installing KBSecret

## External dependencies

KBSecret uses Keybase and KBFS, so you'll need to have a [Keybase account](https://keybase.io/)
and have the client installed.

You can find installation instructions for your system [here](https://keybase.io/download).

## Installation

Currently, KBSecret can be installed either as a Ruby Gem or as a [Homebrew](https://brew.sh)
package.

Via `gem`:

```bash
$ gem install kbsecret
$ gem install --pre kbsecret # if you want a prerelease
```

Via `brew`:

```bash
$ brew tap kbsecret/kbsecret
$ brew install kbsecret
```

## What about `<package-manager>`?

Currently, KBSecret has no official system packages besides Homebrew.

Please help us by contributing native packages for your system/distribution!

# Testing your installation

Once you've installed KBSecret, you can test it by running:

```bash
$ kbsecret version
```

If you see something like `kbsecret version 0.9.7.`, you're good to go!

Everything working? Check out the [quick start](quickstart) guide.

Something broken? [Tell us about it](github.com/kbsecret/kbsecret/issues).
