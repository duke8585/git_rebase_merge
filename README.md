# how to start

## create subfolder with repo before merge before you start

* `git clone before_rebase before_rebase_repo`
* open it via `code before_rebase_repo`
* if you get stuck, you can start again by deleting the folder `rm -rf before_rebase_repo`, then restoreing again from this repo
* this will create a new repo in the subfolder, you can open it by e.g. `code before_rebase` or `cd`-ing there and doing it via cli


## rebase multiple commits 

[here](https://blog.oddbit.com/post/2019-06-17-avoid-rebase-hell-squashing-wi/)'s the cure

* create a tmp branch from the main `git co main` then `git co -b sq_tmp`
* apply all feature commits as one squashed one `git merge origin/feat_1 --squash`
* resolve merge conflicts __ONCE__
* result
```h
* 673fb9e - (3 seconds ago) Squashed commit of the following: - max rieger (HEAD -> sq_tmp)
* cb42560 - (34 minutes ago) alter main files - max rieger (origin/main, origin/HEAD, main)
* 717cf52 - (36 minutes ago) before_pain docu - max rieger
* faa33d3 - (36 minutes ago) before pain - max rieger
* f809a5c - (39 minutes ago) after cherry-pick - max rieger
* b5ccde4 - (47 minutes ago) readme continue - max rieger
* 5106ca6 - (52 minutes ago) readme and backups - max rieger
* f5ff8bd - (56 minutes ago) more commits #3 - max rieger
* 62b93f1 - (56 minutes ago) more commits #2 - max rieger
* 5cfbd93 - (57 minutes ago) more commits #1 - max rieger
* 801b3e6 - (70 minutes ago) m.1 - max rieger
| * d4fa23f - (33 minutes ago) alter feat_1 files - max rieger (origin/feat_1)
| * 3afe0f6 - (52 minutes ago) readme and backups - max rieger
| * e4e7f03 - (54 minutes ago) more commits #5 - max rieger
| * b30b9a2 - (55 minutes ago) more commits #4 - max rieger
| * 47d7204 - (72 minutes ago) feat1.2 - max rieger
| * 9202894 - (73 minutes ago) feat_1.1 - max rieger
|/  
* 8166883 - (74 minutes ago) initial - max rieger
```
* commit the merge `git commit`
* checkout the feature branch `git checkout feat_1`
* reset the feature branch marker to the branch with the sqashed rebase `git reset --hard sq_tmp`


## if you want to see the painstaking rebasing result

* to reproduce it from before_rebase-backup
  * `git clone before_rebase before_rebase_repo`
  * `code before_rebase_repo`
  * `git co feat_1`
  * `git rebase main`
  * have ~~fun~~ pain!
* or if you wanna compare
    * `git clone after_rebase after_rebase_repo`
