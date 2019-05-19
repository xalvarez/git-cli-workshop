# Git CLI Workshop

Xavier Alvarez

20/05/2019

---

## Presentation slides

[gitpitch.com/xalvarez/git-cli-workshop](https://gitpitch.com/xalvarez/git-cli-workshop)

@img[no-border](assets/img/git-cli-workshop-qr.png)

---

## Agenda

@ol[](false)

- Happy Path
- Viewing and re-writing history
- Undoing changes
- Refactoring
- Git configuration
- Guidelines for writing commits

@olend

---

## Happy Path

---

### Git Repositories (I)

@img[no-border](assets/img/git-upstream-repo.png)

---

### Git Repositories (II)

@img[no-border](assets/img/git-copy-upstream-repo.png)

Note:

- A fork is a 1:1 copy of _upstream_.
- Naming convention: _origin_ is where I work, _upstream_ is where I create pull requests.

---

@title[Initial Setup (I)]

### Initial Setup

Cloning and forking a repository:

```bash
git clone -o upstream \
    git@github.com:xalvarez/git-cli-workshop.git
hub fork --remote-name origin
```

---

@title[Initial Setup (II)]

@img[no-border](assets/img/git-after-cloning.png)

---

### Starting to work

Updating references:

```bash
git fetch upstream
# or git fetch --all

git checkout -b <new-branch-name> [<remote>[/<branch>]]
# or git checkout -b <new-branch-name>

git branch <new-branch-name> [<remote>[/<branch>]]
# or git branch <new-branch-name>
```

---

### Starting to work (II)

Checking working branch:

```bash
git branch -vv
git branch -m <new-branch-name>
git branch -u <remote>[/<branch>]
```

---

### Committing changes (I)

Preparing a commit:
```bash
git status
git add <path>
git add -u
git add -A
```

---

### Committing changes (II)

Preparing a commit:
```bash
git commit
git commit -m
git commit -a
git commit --amend
```

---

### Delivering changes (I)

Merging local and remote branches:
```bash
git fetch upstream
git rebase upstream/master
```

---

### Delivering changes (II)

Creating a pull request:
```bash
git push
git push -u <remote> <branch>
hub pull-request -o
```

---

## Viewing and re-writing history

---

### Viewing history

Checking last commits:
```bash
git log
git log -<>
git log <path>
git log --oneline
git log --raw
```

@css[fragment](Some visualization tools:)

@ul[fragment](false)

- gitk: sudo apt install gitk
- GitKraken (non-commercial use only): [gitkraken.com](https://www.gitkraken.com)

@ulend

---

@title[Re-writing history (I)]

### Re-writing history

Changing last commit:

```bash
git commit --amend
```

Changing history:

```bash
git rebase -i HEAD~<n>
```

---

@title[Re-writing history (II)]

@snap[west span-35]
@img[no-border](assets/img/git-before-amend.png)
@snapend

@snap[east span-35]
@img[no-border fragment](assets/img/git-after-amend.png)
@snapend

Note:

What happens to commit ID's after amend or rebase? E.g. amend:

- Before amend: local and remote copies are equal
- After amend: one ID has changed

---

### Force push

@ul[](false)

- **It's a destructive operation!**
- It must only be used when necessary

@ulend

```bash
git push -f | --force [remote] [branch]
git push <remote> +<branch>
```

---

## Undoing changes

---

### Reverting changes

@ul[](false)

- It's a safe operation!
- No conflicts
- Your pair-programming partner will love you

@ulend

```bash
git revert HEAD~<n>
git revert <commit_hash>
git revert <oldest_commit_to_revert>..<newest_commit_to_revert>
```

---

### Resetting

Reset modes:

@ul[](false)

- --mixed (default): _unstages_ current working tree (not marked for commit)
- --soft: leaves current working tree staged (marked for commit)
- --hard: removes current working tree. Destroys local changes!

@ulend

```bash
git reset [mode] <remote>/<branch>
git reset [mode] <commit_hash>
```

---

### Fetching remote files

```bash
git checkout [<remote>/<branch>] [<path to replace>]
```

### Stashing

```bash
git stash
git stash push [-m <message>
git stash list
git stash apply [stash_id]
git stash pop [stash_id]
git branch <new-branch-name> [stash_id]
```

---

## Refactoring

Removing files:

```bash
git rm [-r] <path>
# Removes file from the index and from the disk

git rm --cached <path>
# Removes file from the index only (no physical removal)
```

Moving files:

```bash
git mv <current_path> <new_path>
# Shortcut for mv && git add && git rm
```

Copying commit:

```bash
git cherry-pick <commit>
```

---

## Git Configuration

```bash
git config [--global] -l
git config user.name "Xavier Alvarez"
git config color.ui auto
git config alias.<some alias> <git command>
git config alias.<some alias> !<shell command>
```

Configuration files:

@ul[](false)

- Global configuration: ~/.gitconfig
- Current repo's configuration: .git/config

@ulend

---

## Guidelines for writing commits

---

## How to write a good commit? (I)

Main ideas:

@ul

- These are guidelines and should be adapted to each team / use-case
- 50/72 rule (**vim** uses it by default)
- Use imperative (just like _git_ does)
- Talk about _what_ and / or _why_, not about _how_

@ulend

---

## How to write a good commit? (II)

Commit structure:

@ol

- Title (max. 50 characters) answering the question _what?_
- (Optional) Further information answering the question _what?_
- (Optional) Explain the problem that the commit solves (answering the question _why?_)

@olend

---

## How to write a good commit? (III)

Examples:

@ul

- [The seven rules of a great Git commit message](https://chris.beams.io/posts/git-commit/#seven-rules)
- [Commit guidelines (git official documentation)](https://www.git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project#_commit_guidelines)

@ulend

---

## Interesting Resources

@ul[](false)

- Git Official Docs: [git-scm.com/doc](https://git-scm.com/doc)
- How to write ranges: [git-scm.com/docs/gitrevisions](https://git-scm.com/docs/gitrevisions)
- [try.github.io](http://try.github.io)
- Hub: [github.com/github/hub](https://github.com/github/hub)
- gitk: sudo apt install gitk
- GitKraken (non-commercial use only): [gitkraken.com](https://www.gitkraken.com)

@ulend

---?image=assets/img/thank-you.png

@title[Thank you]

@snap[south-east text-05]
Image by [Gerd Altman](https://pixabay.com/users/geralt-9301) from [Pixabay](https://pixabay.com)
@snapend