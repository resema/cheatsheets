# Glossary <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Git](#1-git)
  - [1.1. Submodule](#11-submodule)
  - [1.2. Update with origin/main](#12-update-with-originmain)
- [2. GPG & git-crypt](#2-gpg--git-crypt)
  - [2.1. Link](#21-link)

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
  echo "Basic: $(echo "username:pwd4dummy" | base64)"
  ```


  │ {"application":"compute-case-complexity","env":"","level":"info","logger":"tracer","text":"DATADOG TRACER CONFIGURATION - {\"agent_url\":\"http://10.244.26.29:8126\",\"analytics_enabled\":false,\"analytics_sample_rate\":null,\"date\":\"2022-08-18T10:10:12+0000\",\"dd_version\":\"a593e735d0\",\"enabled\":true,\"env\": │