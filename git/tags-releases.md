# Tags and releases

```bash
git tag -a v1.2.0 -m "Release 1.2.0"     # annotated tag (has author, date, message)
git tag v1.2.0-rc1                       # lightweight tag (just a pointer)
git push origin v1.2.0                   # tags aren't pushed by default
git push origin --tags                   # push all tags
git tag -d v1.2.0 && git push origin :refs/tags/v1.2.0   # delete locally + remotely
git describe --tags                      # e.g. v1.2.0-5-g4f2a9c1 (5 commits after v1.2.0)
```

**Semantic versioning** `MAJOR.MINOR.PATCH`:
- MAJOR: breaking change
- MINOR: new feature, backwards compatible
- PATCH: bug fix

Use annotated tags for releases; GitHub Releases are built on top of them.
