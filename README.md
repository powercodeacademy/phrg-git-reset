# Git Log & Git Reset

`git` is a powerful and complex CLI that manages versions of your code. This lesson explores using the `git log` and `git reset`, commands that help us manipulate our local commits.

## The Manual

It is helpful to utilize [`git` documentation](https://git-scm.com/doc) often as you grow as a developer. Sometimes it is even easier to launch `git` documentation in your shell session. Let's do this right now for `git log` and `git reset`, using the `--help` option. You can pass the `--help` option to any `git` command for more information.

```
git log --help
```

```
git reset --help
```

Take a few minutes to read about ways to use these commands.

---

# Git Log

The `git log` command helps us track what commits we have locally. While Github presents a great interface to review commits that have been `push`ed, Github does not (and cannot) know what is stored locally on our own machines. This makes `git log` an indispensable tool, as we often need to review and/or change our commits before we send them up to Github.

`git log` presents very informative output. Here is the output for a new project we just started. (NOTE: `git log` output [is formattable](https://git-scm.com/docs/git-log#_pretty_formats). This lesson uses the default git log format, which is medium.)

```
commit 39ff2a73e31c7f2016d6374538c4c987e8e24e71 (HEAD -> example_branch)
Author: Garett Arrowood <garettarrowood@gmail.com>
Date:   Thu Sep 6 06:52:34 2018 -0400

    Add doggy image

commit fb9106cdc9ca1fc4772f0319ebd3e0d5aa3b3833
Author: Garett Arrowood <garettarrowood@gmail.com>
Date:   Thu Sep 6 06:52:10 2018 -0400

    Add kitty image

commit aa45b596d39a25d3a1fc32b6d382e5be85eccab1 (origin/master, master)
Author: Garett Arrowood <garettarrowood@gmail.com>
Date:   Thu Sep 6 06:47:06 2018 -0400

    First commit
```

By the look this output, our project has just 3 commits; a "First commit", a kitty image commit, and a doggy image commit. Let's break this down.

- The `commit` line reports the full git [SHA-1 hash](https://blog.thoughtram.io/git/2014/11/18/the-anatomy-of-a-git-commit.html#introducing-sha-1). These are the unique identifiers we can use to grab individual commits.
- The `Author` line informs us of the contributor's git username and email.
- The `Date` reports when the commit was created.
- The text below is the commit's subject. If a commit were to also contain a description, this would also be present.

That leaves the information in parentheses after the commit SHAs. The bottom commit shows `(origin/master, master)`. This indicates that it is the last commit we have from master on our current branch. Moving to the top commit, this shows `(HEAD -> example_branch)`. `example_branch` is the name of our current branch. This branch was created from master after its "First commit". [`HEAD`](https://stackoverflow.com/questions/2304087/what-is-head-in-git) represents the exact commit we are working from at the moment. Thus, our last commit is "Add doggy image", and we currently have the `example_branch` checked out.

# Git Reset

`git reset` is a powerful command that is used to undo local changes to the state of a Git repo. The command takes two arguments. The first is a flag that specifies what mode `git reset` should run in (`--soft`, `--mixed` and `--hard`). The second is a commit reference (ref). When not passed a mode or ref, `git reset` uses `--mixed` and `HEAD`. So:

```
git reset
```

is actually performing:

```
git reset --mixed HEAD
```

## Commit Refs

Before diving into modes, let's discuss how we point to different states in our git repo using commit references.

Commit refs come in a few forms. We can use the entire SHA-1 commit hash. From our `git log` output, the latest commit ref would be `39ff2a73e31c7f2016d6374538c4c987e8e24e71`. But since git SHAs are so unique, it is more common and easier to simply use the first 7 characters, or `39ff2a7`. And since `39ff2a7` is where our project is currently pointed, the commit ref could also simply be `HEAD`.

These three commands are identical in our current project state:

```
git reset 39ff2a73e31c7f2016d6374538c4c987e8e24e71
git reset 39ff2a7
git reset HEAD
```

If we want to `reset` to an earlier reference, all we need to do is grab the corresponding SHA. Let's reset back to our out "Add kitty image" commit.

```
git reset fb9106c
```

It is often easier to reset using `HEAD` instead of git SHAs though. Especially if we are only navigating a handfull of commits. The syntax for using `HEAD` is attaching the `~` or `^` after it and specifying how many commits to move backwards (`~` or `^` perform identically). So since our "Add kitty image" is only `1` commit back, instead of using the git SHA, we could use either of these commit refs to accomplish the same result.

```
git reset HEAD~1
git reset HEAD^1
```

## Reset modes


## Resources

- [`git` documentation](https://git-scm.com/doc)
- [`git log` documentation](https://git-scm.com/docs/git-log)
- [`git reset` documentation](https://git-scm.com/docs/git-reset)
- [Undoing Changes](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset)
- [The Anatomy of a Git Commit](https://blog.thoughtram.io/git/2014/11/18/the-anatomy-of-a-git-commit.html)
