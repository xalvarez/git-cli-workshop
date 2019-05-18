# Git CLI Workshop

Xavier Alvarez

20/05/2019

---

## Agenda

@ol[](false)

- Happy Path
- Viewing and re-writing history
- Conflict resolution
- Reverts & resets
- Removing & moving files
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

### Initial Setup

Cloning and forking a repository:

```bash
git clone -o upstream \
    git@github.com:xalvarez/git-cli-workshop.git
hub fork --remote-name origin
```

---

### Starting to work (I)

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

## Interesting Resources

@ul[](false)

- Git Official Docs: [git-scm.com/doc](https://git-scm.com/doc)
- [try.github.io](http://try.github.io)
- Hub: [github.com/github/hub](https://github.com/github/hub)

@ulend