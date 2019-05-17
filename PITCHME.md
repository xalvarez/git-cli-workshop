# Git CLI Workshop

Xavier Alvarez

20/05/2019

---

## Agenda

@ol[](false)

- Happy Path
- Re-writing and viewing history
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

### Git Repositories

@img[no-border](assets/img/git-upstream-repo.png)

---

### Git Repositories

@img[no-border](assets/img/git-copy-upstream-repo.png)

Note:

- A fork is a 1:1 copy of _upstream_.
- Naming convention: _origin_ is where I work, _upstream_ is where I create pull requests.

---

### Initial Setup

Cloning and forking a repository:

```
git clone -o upstream \
    git@github.com:xalvarez/git-cli-workshop.git
hub fork --remote-name origin
```

---

### Starting to work

Updating references:

```
git fetch upstream
# or git fetch --all

git checkout -b <new-branch-name> [<remote>/<branch-to-copy-and-track>]
# or git checkout -b <new-branch-name>
```

---

## Interesting Resources

@ul[](false)

- Git Official Docs: [git-scm.com/doc](https://git-scm.com/doc)
- [try.github.io](http://try.github.io)
- Hub: [github.com/github/hub](https://github.com/github/hub)

@ulend