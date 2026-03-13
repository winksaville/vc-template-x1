# vc-template-x1

This is the main repo of a dual-repo convention for using
a bot to help in the development of a coding project. The goal
is that this main repo contains the "what", while the partner
bot repo contains "why" and "how". The key to the convention
is each change is cross-referenced to the other. Thus there
is a coherent story of the development of the project across time.

The beginnings of that tool is [vc-x1](https://github.com/winksaville/vc-x1)
which currently does achieve this goal, but is being used as a
first test bed.

## jj Tips for Git Users

If you're coming from git, jj's log output can be surprising compared to
tools like `gitk --all`.

### Why `jj log` shows fewer commits than `gitk`

jj tracks *changes* (identified by change IDs), not individual git commits.
When you rewrite a change (`jj describe`, `jj rebase`, `jj squash`, etc.),
jj creates a new git commit and keeps the old one under `refs/jj/keep/*` as
undo history. `gitk --all` sees all of these obsolete commits; `jj log` only
shows the current version of each change.

### Useful commands

| Command | Description |
|---------|-------------|
| `jj log` | Show recent visible commits (default revset) |
| `jj log -r ::@` | Show **all** ancestors of the working copy |
| `jj log -r 'all()'` | Show all non-hidden commits (needed if you have multiple heads/branches) |
| `jj st | Show the status of the Working and Parent commits |
| `jj st -r <chid> | Status of the commit, <chid> such as `@`, `@-`, `xyz` |
| `jj show | Show the Working commit, -r @ |
| `jj show -r <chid> | Show the commit, <chid> such as `@`, `@-`, `xyz` |
| `jj evolog -r <chid>` | Show the evolution history of a single change |
| `jj op log` | Show operation history (each rewrite operation) |


In a single-branch workflow, `jj log -r ::@` and `jj log -r 'all()'` give
the same result. Use `all()` when you have multiple branches or heads.

## Cross-repo Linking with Git Trailers

Commits in each repo use [git trailers](https://git-scm.com/docs/git-interpret-trailers)
to cross-reference their counterpart in the other repo. The `ochid`
(Other Change ID) trailer contains a workspace-root-relative path
and jj changeID:

```
ochid: /.claude/xvzvruqo   # points to a .claude repo change
ochid: /wtpmottv            # points to an app repo change
```

Paths always start with `/` (the workspace root, i.e. vc-x1).
Each repo has a `.vc-config.toml` that identifies its location
within the workspace, so tools can resolve these paths locally.

For full details see:
- [Git trailer convention](./notes/chores-01.md#git-trailer-convention)
  — [ochid (Other Change ID)](./notes/chores-01.md#ochid-other-change-id)
  — [ChangeID path syntax](./notes/chores-01.md#changeid-path-syntax)
  — [.vc-config.toml](./notes/chores-01.md#vc-configtoml)

## License

Licensed under either of

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall
be dual licensed as above, without any additional terms or conditions.

[1]: https://github.com/karpathy/autoresearch
