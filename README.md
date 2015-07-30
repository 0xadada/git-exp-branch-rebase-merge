# Git Experiment: Branch / Rebase / Merge

Experiment tests the workflow where there is a master branch, user checks
out feature branch from master branch. User commits work to feature branch.
Work continues in parallel in master branch. User on feature branch rebases
master `32785`, does a force-push to GitHub (required for pushing a rebase
to a published history). Finally `32789` on master, merges in feature
branch with a squash, and commits the commit message.

```
32758  echo "1" > 1
32760  git add -A && git commit -m "#1"
32761  git push origin master
32762  echo "2" >> 1
32763  git commit -am "#2"
32764  git push origin master
32765  git checkout -b feature
32766  echo "a" >> a
32768  git add -A
32769  git commit -am "#a"
32770  git push origin feature
32771  echo "b" >> a
32772  git commit -am "#b"
32773  git push origin feature
32774  git checkout master
32775  echo "3" >> 1
32776  git commit -am "#3"
32777  echo "4" >> 1
32778  git commit -am "#4"
32779  git push origin master
32780  git checkout feature
32782  echo "#c" >> a
32784  git commit -am "#c"
32785  git rebase master
32788  git push origin feature --force
32789  git checkout master
32790  git merge feature --squash
32791  git push origin master
32794  git commit -am "#5 git merge feature --squash"
32795  git push origin master
```
