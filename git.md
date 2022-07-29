# Glossary <!-- omit in toc -->
### Table of Content <!-- omit in toc -->
- [1. Git](#1-git)
  - [1.1. Submodule](#11-submodule)

---
---
# 1. Git

---
## 1.1. Submodule

### Initialize <!-- omit in toc -->

- `git submodule update --init --recursive`

### Update <!-- omit in toc -->
1. `cd repo/submodule`
2. `git fetch`
3. `git log --online origin/main`
4. `git checkout -q <HASh>`