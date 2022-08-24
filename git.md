# Glossary <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Git](#1-git)
  - [1.1. Checkout](#11-checkout)
  - [1.2. Submodule](#12-submodule)
  - [1.3. Update with origin/main](#13-update-with-originmain)
  - [1.4. Update Submodule in Another Repo](#14-update-submodule-in-another-repo)
- [2. GPG & git-crypt](#2-gpg--git-crypt)
  - [2.1. Link](#21-link)

---
---
# 1. Git

---
## 1.1. Checkout
```sh
git checkout --recurse-submodules <URL_Repo>
```

---
## 1.2. Submodule

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
## 1.3. Update with origin/main
``` sh
# create branch with name backup
git branch backup

git rebase -i origin/main
```

---
## 1.4. Update Submodule in Another Repo
```sh
# submodule root folder
git pull # OR checkout the correct version

# step out of folder, add and commit
git add <Submodule>
git commit -m 'blub'
git push

# create PR
```


---
---
# 2. GPG & git-crypt
## 2.1. Link
- https://medium.com/@sumitkum/securing-your-secret-keys-with-git-crypt-b2fa6ffed1a6
- Creating a **public key**
  ``` sh
  gpg --list-keys

  gpg --armor --export --output /Users/someuser/user_pubkey.gpg <ID>

  # generate key with specified encryption
  gpg --full-generate-key

  # Basic Auth
  echo "Basic $(echo -n "outsim:W2NXU82dxBxsglAWwX2TSD4UZ3NX8ghm" | base64)"
  ```

