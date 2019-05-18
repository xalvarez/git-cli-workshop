# Git CLI Workshop

Xavier Alvarez

20/05/2019

---

## Agenda

@ol[](false)

- Happy Path
- Viewing and re-writing history
- Undoing changes
- Git configuration
- Handling multiple accounts
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

---

@title[Re-writing history (I)]

@snap[north span-100]
### Re-writing history
@snapend

@snap[west span-45]
@box[bg-green text-white box-padding](Changing last commit#git commit --amend)
@snapend

@snap[east span-45]
@box[bg-green text-white box-padding](Interactive rebase#git rebase -i HEAD~&lt;n&gt;)
@snapend

---

@title[Re-writing history (II)]

@snap[west span-35]
@img[no-border](assets/img/git-before-amend.png)
@snapend

@snap[east span-35]
@img[no-border fragment](assets/img/git-after-amend.png)
@snapend

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

@snap[north span-100]
### Git Configuration
@snapend

@snap[west span-45]
@box[bg-green text-white box-padding](Repo's config#.git/config)
@snapend

@snap[east span-45]
@box[bg-green text-white box-padding](Repo's config#~.gitconfig)
@snapend

@snap[south-west span-45]

```bash
git config -l
```

@snapend

@snap[south-east span-45]

```bash
git config --global -l
```

@snapend

---

## Interesting Resources

@ul[](false)

- Git Official Docs: [git-scm.com/doc](https://git-scm.com/doc)
- [try.github.io](http://try.github.io)
- Hub: [github.com/github/hub](https://github.com/github/hub)

@ulend