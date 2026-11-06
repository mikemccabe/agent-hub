---
name: md
description: Create a dated working document in mds/. Use when the user says "make an md" or runs /md.
---

Check for prior mds on the topic first, then create
`mds/YYYY-MM-DD-<name>.md` -- both per docs/dated-markdown.md
("Check for priors first"; filename, `summary:` frontmatter,
companion directory). Then commit it
in the same step, by pathspec, with the changes it documents:
`git add <new files> && git commit -m ... -- <paths>`.

$ARGUMENTS
