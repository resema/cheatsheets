# Glossary <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Git](#1-git)
  - [1.1. Submodule](#11-submodule)
  - [1.2. Update with origin/main](#12-update-with-originmain)
- [1.3. GPG & git-crypt](#13-gpg--git-crypt)
  - [1.3.1. Link](#131-link)

---
---
# 1. Git

---
## 1.1. Submodule

https://devconnected.com/how-to-add-and-update-git-submodules/

### Initialize <!-- omit in toc -->

- `git submodule update --init --recursive`

### Update <!-- omit in toc -->
1. `cd repo/submodule`
2. `git fetch`
3. `git log --online origin/main`
4. `git checkout -q <HASh>`

Or
```
get pull origin main

git add .
git commit -m 'blub'
git push
```

Or 

`git submodule update --remote --merge`

---
## 1.2. Update with origin/main
```
# create branch with name backup
git branch backup

git rebase -i origin/main
```

---
# 1.3. GPG & git-crypt
## 1.3.1. Link
- https://medium.com/@sumitkum/securing-your-secret-keys-with-git-crypt-b2fa6ffed1a6
- Creating a **public key**
  ``` sh
  gpg --list-keys

  gpg --armor --export --output /Users/someuser/user_pubkey.gpg <ID>

  # generate key with specified encryption
  gpg --full-generate-key
  ```