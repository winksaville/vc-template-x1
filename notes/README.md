# Notes

This directory contains various notes and documentation related to the project.
Each file is organized by topic for easy reference.

By default there are chores-*.md and todo.md. Chores are general notes
about tasks and todo.md contains short term tasks and their status.

In the future we I expect we may want to create a "notes"
database to better manage the information, TBD.

Examples chore file:
```
# Chores-01.md

General maintenance tasks and considerations for the project see other files for
more specific topics. A chore in a chores file provides quick information on the
how and why of a particular chore. The section header is short and sweet
and the title is appended with the version number of the app when the chore
is completed.

## Create an app that does something interesting (0.1.0)

The app counts from 1 to 100, not to interesting.
```

## jj tips

For users new to jj see [jj-tips.md](jj-tips.md).

```
## Chores format

Filename: "chores-XX.md"
example: chores-01.md

Format of section labels: "## <short description> (X.Y.Z)"
example: "## Topic format description (0.1.0)"

Example chore file:
```
# Chores-01.md
 
General maintenance tasks and considerations for the project see other files for
more specific topics. A chore in a chores file provides quick information on the
how and why of a particular chore.

## Do something (1.3.1)

Describe something
```

## Workflow and conventions

Bot-facing workflow, versioning, and code conventions live in
[`../CLAUDE.md`](../CLAUDE.md). Start there for:

- **Versioning during development** — single-step vs multi-step,
  `-N` pre-release suffixes, done-marker discipline.
- **Code Conventions** — doc comments on every file / fn / method,
  `// OK: …` justifications on `unwrap*` calls, ask-on-ambiguity,
  stuck detection.
- **Commit-Push-Finalize Flow** — two-checkpoint per-step
  discipline with hard stop after finalize.

## Todo format

Todo.md contains two main sections "Todo" and "Done" each item is a
short explanations of a tasks and links to more details using 1 or more
references.

Multiple references must be separated: `[2],[3]` not `[2,3]` or `[2][3]`.
In markdown, `[2,3]` is a single ref key (won't resolve) and `[2][3]`
is parsed as display text `2` with ref key `3` (so `[2]` won't resolve).

Examples:

# Todo

- Add new feature X [details](chores-01.md#feature-x)
- Fix bug Y [1]

# Done

- Fixed issue Z [2],[3]

[1]: chores-01bugs.md#bug-y
