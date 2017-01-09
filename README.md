# Cardano SL Documentation

[//]: # (@any)

This repository contains the documentation for Cardano SL.

## Requirements

In order to build the documentation you must have installed `mkdocs`

To install, visit: http://www.mkdocs.org/#installation

## Visualizing the Documentation

To visualize the documentation you can run `mkdocs serve` on the root folder
and visit [http://localhost:8000](http://localhost:8000)

To build the documentation run `mkdocs build`

## On-line Live Version of the Documentation

If you want to run an on-line live version of the documentation, use the
following command:

```
mkdocs serve --dev-addr=0.0.0.0:8080
```

Jonn's live version of documentation is hosted
[here](http://207.154.207.51:8080).

# Documenting IOHK Projects Using Readthedocs

[//]: # (@any)

## Abstract

In this document we talk about documenting IOHK projects such as CSL
using `mkdocs`, a tool compatible with Readthedocs platform. Here we
address issues of documentation upkeep as well as per-release
documentation generation.

## Introduction

The matter of documentation upkeep, especially targeting end-users is one
of the most challenging tasks in software maintenance. Here we propose a
method of making this upkeep as painless as possible, making sure that
documentation (targeting end-users or fellow developers) is up to date.
Note that the guidelines in this document should be used for
documentation even despite the fact that reporting tool, that is
mentioned in this document, isn't implemented yet.
[//]: # (TODO: Update this section when reporting tool is implemented)

## Readthedocs/GitHub-compatible Commentaries in Markdown

First of all, it's important to note that even though Markdown is used
to document IOHK projects, one can insert one-line commentaries using
the following label hack:

```
[//]: # (Commentary goes here)
```

Those commentaries are internal and won't be displayed at all in the
rendered documentation (see
[current
version](http://pos-haskell-prototype.readthedocs.io/en/latest/) of
Cardano SL documentation for a reference. In the documentation index,
you can't see the commentaries for developers that refer to this file,
while in the Markdown source text they
[exist](https://raw.githubusercontent.com/manpages/pos-haskell-prototype/master/docs/index.md).
[//]: # (TODO: Replace URLs here with IOHK repo)

## Style Guide

For Markdown styling, use `#`-headers, instead of "underlined"
headers:

```
## This is Good
```

```
This is Bad
---
```

When writing a section title, or any other title, capitalize every noun,
pronoun, and verb:

```
# An Example of Proper Capitalization
```

```
# An example of improper capitalization
```

## Semantic Commentaries

After each section, but at least at the top-level (`#`) sections, a
Markdown comment should be inserted about last version of software for
which a certain piece of documentation was verified to be actual. Valid
values are:

 + `[//]: # (@any)` documentation is future-compatible, and valid for
    any software revision.
 + `[//]: # (@feature-branch)` documentation is actual on
    `feature-branch` branch. Should only be used with feature branches.
    When such branch (perhaps, along with documentation) will get merged
    into `master` or `develop`, documentation will become unverified and
    maintenance is required to update such documentation.
 + `[//]: # (v1.0.0)` documentation is actual for the release `1.0.0`
   and is considered to be verified until new software version is
   released.
 + `[//]: # (#6e663b8eabc5acfe970892a607e48f85443931bd)` documentation
   is actual for commit `6e663b8eabc5acfe970892a607e48f85443931bd` and
   will be considered unverified when a new version is pushed.

Most sections should be labeled with `@` or `v` comments.

In any section, if an issue is mentioned in Markdown commentaries, an
automation will be put in place in that will report changes of the
status of the relevant action and request maintenance. Use standard
syntax to mention an issue in a commentary:

```
[//]: # (To be implemented in [CSL-228])
```

## Pushing Incomplete Documentation

The standard notation for a piece of incomplete documentation is visible
emphasised string "Pending" (`_Pending_`, in Markdown). It is obligatory
to add commentary with a reason why a particular piece of documentation
hasn't been written yet and if there are any blockers, a commentary
about the blocker should be inserted. Example:

```
## Subject

_Pending_
[//]: # (Reason: This feature hasn't been finalized yet, @gromak to provide details.)
[//]: # (Blocked by [CSL-228].)
```

## Subject to Change Marker

If a certain feature is subject to change, a commentary `[//]: # (STC)`
or `[//]: # (STC [CSL-228])` must be added. In first case whenever an
issue is closed, a branch is merged or a new version is released, STC
sections will become unverified and a maintenance shall be required.

## Sprint-related Changes

As a part of sprint planning, markers should be inserted in the
documentation that shall mark sections as unverified after a particular
date. Syntax for sprint-related changes is the following:
`[//]: # <2017-01-29>`.

## Feedback Request Marker

_Pending_
[//]: # (Specification of Feedback Request Marker semantics to be developed)

## Documentation Report Scripts

_Pending_
[//]: # (There's not enough time to automate doc report generation now)
