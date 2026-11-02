**English** · [Русский](../ru/features/regex-manager.md)

# Regex Manager

A dedicated workspace for the regular expressions you use while modding. Instead
of keeping patterns in scattered notes, Alter gives you an organized, searchable
library you can carry between devices.

## Why Alter exists

Alter started from a frustration with existing regex tools in the modding space.
Those tools ship a fixed, read-only set of pre-approved patterns and give the
user no way to add their own, so the real problem is never solved: your own
patterns still end up scattered and disorganized. Alter is the answer to that.
Your regexes are yours. You add them, you organize them, and you take them with
you.

## What it does

- **Add your own patterns.** Store as many patterns as you like, each with a
  name and a search/replace pair. There is no approved list and no gatekeeping;
  the library is yours to build.
- **Group into folders.** Organize patterns into named folders by purpose, for
  example `remove ads`, `anti analytics`, `safety`, or `freemium`. Folders show
  up as filter chips at the top of the Regex tab.
- **Search on submit.** Type your query and confirm it to run the search. The
  list is not rebuilt on every keystroke, so scrolling and typing stay smooth on
  large collections.
- **Syntax highlighting.** Groups, classes, quantifiers, escapes and anchors are
  coloured, and invalid constructs are marked.
- **Copy in one tap.** Copy either side of a pattern (search or replace) to the
  clipboard instantly.

## Backup and import

Your whole collection can be exported and restored as a portable archive.

- **Format:** a `.zip` archive containing plain `JSON` files. The archive is left
  readable so other tools can open it.

Inside the archive:

- `folders_meta.json`: the index. A `JSON` array describing every folder in the
  collection, with each folder's `id` and `name`.
- `regex_folder_<id>.json`: one file per folder, named after that folder's `id`.
  A `JSON` array of the folder's patterns.
- `regex_data.json`: patterns that are not in any folder.

### File shapes

`folders_meta.json`:

```json
[
  { "id": "1784926869621_0", "name": "remove ads" },
  { "id": "1784926869624_1", "name": "anti analytics" }
]
```

`regex_folder_<id>.json`:

```json
[
  { "name": "pattern name", "search": "<search value>", "replace": "<replace value>", "filter": "" }
]
```

### How import works

Import **merges** the backup into your current collection; nothing you already
have is deleted. Folders are matched by name (case-insensitive), and a pattern
whose search, replace and filter are identical to an existing one is skipped, so
importing the same archive twice does not create duplicates.

To back up or import, use **Settings → Data management → Export regexes /
Import regexes**.

## Why it's different

Three things set Alter apart, and one principle ties them together: your patterns belong to you.

1. **You can add your own patterns.** Alter is a home for the patterns you
   collect, not a locked list of someone else's approved ones.
2. **Folder organization.** Arrange your collection into named folders rather
   than one flat pile.
3. **Manual backup and import.** Full control over exporting and restoring your
   collection as a portable, shareable archive.
