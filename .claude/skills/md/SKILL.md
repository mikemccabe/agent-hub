---
name: md
description: Create a dated working document in mds/. Use when the user says "make an md" or runs /md.
---

Create a dated working document, following docs/dated-markdown.md:

1. Check for prior mds on the topic ("Check for priors first"). If one
   already is this deliverable, revise its summary or supersede it
   instead of creating a new file.
2. Write `mds/YYYY-MM-DD-<name>.md`, dated today, with a `summary:`
   frontmatter block. Files that go with it go in its companion
   directory, `mds/YYYY-MM-DD-<name>/`.
3. Commit it in the same step, by pathspec, together with the changes it
   documents: `git add <new files> && git commit -m ... -- <paths>`.

$ARGUMENTS
