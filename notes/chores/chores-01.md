# Chores-01

Chores-XX files use [Prose form](../../AGENTS.md#prose-form). They
contain discussions and notes on various chores in github compatible
markdown. There is also a [todo.md](../todo.md) file that tracks
tasks and in general there should be a chore section for each task
with the why and how this task will be completed.

## docs: shared protocol set; template cleanup

Commits:

Two threads land together. First, the notes-sync round with
vc-x1: the shared protocol set — `AGENTS.md`,
`notes/cycle-protocol.md`, `notes/versioning.md`,
`notes/jj-tips.md` — is now byte-identical across the sibling
projects (iiac-perf receives the files after this round).
Second, template cleanup: strip template-inherited scaffolding
so a cloned repo starts clean, and land the Rust unwrap policy.

- Repo terminology standardized: **work repo** / **bot repo**,
  written as two words, hyphenated only when the pair sits
  directly in front of another noun. Defined once in AGENTS.md
  Project Structure; all variants (app repo, session repo,
  code-side, `.claude` repo) swept from the living docs.
- vc-x1 0.69.0 corrections folded in from the sync round:
  `squash-push` replaces the detached `finalize` flow, push
  preflight is repo-state-only (the medium's validation is the
  per-commit flow's job), and the hard stop follows the user's
  directive rather than every push.
- Sections adopted from siblings: "Plain synopsis after
  technical explanations" (from iiac-perf); the lean-not-ban
  `unwrap*`/`expect` policy with project-wide clippy lints,
  seeded for new Rust projects via `CargoRust.toml`.
- `notes/substep-test.sh` removed — the jj squash-ladder
  scratch harness that validated the sub-cycle squash recipes.
  Recover it from its introducing commit [[1]]:
  `git show bd2902617c2f:notes/substep-test.sh`.

# References

[1]: https://github.com/winksaville/vc-template-x1/commit/bd2902617c2f "bd2902617c2fc96b43ad08799b198e17567ce601"
