git cheat sheet

create & clone

create new repository
git init
clone local repository
git clone /path/to/repository
clone remote repository
git clone username@host:/path/to/repository
add & remove
add changes to INDEX
git add (filename>
add changes to INDEX
git add *

remove/delete

git rm (filename>

commit & synchronize

commit changes
push changes to a remote repository
connect local repository to remote repository
update the local repository with remote changes
git commit -m "Commit message"
git push origin master
git remote add origin <server>
git pull

branches

create new branch
switch to master branch
delete branch
push branch to the remote repository
git checkout -b <branch>
e.g. git checkout -b feature_x
git checkout master
git branch -d (branch)
git push origin <branch>

merge

merge changes from another branch git merge <branch>
view changes between two branches git diff <target_branch>
e.g. git diff feature_x feature-y
tagging
create tag git tag (commit ID)
e.g. git tag 1.0.01b2e1d63ff
get commit IDs git log

restore

replace working copy with latest from HEAD git checkout (filename)

$ git config --global user.email "vlad@tran.sylvan.ia"

Closing issues -> mention closes #issue number so that it gets linked

Git flow is organized around releases which are around stuff that might not be ready for release while GitHub flow assumes there is always the main branch ready to deploy
Github flow also doesn’t have a strict sep from main and development, makes hotfix redundant 
Using GitHub flow means that you have to be very sure that your change won’t break prod, also use CI/CL and pull request discussion should be easy/transparent
Using GitHub doesn’t mean you have to use GitHub flow or git-flow 

For ops, if you need to cli to run a script, you can use a personal access token to operate on other users accounts

Using ssh uses keys which how it knows its user

Add collaborators 

Code review response:
	Comment- needs more discussion
	Accept- gtg, might need small changes (i.e. formatting)
	Request Changes- big changes needed, needs to be resubmitted 

Master is the main branch by default, but any branch can be made into main, and main means that that branch is the one that gets checked out and where default pull requests get sent 

Things to get quality issues -> Issue templates, Contributor guidelines, good documentation 

Squash and merge 
	Preserves a tidy main branch, atomic commits 
	
Condenses history for a topic (i.e. it took me three commits to fix a bug, but instead of three commits, it will just be one) 

Rebase and merge
	This will keep atomic commits, it may be hard to merge further work. the commits from the pull request’s branch are rebased on to the tip of the base branch, and then the base branch itself is fast-forwarded to this newly rebased head.

Create a merge commit 
	“Normal” the commits from the pull request’s branch are rebased on to the tip
of the base branch, and then the base branch itself is fast-forwarded
to this newly rebased head.

Git diff –name-only –diff-filter=U | uniq | xargs $EDITOR
Rebasing has some risks, like the appearance of some conflicts in several files. Use this command to open all the files which have problems that need solving.
