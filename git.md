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


# git stash
* You can pass a message to `save`

```bash
git stash save "my descriptive message"
git stash list
  # stash@{0}: On master: my descriptive message
  # (END)
```

* To stash files that are not tracked by git yet:

```
git stash save --include-untracked
```

* To stash all unstaged files:

```
git stash save --keep-index
```

* To see the content of a stash

```bash
git stash list --stat
```

```bash
git stash show stash@{1}
  # trunk/backend/ketenmanagement/app/models/concerns/playable.rb | 7 +++++--
  # 1 file changed, 5 insertions(+), 2 deletions(-)
```
and you can even use any flag that you would use with `git log`

```bash
git stash show stash@{1} --patch
  # diff --git a/trunk/backend/ketenmanagement/app/models/concerns/playable.rb b/trunk/backend/ketenmanagement/app/models/concerns/playable.rb
  # index 32a7f10..f693889 100644
  # --- a/trunk/backend/ketenmanagement/app/models/concerns/playable.rb
  # +++ b/trunk/backend/ketenmanagement/app/models/concerns/playable.rb
  # @@ -44,7 +44,7 @@ module Playable
  #        raise TurnAlreadyFinished unless !turn.finished
  #        raise TurnAlreadyFinished unless self.turns.last == turn
  #        turn.expired = true
```

* To create a branch out of a stash:

```bash
git stash branch my-awesome-feature stash@{0}
```

* To empty the stash stack

```bash
git stash clear
```


# My config

```bash
# to use rebase as default
git config --global pull.rebase true

# to automatically reapply your conflict solution if the same confilct is found again
git config --global rerere.enabled true

# more beautiful, readable, and useful output for log
# git config --global alias.lg "log --oneline --decorate --all --graph"
git config --global alias.lg "log --pretty=format:'%Cgreen%h %Cblue%<(15,trunc)%an %Creset%s' --graph --all"
  # %Cgreen      : switch color to green
  # %h           : abbreviated commit hash
  # %Cblue       : switch color to blue
  # %<(15,trunc) : make the next placeholder take 15 columns, padding spaces on the right, and truncating on the right
  # %an          : author name
  # %Creset      : reset color
  # %s           : subject
  # http://git-scm.com/docs/git-log --> search for "pretty formats"

# a shorter form of the status
git config --global alias.s "status -s"

git config --global user.name  "Alejandro Riera"
git config --global user.email "ar@zeit.io"
git config --global alias.st   "status"
git config --global alias.co   "checkout"
git config --global alias.ci   "commit"
git config --global alias.br   "branch"
```
