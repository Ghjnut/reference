Git
---

#### Fetch Pull Requests
`+refs/pull/*/head:refs/remotes/origin/pr/*`

#### Checkout
`git checkout pr/<num>`

#### Prune
`git remote prune origin`

#### Push different branch name
`git push origin local-name:remote-name`

#### Rebase timestamps
1. `git rebase -i HEAD~5`
2. 'edit' all
3. `git commit --amend --date=now`
4. `git rebase --continue`
