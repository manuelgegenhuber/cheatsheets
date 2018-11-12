<h1>Configuration</h1>

<pre>git config --global user.name "Your Name"</pre>
Sets the username in git

<br>
<br>

<pre>git config --global user.email "your.email@your-place.com"</pre>
Sets the users email in git

<br>
<br>

<pre>git config core.editor "mate -w"</pre>
Sets textmate as default git editor

<br>
<br>

<pre>git config core.editor "code -w"</pre>
sets vscode as default git editor.

<a href="https://code.visualstudio.com/docs/setup/mac">add code to shell</a>

<br>
<br>

<pre>git config --global -e</pre>
Opens global git config file in specified editor.

<br>
<br>

<pre>git init</pre>
Create an empty Git repository or reinitialize an existing one.

<br>
<br>

<pre>git config --global --list</pre>
Lists all global configurations

<br>
<br>

<pre>
git config --global diff.tool p4merge
git config --global difftool.p4merge.path "/Applications/p4merge.app/Contents/MacOS/p4merge"
git config --global difftool.prompt false
</pre>
Configure P4Merge as Diff tool
(<a href="https://www.perforce.com/products/helix-core-apps/merge-diff-tool-p4merge">Download</a>)

<br>
<br>

<pre>
git config --global merge.tool p4merge
git config --global mergetool.p4merge.path "/Applications/p4merge.app/Contents/MacOS/p4merge"
git config --global mergetool.prompt false
</pre>
Configure P4Merge as Merge tool
(<a href="https://www.perforce.com/products/helix-core-apps/merge-diff-tool-p4merge">Download</a>)

<br>
<br>

<code>HEAD</code>

Like "pointers"
Points to last Commit of current Branch
Can be Moved (Advanced)

<br>
<br>

-------------------------------------------------------------------------------

<h1>Basics</h1>

<pre>git status</pre>
shows status of current work & staging area. And also untracked files.

<br>
<br>

<pre>git log</pre>
shows (all) commits.

<br>
<br>

<pre>git reflog</pre>
Logs everything that happened on that repository.
(i.e. Branch switches and resets)

<br>
<br>

<pre>git show</pre>
shows last (HEAD) commit.
(with more detailed information i.e. differences)

<br>
<br>

<pre>git add {file}</pre>
takes file from working area and places it on stagin area.

<br>
<br>

<pre>git add .</pre>
Adds all files from the working area to the staging area.

<br>
<br>

<pre>git rm --cached {file}</pre>
Removes file from repo and staging and sets it as untracked. (need commit afterwards)

<br>
<br>

<pre>git reset HEAD {file}</pre>
Removes file from staging area and puts it to the working area.
HEAD -> last commit

<br>
<br>

<pre>git reset HEAD .</pre>
Removes all files from the staging area and places them on the working area.
HEAD -> last commit

<br>
<br>

<pre>git commit {file}</pre>
Commits selected file to the repo. (Opens file for message)

<br>
<br>

<pre>git commit -m "{message}"</pre>
A little bit faster to put q file to the repo.

<br>
<br>

<pre>git commit -a</pre>
Commits a file from the working area directly to the repo. (Opens file for message)

<br>
<br>

<pre>git commit -am "{message}"</pre>
Commits a file from the working area directly to the repo.

<br>
<br>

<pre>git commit -am "{message} , close {issue Nr.}"</pre>
Close Issue via Commit.
By the next <code>git push</code> the changes will be updated
on Github.

<br>
<br>

<pre>git mv {old_filename} {new_filename}</pre>
Renames a file and also keeps track about it. (need commit afterwards)

<br>
<br>

<pre>git checkout {file}</pre>
if changes are in the working area -> gets the last version in the repo (gets "original")

<br>
<br>

<pre>git checkout .</pre>
gets the last version in the repo of all files in the working area (removes changes)

<br>
<br>

<pre>touch .gitignore</pre>
Create .gitignore file.
Each line represents 1 expression
(i.e. *.log -> excludes all files that end with '.log')

<br>
<br>

<h1>Clean changes outside of git</h1>

<pre>git add -u</pre>
if you renamed a file without git mv (recommended).
Updates these changes to the staging area.
(needs commit afterwards)

<br>
<br>

<pre>git add -A</pre>
All file modification get to the staging area.
(i.e. if you changed the name of a file, and the new name is marked as untracked file.)

<br>
<br>

<h1>Alias</h1>

<pre>git config --global alias.{alias name} "{alias command}"</pre>
add an alias to git (can be found in git config --global --list)
(i.e. git config --global alias.history "log --oneline --graph --decorate --all" -> like log but more compact)

<br>
<br>

-------------------------------------------------------------------------------

<h1>Advanced</h1>

<pre>git tag {tag name}</pre>
Default -> last commit (HEAD)
Creates tag.

<br>
<br>

<pre>git tag {tag name} {branch name}</pre>
Default -> last commit (HEAD)
Creates tag on the last commit on
the specified tag.

<br>
<br>

<pre>git tag -d {tag name}</pre>
Deletes specified tag

<br>
<br>

<pre>git tag --list</pre>
Shows tags

<br>
<br>

<pre>git tag -a {tag name} -m "{tag msg}" {commit number}</pre>
Creates annotated tag.


<br>
<br>

<pre>git tag -f {tag name} {new commit number (optional - default HEAD)}</pre>
Changes commit assoicated to the tag.

to update github:
<code>git push --force origin unstable</code>
<br>
<br>

<pre>git show {annotated tag name}</pre>
Shows commit with annotated tag.

<br>
<br>

<pre>git push origin {tag name}</pre>
Pushes specified tag to github.

(<code>git push origin :{tag name}</code> Deletes remote connection if deleted locally -> notice semicolon!)

<br>
<br>

<pre>git push --tags</pre>
Pushes all tags to github.
<br>
<br>

<pre>git diff {commit number} HEAD</pre>
Compares the HEAD commit with the specified (commit number) commit.
HEAD -> last commit

<br>
<br>

<pre>git difftool {commit number} HEAD</pre>
Compares the HEAD commit with the specified (commit mnumber) commit.
via the specified git.difftool (i.e. P4Merge)
cmd + q -> to quit P4Merge and return to the terminal.
HEAD -> last commit

<br>
<br>

<pre>git diff</pre>
Compares recent changes on the working directory with the HEAD commit.
HEAD -> last commit

<br>
<br>

<pre>git difftool</pre>
Compares recent changes on the working directory with the HEAD commit.
via the specified git.difftool (i.e. P4Merge)
cmd + q -> to quit P4Merge and return to the terminal.
HEAD -> last commit

<br>
<br>

<pre>git diff {branch name} master</pre>
Compares last commits on the specified branches.

<br>
<br>

<pre>git difftool {branch name} master</pre>
Compares last commits on the specified branches.
via the specified git.difftool (i.e. P4Merge)
cmd + q -> to quit P4Merge and return to the terminal.

<br>
<br>

<pre>git branch</pre>
Listd all branches
asterix -> you're currently on that branch.

<br>
<br>

<pre>git branch -a</pre>
Listd all branches
asterix -> you're currently on that branch.
-a -> also shows remote branches from github

<br>
<br>

<pre>git branch -d {branch name}</pre>
Deletes specified branch.

<br>
<br>

<pre>git checkout {branch name}</pre>
To switch to a specified branch.

<br>
<br>

<pre>git checkout -b {branch name}</pre>
To create a new branch &
switch to that specified branch.

<br>
<br>

<pre>git merge {branch name} </pre>
Merges the commits into the current branch.

Switch to master (to merge with master):
<br>
<code>git checkout master</code>
<br>

Fast-Forward
<ul>
<li>Simplest Case</li>
<li>Like Never Branched (Commits on Destination)</li>
<li>Can Be Disabled</li>
</ul>
Automatic
<ul>
<li>Non-Conflicting Merge Detected</li>
<li>Preserves both Timelines</li>
<li>Merge Commit on Destination</li>
<li>New Merge Commit is created</li>
</ul>
Manual
<ul>
<li>Automatic Merge Not Possible</li>
<li>Conflicting Merge State</li>
<li>Changes Saved in Merge Commit</li>
<li>New Merge Commit is created</li>
</ul>

<br>
<br>

<pre>cat {file}</pre>
If you have a conflict
<code>Auto merging CONFLICT</code>

shows difference of the HEAD commit 
and last commit on current branch.
<br>
<br>

<pre>git mergetool</pre>
If you have a conflict
<code>Auto merging CONFLICT</code>

shows differences (conflicts)

via the specified git.difftool (i.e. P4Merge)

cmd + q -> to quit P4Merge and return to the terminal.
<br>
<br>

<pre>git stash</pre>
Saves current working directory.

And puts it aside.

(Your working directory changes are "gone")

After that you can change and commit something different.
And get that saved stash back later with: <code>git stash pop</code>

<br>
<br>

<pre>git stash list</pre>
Lists saved stashes.

<br>
<br>

<pre>git stash pop</pre>
loads last stash.

<br>
<br>

<pre>git reset {commit number} --soft</pre>
Resets current HEAD commit to specified commit.

-> working and staging area don't get cleaned.

<br>
<br>

<pre>git reset {commit number} --mixed</pre>
--mixed => default
Sets HEAD commit to sppecified commit.
Unstages all changes since that specified commit. (clears staging area)

<br>
<br>

<pre>git reset {commit number} --hard</pre>
Sets HEAD commit to sppecified commit.
Clears working and staging area.
(Most destructive reset)

<br>
<br>

-------------------------------------------------------------------------------

<h1>Github (Bitbucket, Gitlab etc)</h1>

<pre>git remote add origin {Repo url}</pre>
handles the remote connection with the Repo in Github.
origin -> name

Can be usefule to add another remote besides origin if you forked
a repository on github.
<code>git remote add {new remote name} {repo-link you forked from}</code>
<br>
<br>

<pre>git remote -v</pre>
Lists Urls for Remote Connection.
Can be 2 different urls.
Most of the time it's the same url.

<br>
<br>

<pre>git remote show origin</pre>
More detailed than <code>git remote -v</code>.

<br>
<br>

<pre>git remote set-url origin {repository url}</pre>
To change the Remote-Url.
(i.e. The Name of the Repo changed on Github)

<br>
<br>

<pre>git push</pre>
Pushes master (since Git v2.* only master)
to the repository. Even if you have other branches. Before 2.* it sent everything.

<br>
<br>

<pre>git push -u origin master</pre>
Pushes local repo to the Github repo.

origin -> Github repository

master -> branch

-u -> sets up tracking relationship

<br>
<br>

<pre>git push -u origin master --tags</pre>
Pushes local repo to the Github repo.

-u -> sets up tracking relationship

origin -> Github repository

master -> branch

--tags -> pushes it with the tags

<br>
<br>

<pre>git push origin :{branch name}</pre>
If you deleted a branch locally -> updates Github.
Start with the branch-name right after the semicolon. (No space)

<br>
<br>

<pre>git clone {git url} {folder name (optional)}</pre>
Copy's a git repository to your local machine.
(i.e. You created a Repo on Github)

<br>
<br>

<pre>git config --global push.default matching</pre>
To set git push to the old behavior.
Git will push local branches to the remote branches that already exist with
the same name. (all)
<br>
<br>

<pre>git config --global push.default simple</pre>
To set git push to the new behavior (old matching).
Only pushes the current branch to the corresponding
remote branch that <code>git pull</code>
uses to update the current branch.
<br>
<br>

<pre>git pull</pre>
Gets the changes from remote repository into the current branch.
Is a
<code>git fetch + git merge FETCH HEAD</code>
(can be destructive)

<br>
<br>

<pre>git pull --all</pre>
Updates all branches from remote repository.
<code>git fetch + git merge FETCH HEAD</code>
(can be destructive)

<br>
<br>

<pre>git fetch</pre>
updates local information based on what's changed on Github.
(non-destructive)

<br>
<br>

<pre>git fetch --all</pre>
updates local information based on all remote Connections.
(non-destructive)

<br>
<br>

<pre>git fetch -p</pre>
updates local information based on what's changed on Github.
(non-destructive)
-p -> (prune option) fetches all current
references
(i.e. It's going to look for any dead branches and remove those
references locally.)

<br>
<br>

<pre>git pull --rebase</pre>
Git pull with rebase
rebase -> updates local branch from github and sets
branch commits on top of updates from github.

before:

commit on github & commit locally (can be resolved by merge or rebase)

after:

comit locally (on top)

commit on github

changes are nore locally but github is still behind
the local commit.

<a href="https://git-scm.com/book/de/v1/Git-Branching-Rebasing">more detailed information</a>
<br>
<br>

<h1>SSH Authentication</h1>

<h2>Generate SSH-Key (mac)</h2>

<pre>cd ~/</pre>
Change directory to:
<code>"/Users/username"</code>
<pre>mkdir .ssh</pre>
Create <code>.ssh</code> directory.
That folder contains our ssh related files.
<pre>cd .ssh</pre>
Go into the .ssh folder.
<pre>ssh-keygen -t rsa-C "email-adress"</pre>
ssh-keygen -> tool to generate private and public key

-t -> type

rsa -> specified type (https://de.wikipedia.org/wiki/RSA-Kryptosystem)

-C -> Common-Name

<code>(passphrase recommended)</code>

<pre>ls -al</pre>
To list all files -> open <code>id_rsa.pub</code> and copy all of it.

<br>
<br>

<h2>Setting up SSH-Key on Github</h2>

On Github -> profile -> settings -> SSH and GPG keys -> "new SSH key".

Fill out title & paste the key.

<pre>ssh -T git@github.com</pre>
Authenticate

(passphrases needed)
<br>
<br>

<pre>ssh-add -K</pre>
Stores passphrase permanentls to Keychain.

<br>
<br>

