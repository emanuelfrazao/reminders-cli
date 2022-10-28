---
project: reminders-cli
description: a simple bash cli (following REST) for saving notes with hierarchical tags, seeing and deleting them
version: ideation
---

<h1>reminders-cli</h1>

- [UI](#ui)
  - [subcommands](#subcommands)
  - [usage](#usage)

# UI

Say the cli is accessed through a single command named `rem`.

## subcommands
It has subcommands:
* `ember`: save notes (with optional tag)
* `ind`: get notes (either general, or on optional tag)
* `del`: delete notes (on given tag, either a single one by number/id, or all of them)

## usage
The subcommands arguments are:
* `rem ember [-<tag>[.<sub-tag>...]] (<note> | -m)`:
  * `-<tag>[.<sub-tag>...]`     ,   for specifying on which tag to save `<note>`. if not specified, save under "general"
  * `-m`                        ,   for writing a multi-line note
* `rem ind ([-<tag>[.<sub-tag>...] [<id>]]|--all)`
  * `-<tag>[.<sub-tag>...]`,   for retrieving all notes saved on given tag. if not specified (and neither is `--all`), show "general". either way, specify `<id>` for getting the single note corresponding to it
  * `--all`, for showing all notes saved (on all tags)
* `rem del ([-<tag>[.<sub-tag>...] [<id>]]|--all) [-f]`
  * `-<tag>[.<sub-tag>...]`,   for removing all notes saved on given tag. if not specified (and neither is `--all`), remove the ones in "general". either way, specify `<id>` for deleting the single note corresponding to it. user is prompted for confirmation.
  * `--all`, for removing all notes saved (on all tags)
  * `-f`, for forcing removal without confirmation


When the user asks to delete a note, it is prompted for confirmation, unless the flag `-f` is used.

Notes should be printed to stdout with their tag (and subtags) and corresponding id.

