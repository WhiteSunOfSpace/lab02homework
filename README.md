alias edit=nano
cd WhiteSunOfSpace/workspace
git config —global hub.protocol https
cd projects/lab02homework

git branch patch1
git switch patch1

edit ./proga/hello_world.cpp
git add .
git commit -m "change hello_world"
git push origin patch1

edit ./proga/hello_world.cpp
git add .
git commit -m "modified hello_world"
git push origin patch1

git status
```shell
On branch patch1
Untracked files:
(use "git add <file>..." to include in what will be committed)
origin

nothing added to commit but untracked files present (use "git add" to track)
```

git rebase master
Current branch patch1 is up to date.

git switch master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

git checkout master
Already on 'master'
Your branch is up to date with 'origin/master'.

git merge patch1
```shell
Updating 7382f5e..34d68cf
Fast-forward
master | 0
origin | 0
proga/hello_world.cpp | 9 +++++----
3 files changed, 5 insertions(+), 4 deletions(-)
create mode 100644 master
create mode 100644 origin
```

git branch -d patch1
```shell
Deleted branch patch1 (was 34d68cf).
```


git branch patch2
git switch patch2
Switched to branch 'patch2'

clang-format -style=Mozilla ./proga/hello_world.cpp
```bash
#include <iostream>
#include <string>

int
main()
{
string name; // name
std::cin » name; // input
std::cout « "hello world from " « name « endl; // output
return 0;
}
clang-format -i ./proga/hello_world.cpp
```

git status
```shell
On branch patch2
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: proga/hello_world.cpp

no changes added to commit (use "git add" and/or "git commit -a")
```

git add .
git commit -m "mozilla codestyle"
```shell
[patch2 13dcfaa] mozilla codestyle
1 file changed, 5 insertions(+), 5 deletions(-)
```

git push origin patch2
```shell
Username for 'https://github.com': WhiteSunOfSpace
Password for 'https://WhiteSunOfSpace@github.com':
Enumerating objects: 26, done.
Counting objects: 100% (26/26), done.
Delta compression using up to 4 threads
Compressing objects: 100% (19/19), done.
Writing objects: 100% (25/25), 2.25 KiB | 769.00 KiB/s, done.
Total 25 (delta 7), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (7/7), done.
remote:
remote: Create a pull request for 'patch2' on GitHub by visiting:
remote: https://github.com/WhiteSunOfSpace/lab02homework/pull/new/patch2
remote:
To https://github.com/WhiteSunOfSpace/lab02homework.git
* [new branch] patch2 -> patch2
```

git pull origin master
```shell
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100%
18:31


(1/1), 894 bytes | 894.00 KiB/s, done.
From https://github.com/WhiteSunOfSpace/lab02homework
* branch master -> FETCH_HEAD
7382f5e..5a36a61 master -> origin/master
hint: You have divergent branches and need to specify how to reconcile them.
hint: You can do so by running one of the following commands sometime before
hint: your next pull:
hint:
hint: git config pull.rebase false # merge (the default strategy)
hint: git config pull.rebase true # rebase
hint: git config pull.ff only # fast-forward only
hint:
hint: You can replace "git config" with "git config —global" to set a default
hint: preference for all repositories. You can also pass —rebase, —no-rebase,
hint: or —ff-only on the command line to override the configured default per
hint: invocation.
fatal: Need to specify how to reconcile divergent branches.
```

git pull —rebase origin master
```shell
From https://github.com/WhiteSunOfSpace/lab02homework
* branch master -> FETCH_HEAD
Successfully rebased and updated refs/heads/patch2.
git push origin patch2 —force
Username for 'https://github.com': WhiteSunOfSpace
Password for 'https://WhiteSunOfSpace@github.com':
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 680 bytes | 680.00 KiB/s, done.
Total 6 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/WhiteSunOfSpace/lab02homework.git
+ 13dcfaa...11a2706 patch2 -> patch2 (forced update)
```

git switch master
```shell
Switched to branch 'master'
Your branch and 'origin/master' have diverged,
and have 1 and 1 different commits each, respectively.
(use "git pull" to merge the remote branch into yours)
```

git merge patch2
```shell
Merge made by the 'ort' strategy.
proga/hello_world.cpp | 10 +++++-----
1 file changed, 5 insertions(+), 5 deletions(-)
```

git status
```shell
On branch master
Your branch is ahead of 'origin/master' by 4 commits.
(use "git push" to publish your local commits)

nothing to commit, working tree clean
```

