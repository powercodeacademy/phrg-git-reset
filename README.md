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

That leaves the information in parentheses after the commit SHAs. The bottom commit shows `(origin/master, master)`. This indicates that it is the last commit we have from the master on our current branch. Moving up to the top commit, it shows `(HEAD -> example_branch)`. `example_branch` is the name of our current branch. This branch was created from master after its "First commit". [`HEAD`](https://stackoverflow.com/questions/2304087/what-is-head-in-git) represents the exact commit we are working from at the moment. Thus, our last commit is "Add doggy image", and we currently have the `example_branch` checked out.


# Git Reset

...


## Resources

- [`git` documentation](https://git-scm.com/doc)
- [`git log` documentation](https://git-scm.com/docs/git-log)
- [`git reset` documentation](https://git-scm.com/docs/git-reset)
- [Undoing Changes](https://www.atlassian.com/git/tutorials/undoing-changes/git-reset)
- [The Anatomy of a Git Commit](https://blog.thoughtram.io/git/2014/11/18/the-anatomy-of-a-git-commit.html)
