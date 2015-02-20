# Remove local (untracked) files from my current Git branch?

```
git clean -f
```

But beware... there's no going back. Use `-n` or `--dry-run` to preview the damage you'll do.

If you want to also remove directories, run `git clean -f -d` or `git clean -fd`

If you just want to remove ignored files, run `git clean -f -X` or `git clean -fX`

If you want to remove ignored as well as non-ignored files, run `git clean -f -x` or `git clean -fx`

Note the case difference on the X for the two latter commands.

If `clean.requireForce` is set to "true" (the default) in your configuration, then unless you specify `-f` nothing will actually happen, with a recent enough version of git.

Note that as of git-1.6.0, the dashed style of writing git commands (ie, `git-clean` instead of `git clean`) is obsoleted.

See the [git-clean](http://git-scm.com/docs/git-clean) docs for more information.
