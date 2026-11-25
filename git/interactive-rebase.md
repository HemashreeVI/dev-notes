# Cleaning up commits with interactive rebase

Squash "wip" commits into meaningful ones before opening a PR.

```bash
git rebase -i HEAD~4
```

The editor shows the last 4 commits, oldest first:

```text
pick 1a2b3c4 Add login endpoint
squash 5d6e7f8 wip
squash 9a8b7c6 fix typo
reword 3c4d5e6 Add tests
```

| Keyword | Effect |
|---|---|
| `pick` | keep as is |
| `reword` | keep, edit message |
| `squash` | merge into previous, combine messages |
| `fixup` | merge into previous, drop this message |
| `drop` | delete the commit |

**Shortcut:** `git commit --fixup <hash>` then `git rebase -i --autosquash <base>` lines everything up for you.
