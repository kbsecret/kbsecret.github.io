---
layout: default
---

# Getting started

Once you have KBSecret [installed](installation), getting started is straightforward.

## Terminology

To get started, you'll need to know three terms as KBSecret uses them: **types**, **records**,
and **sessions**.

A **type** in KBSecret is a collection of fields and operations on those fields. For example,
the `login` type might have two fields (a `username` and `password`), and operations to update
those fields as necessary.

A **record** in KBSecret is an instantiation of a **type**, meaning that its fields are bound to
real values. For example, if `gmail` were a record of type `login`, its `username` might be
bound to `alice` and its `password` might be bound to `hunter2`.

A **session** in KBSecret is a collection of **records**. The session can be heterogeneous,
meaning that multiple types of records can be present in it. Every session is *either* associated
with one or more Keybase users (including you), *or* with a
[Keybase team](https://keybase.io/blog/introducing-keybase-teams).

There are other concepts in KBSecret that you'll discover later (like generators), but these
three are the only ones absolutely required to get started.

## Types

First, let's see what kinds of records we can create:

```bash
$ kbsecret types
```

Example output:

```
todo
login
environment
unstructured
snippet
```

In a clean installation, these are KBSecret's default types.

Users can add their own types by dropping Ruby classes in `~/.config/kbsecret/record/`,
and you should check out the [customization](customization) page for more info on that.

## Records

So, KBSecret knows about `login` records. Let's try to create to create one!

```bash
$ kbsecret new login my-login
```

This will prompt you to input the fields expected by the `login` type, namely a
username and password:

```
Username? Alice
Password? ********
```

Now, let's see what records we have:

```bash
$ kbsecret list
```

Outputs:

```
my-login
```

Try this out with some of the other types above, and see what you get!

## Sessions

But wait, where did the record(s) created above go? We didn't specify a session in either
`kbsecret new` or `kbsecret list`!

When you don't pass an explicit session (more on that in a sec), KBSecret
will assume that you wanted the default session.

We can confirm this by observing that these have the same output:

```bash
$ kbsecret list
$ kbsecret list -s default
```

So, how do we create a new session? With `kbsecret new-session`!

For example, this will create a session between two Keybase users ("alice" and
"bob") named "ultra-secret":

```bash
$ kbsecret session new ultra-secret --root ultra-secret --users alice,bob
$ # more briefly
$ kbsecret session new ultra-secret -r ultra-secret -u alice,bob
```

Note that the session label and `--root`/`-r` option don't need to be the same &mdash;
the label is what identifies the session to other `kbsecret` commands, while the root
is just the directory that the session's storage directory. In this case, it gets expanded
to `/keybase/private/alice,bob/kbsecret/ultra-secret/`.

We can also create a *team-based* session via the `--team` option, which takes the name
of a Keybase team that you already belong to:

```bash
$ kbsecret session new api-keys --team megacorp.devs
```

Team-based sessions infer the session storage directory from label, so we don't need
to pass a separate `--root` option.

Now that we have a new session, we can pass it to (most) other commands via the
`--session`/`-s` option:

```bash
$ kbsecret new -s ultra-secret
$ kbsecret list --session api-keys
```

Note that `--session`/`-s` is a subcommand option, not applied to `kbsecret` itself. In other words,
`kbsecret --session ultra-secret list` won't work!

## Next steps

That covers the basics of KBSecret's main primitives: types, records, and sessions.

These examples demonstrate some of the most common operations, but there are plenty of other
commands and options that you'll find useful. Luckily, they're all documented in the
[manual pages](man/)!

## Afternote

If this guide is outdated, didn't help, or wasn't clear enough, it's a bug. Help us out by filing
a report [here](https://github.com/kbsecret/kbsecret.github.io/issues).
