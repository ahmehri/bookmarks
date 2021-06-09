# Misc

- [One second to read GitHub code with VS Code](https://github.com/conwnet/github1s)
- https://git-scm.com/docs/gitrevisions
- [Merging vs Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/)
- [Interactive staging](https://git-scm.com/book/en/v2/Git-Tools-Interactive-Staging#_interactive_staging)
- [The Refspec](https://git-scm.com/book/en/v2/Git-Internals-The-Refspec#_refspec)
- [A successful git branching model](http://nvie.com/posts/a-successful-git-branching-model/)
- [Reset demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
- [Is there a git-merge --dry-run option?](https://stackoverflow.com/questions/501407/is-there-a-git-merge-dry-run-option)
- [Alwasy squash and rebase your git commits](https://blog.carbonfive.com/2017/08/28/always-squash-and-rebase-your-git-commits/)
- [Debugging with git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)
- [Keeping commit histories clean](https://www.notion.so/Keeping-Commit-Histories-Clean-0f717c4e802c4a0ebd852cf9337ce5d2)
- [gitrevisions](https://git-scm.com/docs/gitrevisions)
- [10 git antipatterns you should be aware of](https://speakerdeck.com/lemiorhan/10-git-anti-patterns-you-should-be-aware-of?slide=6)
- [How to find out which branch tag is?](https://stackoverflow.com/questions/15806448/git-how-to-find-out-on-which-branch-tag-is)
- [Find out when a file has been added/deleted](https://www.shellhacks.com/git-particular-file-change-history/)
- https://koukia.ca/how-to-remove-local-untracked-files-from-the-current-git-branch-571c6ce9b6b1
- [git diverged get remote](https://gist.github.com/scmx/f0cf283f33e5e1ac83946453461b9ff2)
- https://www.atlassian.com/blog/git/advanced-git-aliases
- [Rebase by default when doing git pull](https://coderwall.com/p/tnoiug/rebase-by-default-when-doing-git-pull)

# Github

- [Run your GitHub Actions locally](https://github.com/nektos/act)
- [The command palette for GitHub](https://jumpcat.dev/)

# Pruning remote branches

- [A short story of pruning remote branches](http://www.jamessturtevant.com/posts/Pruning-remote-branches/)
- [Always prune remote traching branches](http://albertogrespan.com/blog/always-prune-remote-tracking-branches/)

# Rebasing

- [How to rebase a pr](https://github.com/edx/edx-platform/wiki/How-to-Rebase-a-Pull-Request)
- [git merge-base](https://git-scm.com/docs/git-merge-base)
- [How to rebase your feature branch from one branch to another](https://makandracards.com/makandra/10173-git-how-to-rebase-your-feature-branch-from-one-branch-to-another)
- [git find out which branch is based on](https://community.atlassian.com/t5/Bitbucket-questions/Knowing-from-which-branch-the-current-branch-was-created-from/qaq-p/570135)
- https://romanofskiat.wordpress.com/2015/05/12/git-moving-partial-changes-between-commits/

# Rewriting things

- [Rewriting history](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History)
- [Undo things](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)

# Hooks

- [typicode/husky](https://github.com/typicode/husky)
- [observing/pre-commit](https://github.com/observing/pre-commit)
- [okonet/lint-staged](https://github.com/okonet/lint-staged)
- [Make linting great again](https://medium.com/@okonetchnikov/make-linting-great-again-f3890e1ad6b8)

# Conventional commits

- [conventional-changelog/conventionalcommits.org](https://github.com/conventional-changelog/conventionalcommits.org)
- [commitizen/cz-cli](https://github.com/commitizen/cz-cli)
- [commitizen/cz-conventional-changelog](https://github.com/commitizen/cz-conventional-changelog)
- [conventional-changelog/conventional-changelog](https://github.com/conventional-changelog/conventional-changelog)
- [Lint commit messages](https://github.com/marionebl/commitlint)
- [Conventional commits](https://conventionalcommits.org/)
- [Keep a changelog](https://keepachangelog.com/en/0.3.0/)

# Git completion on macos

git completion is provided by git-completion.bash script that can be obtained only when installing git using homebrew brew install git. The file will automatically be added to /usr/local/etc/bash_completion.d folder given that bash-completion is already installed, brew install bash-completion.

This has nothing to do with bash-completion@2 homebrew package.

# Tools

- [jkup/pullit](https://github.com/jkup/pullit)
- [nvie/gitflow](https://github.com/nvie/gitflow)

# Ignore files that haven't been managed by git yet locally

Add them in `.git/info/exclude` file. To list such files, simply check the content of the file.

`git update-index --skip-worktree <file>` is for the files which are already managed by git.

# Diffing

- [so-fancy/diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)
- https://matthew-brett.github.io/pydagogue/git_diff_dots.html

## How to beautifully render a diffing in browser

You need first to get the diffing content correctly (with differences explicitly indicated with `-` and `+` signs). In order to do this, you need to use `git diff` command.

Keep in mind though that copying the diff from the terminal won't contain the signs. In order to get them, use `pbcopy` command (pasteboard copy command on macos) as a pipe to copy the content with signs to the clipboard.

`git diff | pbcopy`

The last step is to use that content in markdown code using the `diff` type.

## Diff between two branches

```
       git diff [<options>] <commit> <commit> [--] [<path>...]
           This is to view the changes between two arbitrary <commit>.

       git diff [<options>] <commit>..<commit> [--] [<path>...]
           This is synonymous to the previous form. If <commit> on one side is omitted, it will have
           the same effect as using HEAD instead.

       git diff [<options>] <commit>...<commit> [--] [<path>...]
           This form is to view the changes on the branch containing and up to the second <commit>,
           starting at a common ancestor of both <commit>. "git diff A...B" is equivalent to "git
           diff $(git merge-base A B) B". You can omit any one of <commit>, which has the same effect
           as using HEAD instead.
```

What I want is the third form:
`git diff master...my-branch` eq to `git diff master...`

which will be converted to:
`git diff $(git merge-base master my-branch)..my-branch --name-only`

which is also equivalent to:
`git diff $(git merge-base master my-branch) my-branch --name-only`

The reason why the following doesn't work is because there is no starting point, the branch will be compared to master starting from the very first commit instead of the merge-base:
`git diff master` eq to `git diff master my-branch` eq to `git diff master..my-branch`

# Resources

- [Git Pro book](https://git-scm.com/book/en/v2)
