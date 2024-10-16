# Working with `git` - a version control system

## Squashing commits
To squash the latest N commits together, N a positive integer, run:
```
$ git rebase -i HEAD~N
```

In `git-rebase-todo` file, leave the `pick` command next to the commit
you would like for the other commits to be squashed into, and change
the rest of the commit commands to `fixup` if you want to drop the
commit messages for the other commits (only the message of the commit
that you're squashing into will be visible in the output of the
`git log` command).

However, if you would like to keep all the squashed commits' messages,
place the `squash` command next to all of the said commits. The result
can be seen in commit `1b4c7e3` (Add the info on squashing commits,
2024-10-16).

## How to `stash` and then get the stuff back
Sometimes `git` can be very whimsical when it comes to obeying ones'
commands, and requires of the user to save the introduced changes
before continuing. `git stash` is all it takes, but what next?

Execute `git stash list` to see all the stashes available, and pick
the one you want to apply: `git stash apply stash@{n}`, where `n` is
the number of the stash to be applied.

Not sure what have you `stash`ed? `git stash show -p stash@{n}`, where
`n` is the stash' number from the `git stash list`, produces a diff
listing with all the changes kept in the said stash.

## Removing `stash`es
Unused or no longer needed changes can be dropped: `git stash drop stash@{n}`.
__NOTE:__ Dropped stashes are removed from the list, and the ones that
are left raise towards top of the list, their numbers being changed
accordingly, e.g.:
```
$ git stash list
stash@{0}
stash@{1}
stash@{2}
$ git stash drop stash@{1}
$ git stash list
stash@{0}
stash@{1}
```
After the drop, the old `stash@{2}` becomes the new `stash@{1}`, so
beware!
