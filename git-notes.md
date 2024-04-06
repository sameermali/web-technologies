# git notes

```
# unstage files 
git reset <filepath>

# get remote branch url
git config --get remote.origin.url

# clone
git clone url <folder>

# checkout remote branch
git checkout -b future_branch origin/future_branch // creates local branch with name future_branch and tracks remote branch
git checkout -t origin/future_branch               // same as above

# create new local branch
git checkout -b <new-branch-name>

# list/show branches
git branch     // show local branches
git branch -r  // show remote branches
git branch -a  // show all local and remote branches
git branch -vv // show remote tracking branch

# switch branch
git checkout <existing-branch>  // switch to existing branch

# branch contains commit id
git branch --contains <commit-id>

# [squash commit](https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec)
git rebase -i HEAD~n                               // number of commits to rebase
git rebase -i <after-this-commit-sha1>
keep one commit as pick and change all other to squash

# push local branch to remote
git push origin <local_name>
git push origin <local_tag_name> // push tag to remote
git push -f origin <remote_name> // forcefully
git push origin -f HEAD:features/MAXXFXSG-1254  // HEAD points to the top of the current branch. git can obtain the branch name from that.
git push origin -u HEAD:features/MAXXFXSG-1254  // for every branch that is up to date or successfully pushed, add upstream (tracking) reference fx-generic-buyside-hedgefund-forwards-swaps-messages-config
git push origin HEAD:master  // push top of current branch to master

# push local branch to remote with different name
git push origin local-name:remote-name

# rename branch
git branch -m <oldname> <newname>  // rename other than current branch
git branch -m <newname>            // rename current branch

# delete local branch
git branch -d <branch_name>

# delete remote branch only
git push origin --delete <branch_name>
git push origin :<branch_name>

# delete untracked files
git clean -f -d

# annotate file lines with commit information
git annotate <file_path>

# list of files changed in folder
git log --name-status -10 path/to/dir

# find branches which contain specific commit id
git branch -r --contains <commit_id>
example
git branch -r --contains 0c9d893ec89479c92d011750eecc4e000dc2aace
 origin/stable/fx7.3
 origin/stable/fx7.4

# revert commit
git revert <commit_id>

# cherry pick
git cherry-pick 79ab59282040e0938fcf21b07715ae12957ebe7a^..54a4197c6bb5cc79d4fbcb5bed3cd1bf8389b17e
git checkout <branch-to-which-we-need-to-merge>
git cherry-pick <commit-id>

# rebase remote commits of same branch (local commits are written on top of remote commits)
git fetch --all
git rebase origin/branch-name  

# stash commands [https://www.freecodecamp.org/news/useful-tricks-you-might-not-know-about-git-stash-e8a9490f0a1a/]
git stash save
git stash pop
git stash list  // list stash
git stash clear // clear all saved stashes

# merge
git reflog
git merge <branch_to_merge>            // merge interactively
git merge --no-edit <branch_to_merge>  // merge non-interactively
git merge origin/<branch-name>         // merge remote branch

# merge vs rebase
https://www.youtube.com/watch?v=f1wnYdLEpgI&ab_channel=TheModernCoder
https://www.themoderncoder.com/a-better-git-workflow-with-rebase/

# git archive
git archive --format=zip master // to check what content will be archived
git archive --format=zip -o /full/path/to/zipfile.zip master // to archive add -o argument
git archive --format=zip -o /full/path/to/zipfile.zip HEAD:subdirectory // to archive subdirectory only of current branch

# get remote repo url
git config --get remote.origin.url

# revert in case of merge
git reflog
git reset --hard HEAD@{7}

# checkout to old version of file
git log /path/to/file.txt
git checkout <commit_id> -- /path/to/file.txt
git checkout <commit_id>~1 -- /path/to/file.txt  // number of commits before commit_id

# show commit logs
git log --oneline      // show commit logs in one line
git log -- subfolder   // show commit that modified subfolder or file
git log -p file.txt    // show commit that modifed the file and also modifications can also use gitk
git log <other-branch> // show log history of branch other than current branch
git log --pretty=format:"%h%x09%an%x09%ad%x09%s" // one line log with author, date etc
git log -S "search string" --source --all

# archive repository
git archive --format zip --output /full/path/to/zipfile.zip master 

# diff of commit
git show --color --pretty=format:%b <commit-id>
git show --name-only <commit-id>   //  list only files changed in commit
git show <commit-id> <file-path>   // display diff of only specific file in specific commit

# diff between two branches
git diff branch1..branch2                        // complete diff
git diff --name-only branch1..branch2            // show only files having diff
git diff branch1..branch2 relative/path/to/file  // single file diff between two branches

# create git patch from changes in working directory
git diff > mypatch.patch
git diff --cached > mypatch.patch
git diff --cached --binary > mypatch.patch  // if want to add binary files
git format-patch -1 {commit-id} // create patch from commit id
git format-patch -5 HEAD        // create patch from last 5 commits from HEAD
git apply mypatch.patch

# change remote tracking branch 
git branch --set-upstream-to=origin/remote-branch-name

# diff recursively ignore whitespace
diff -r -b configurations/foo-sales-config /Users/flexadm/codes/backup/foo-sales-config

# ~~~~~ tags ~~~~~
# create tag
git tag <tag_name>

# list remote tags
git ls-remote --tags origin

# list local tags
git tag

# grep/search local tags
git tag -l "v1.*"

# fetch tags from remote repo origin
git fetch --tags

# switch to tag: put your working directory in the state it was when the specified tag was created
git checkout <tag>
git checkout v1.0

# check if particular commit is present in tag. it will list all tags containing commit_hash
git tag -- contains <commit_hash> 

# check if <commit_hash> is present in particular tag
git rev-list <tag_name> | grep <commit_hash>

# display tag details 
git show <tag_name>

# fetch branches tags and deleted local branches if remote deleted
git fetch --all --tags --prune

# create branch from tag
git checkout -b <branch_name> <tag_name>
git checkout --track origin/release/fxadmin6.18.3  // creates local branch with name release/fxadmin6.18.3 and sets upstream to remote branch with same name

```