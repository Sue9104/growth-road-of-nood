# Git

## 分支

![](../.gitbook/assets/git_workflow.png)

* Main分支
  * Master \(只負責管理發布的狀態\)
  * Develop（針對日常開發的分支）
* Feature分支 （新功能的開發或修復錯誤的時候從 develop 分支分開出來）
* Release分支（發布前最後錯誤修復所建立的分支）
* Hot fix分支（master 分支直接建立分支進行修改）

  **常见命令**

* git branch \(-d\)
* git checkout
* git stash \(list\|apply --index\|drop\|pop\|branch\)

## 远端操作

* git fetch 
* git pull \(--rebase\)
* push

## 标签

* git tag \(-am \| -n \| -d\)
* git push --tags

## 改写提交

* git commit --amend

## 取消提交

* git revert（有revert历史）
* git reset（无历史记录）
  * hard 徹底取消最近的提交 \(ORIG\_HEAD\)
  * mixed 復原修改過的索引的狀態
  * soft 只取消提交

## 合并提交

* git cherry-pick
* git rebase -i \(--continue\|--abort\)
* git merge --squash 合并同一分支的所有提交

## changelog

```text
cargo install clog-cli
```

## 常见问题

### create a new ssh key and adding to ssh-agent

* localhost

```text
ssh-keygen -t ed25519 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

* github website
  * Settings -&gt; SSH and GPG Keys

### connection timed out

```text
git config --global --unset http.proxy
git config --global --unset https.proxy
```

### Hosts加速

* [https://github.com/ineo6/hosts](https://github.com/ineo6/hosts)

