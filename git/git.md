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
can be seen in commit 1b4c7e3 (Add the info on squashing commits, 2024-10-16).
