# GIT ADVANCED EXERCISES

## Part 1: Refining Git History (10 Challenges)

Missing File Fix:

Run git status and git log to assess the current state of your repository.
From the status you will see that you forgot to add test4.md in the last commit.
Challenge: Recover from this error by staging/adding test4.md and amending the commit message with an appropriate description.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git log
commit 11a1ab9bc01e2f7db36f2d2183ec5e71c8486599 (HEAD -> main)
Author: ntwalii <ntwaliaubin@gmail.com>
Date:   Tue May 21 17:02:00 2024 +0200

    chore: Create third and fourth files

commit e33522048b61c9599f4b9b7b9ac2fdb0b6ca3761
Author: ntwalii <ntwaliaubin@gmail.com>
Date:   Tue May 21 17:01:59 2024 +0200

    chore: Create another file

commit 8cf8b3fd8d232985d6afa7f6f6962d29471d54ff
Author: ntwalii <ntwaliaubin@gmail.com>
Date:   Tue May 21 17:01:59 2024 +0200

    chore: Create initial file

commit 95908c49d2348c183d728f1854e609e11810000f (origin/main)
Author: ntwalii <ntwaliaubin@gmail.com>
Date:   Tue May 21 16:59:49 2024 +0200

    First push

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git commit -a -m "Added test 4" --amend
[main b48be4d] Added test 4
 Date: Tue May 21 17:02:00 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test3.md

```
2. Editing Commit History:

It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".
Challenge: Utilize interactive rebasing (git rebase -i HEAD~2) to edit the commit message and ensure clarity. learn more about git rebase here.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i HEAD~2
[detached HEAD 81afad8] Create second file
 Date: Tue May 21 17:01:59 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
Successfully rebased and updated refs/heads/main.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git log --oneline
c6d67a1 (HEAD -> main) Added test 4
81afad8 Create second file
8cf8b3f chore: Create initial file
95908c4 (origin/main) First push

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$
```

3. Keeping History Tidy - Squashing Commits:

Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.
Challenge: Use interactive rebasing with the squash command to achieve this. learn more about squash here

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i --root
[detached HEAD f07739a] Squashed two commits
 Date: Tue May 21 16:59:49 2024 +0200
 2 files changed, 2 insertions(+)
 create mode 100644 README.md
 create mode 100644 test1.md
Successfully rebased and updated refs/heads/main.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git log --oneline
83f987f (HEAD -> main) Added test 4
7af4a12 Create second file
f07739a Squashed two commits

```

4. Splitting a Commit:

Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".
Challenge: Leverage git reset to separate the files into individual commits with distinct messages. learn more about splitting commits here

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i --root
Stopped at 469b799...  Squashed two commits
You can amend the commit now, with

  git commit --amend

Once you are satisfied with your changes, run

  git rebase --continue

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 2/4)
$ git status
interactive rebase in progress; onto 65af2c5
Last commands done (2 commands done):
   pick 95908c4 First push
   edit 469b799 Squashed two commits
Next commands to do (2 remaining commands):
   pick fe32c8e Create second file
   pick 1c03549 Added test 4
  (use "git rebase --edit-todo" to view and edit)
You are currently editing a commit while rebasing branch 'main' on '65af2c5'.
  (use "git commit --amend" to amend the current commit)
  (use "git rebase --continue" once you are satisfied with your changes)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 2/4)
$ git add test4.md

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 2/4)
$ git commit -m "Create test 4"
[detached HEAD e4805e2] Create test 4
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test4.md

```

5.Advanced Squashing:

Let's explore more complex squashing. Can you combine the last two commits ("Create third file" and "Create fourth file") into a single commit named "Create third and fourth files"?
Challenge: Utilize interactive rebasing with the squash command to achieve this advanced squash. Check step 4

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 2/4)
$ git rebase --continue
Successfully rebased and updated refs/heads/main.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i --root
[detached HEAD bdcbcc9] Create third and fourth files
 Date: Tue May 21 16:59:49 2024 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.
```
6.Dropping a Commit:

We all make mistakes. Imagine needing to completely remove an unwanted commit from your history.

Create a new file named unwanted.txt add some changes and commit it with a message like "Unwanted commit".
Challenge: Use git rebase -i to identify and remove the "Unwanted commit" commit, cleaning up your history. learn more about dropping commits here


```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ touch unwanted.txt

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git add .

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git commit -m "Unwanted commit"
[main 59d5cc6] Unwanted commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 unwanted.txt

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i --root
Successfully rebased and updated refs/heads/main.
```

7. Reordering Commits:

Delve deeper into git rebase -i. Can you rearrange commits within your history using this command? learn more about ordering commits here

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git rebase -i --root
Successfully rebased and updated refs/heads/main.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$
```

8.Cherry-Picking Commits:

Create a branch, call it ft/branch, and add a new file named test5.md with some content. Commit these changes with a message like "Implemented test 5".
Imagine you only desire a specific commit from ft/branch. Research and use git cherry-pick to selectively bring that commit into your current branch which is main.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout -b ft/branch
Switched to a new branch 'ft/branch'

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ touch test5.md

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git add .

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git commit "Implemented test 5"
error: pathspec 'Implemented test 5' did not match any file(s) known to git

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git commit -m "Implemented test 5"
[ft/branch 1bc2810] Implemented test 5
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test5.md

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git log --oneline
1bc2810 (HEAD -> ft/branch) Implemented test 5
a1286de (main) Added test 4
5951629 Create second file
108e10f First push
51ad0b5 Create third and fourth files

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git switch master
fatal: invalid reference: master

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/branch)
$ git switch main
Switched to branch 'main'
Your branch and 'origin/main' have diverged,
and have 4 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git cherry-pick 1bc2810
[main 4371ffe] Implemented test 5
 Date: Wed May 22 16:40:08 2024 +0200
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test5.md

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git log --oneline
4371ffe (HEAD -> main) Implemented test 5
a1286de Added test 4
5951629 Create second file
108e10f First push
```

9.Visualizing Commit History (Bonus):

Tools like git log --graph or a graphical Git client can help visualize your commit history. Explore these tools for a clearer understanding of your workflow.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git log --graph
* commit 4371ffe84837462d34acdca29e72c2f138edd095 (HEAD -> main)
| Author: ntwalii <ntwaliaubin@gmail.com>
| Date:   Wed May 22 16:40:08 2024 +0200
|
|     Implemented test 5
|
* commit a1286dec85752482784f11e7681db39eab7150e6
| Author: ntwalii <ntwaliaubin@gmail.com>
| Date:   Tue May 21 17:02:00 2024 +0200
|
|     Added test 4
|
* commit 5951629d3bae654f10ade94b2c4c51f884a2bb0b
| Author: ntwalii <ntwaliaubin@gmail.com>
| Date:   Tue May 21 17:01:59 2024 +0200
|
|     Create second file
|
* commit 108e10f8d71ac04e487b1f770a7c57817dfe315b
| Author: ntwalii <ntwaliaubin@gmail.com>
| Date:   Tue May 21 16:59:49 2024 +0200
|
|     First push
|
* commit 51ad0b5422dbbd455b4f66af93198237c27b9eac
  Author: ntwalii <ntwaliaubin@gmail.com>
  Date:   Tue May 21 16:59:49 2024 +0200

      Create third and fourth files

      Squashed two commits

      First push

      chore: Create initial file

      Create test 4

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$
```

10.Understanding Reflogs (Bonus):

Reflogs track Git operation history. Research about git reflog to learn how you can navigate back to previous states in your repository if needed.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git reflog
4371ffe (HEAD -> main) HEAD@{0}: cherry-pick: Implemented test 5
a1286de HEAD@{1}: checkout: moving from ft/branch to main
1bc2810 (ft/branch) HEAD@{2}: commit: Implemented test 5
a1286de HEAD@{3}: checkout: moving from main to ft/branch
a1286de HEAD@{4}: rebase (finish): returning to refs/heads/main
a1286de HEAD@{5}: rebase (pick): Added test 4
5951629 HEAD@{6}: rebase (pick): Create second file
108e10f HEAD@{7}: rebase (pick): First push
51ad0b5 HEAD@{8}: rebase (pick): Create third and fourth files
b27559e HEAD@{9}: rebase (start): checkout b27559e92d7440490ffd2b58b42daf0a6d336ab2
579837e HEAD@{10}: rebase (abort): updating HEAD
afea562 HEAD@{11}: rebase (start): checkout afea562ebbf467a872dba2d3057950f148c676a6
579837e HEAD@{12}: rebase (finish): returning to refs/heads/main
579837e HEAD@{13}: rebase: fast-forward
9a6c2f1 HEAD@{14}: rebase: fast-forward
bdcbcc9 HEAD@{15}: rebase: fast-forward
95908c4 (origin/main) HEAD@{16}: rebase: fast-forward
70b1813 HEAD@{17}: rebase (start): checkout 70b18130e0e086f91ffe58ea23e0cf6a6c24438a
59d5cc6 HEAD@{18}: commit: Unwanted commit
579837e HEAD@{19}: rebase (finish): returning to refs/heads/main
579837e HEAD@{20}: rebase (pick): Added test 4
9a6c2f1 HEAD@{21}: rebase (pick): Create second file
bdcbcc9 HEAD@{22}: rebase (squash): Create third and fourth files
469b799 HEAD@{23}: rebase: fast-forward
95908c4 (origin/main) HEAD@{24}: rebase: fast-forward
6235e24 HEAD@{25}: rebase (start): checkout 6235e24e0ba01be80de5022e6b5098239727f944
ad35534 HEAD@{26}: rebase (continue) (finish): returning to refs/heads/main
ad35534 HEAD@{27}: rebase (continue) (pick): Added test 4
fa2109d HEAD@{28}: rebase (continue) (pick): Create second file
b44ad99 HEAD@{29}: commit (amend): Create test 4
e4805e2 HEAD@{30}: commit: Create test 4
469b799 HEAD@{31}: rebase: fast-forward
95908c4 (origin/main) HEAD@{32}: rebase: fast-forward
65af2c5 HEAD@{33}: rebase (start): checkout 65af2c599553a06407020fe44b108fcac890e2d8
1c03549 HEAD@{34}: rebase (finish): returning to refs/heads/main
1c03549 HEAD@{35}: rebase (pick): Added test 4
fe32c8e HEAD@{36}: rebase (pick): Create second file
469b799 HEAD@{37}: rebase (pick): Squashed two commits
95908c4 (origin/main) HEAD@{38}: rebase (start): checkout refs/remotes/origin/main
83f987f HEAD@{39}: rebase (continue) (finish): returning to refs/heads/main
83f987f HEAD@{40}: rebase: fast-forward
7af4a12 HEAD@{41}: rebase: fast-forward
f07739a HEAD@{42}: rebase: fast-forward
89c68a2 HEAD@{43}: rebase (start): checkout 89c68a229246400707502d51b13ee0a68950d0f4
83f987f HEAD@{44}: rebase (finish): returning to refs/heads/main
83f987f HEAD@{45}: rebase (pick): Added test 4
7af4a12 HEAD@{46}: rebase (pick): Create second file
f07739a HEAD@{47}: rebase (squash): Squashed two commits
```

## Part 2: Branching Basics

1. Feature Branch Creation:

Imagine working on a new feature named ft/new-feature. Let's establish a dedicated branch for it.
Challenge: Create a new branch named ft/new-feature and switch to that branch.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$
```

2. Working on the Feature Branch:

Create a new file named feature.txt in this branch and add some content to it.
Commit these changes with a descriptive message like "Implemented core functionality for new feature".

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout -b ft/new-feature
Switched to a new branch 'ft/new-feature'

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$
```

3.Switching Back and Making More Changes:

It's common to switch between branches during development.
Challenge: Switch back to the main branch (previously master) and create a new file named readme.txt with some introductory content. Commit these changes with a message like "Updated project readme".

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ touch readme.txt

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git add .

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git commit -m "Updated project readme"
[main 751fdbc] Updated project readme
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 readme.txt

```
5. Branch Deletion:

After merging or completing work on a feature branch, it's good practice to remove it.
Challenge: Delete the ft/new-feature branch once you're confident the changes are integrated into main.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git branch -D ft/new-feature
Deleted branch ft/new-feature (was 06a24d9).
```

6. Creating a Branch from a Commit:

You can also create a branch from a specific commit in your history.
Challenge: Use git checkout -b ft/new-branch-from-commit commit-hash (adjust the commit hash as needed) to create a new branch named ft/new-branch-from-commit starting from the commit two positions back in your history. learn more here

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout -b ft/new-branch-from-commit 4371ffe
Switched to a new branch 'ft/new-branch-from-commit'
```

7. Branch Merging:

Now that you've completed work on your feature branch, it's time to integrate it into main.
Challenge: Merge the ft/new-branch-from-commit branch into the main branch. Address any merge conflicts that might arise.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git merge ft/new-branch-from-commit
Already up to date.
```

8. Branch Rebasing:

Rebasing is another method to integrate changes from a feature branch. It rewrites your branch history by incorporating its commits on top of the latest commit in the target branch (main in our case).
Challenge: Try rebasing the ft/new-branch-from-commit branch onto the main branch. Remember, rebasing rewrites history, so use it with caution, especially in shared repositories. learn more about rebasing here.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout ft/new-branch-from-commit
Switched to branch 'ft/new-branch-from-commit'

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-branch-from-commit)
$ git rebase main
Successfully rebased and updated refs/heads/ft/new-branch-from-commit.
```

9. Renaming Branches:

Branch names can sometimes evolve. Let's rename ft/new-branch-from-commit to a more descriptive name.
Challenge: Use git branch -m ft/new-branch-from-commit ft/improved-branch-name to rename your branch.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-branch-from-commit)
$ git branch -m ft/new-branch-from-commit ft/improved-branch-name

```

10. Checking Out Detached HEAD:

In specific situations, you might need to detach HEAD from your current branch. Research git checkout <commit-hash> (replace with the desired commit hash) to understand this concept.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout 4371ffe
Note: switching to '4371ffe'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 4371ffe Implemented test 5
```

## Part 3: Advanced Workflows

Stashing Changes:

1.Imagine you're working on some changes in the main branch but need to attend to something urgent. You don't want to lose your uncommitted work.
Challenge: Stash your current changes in the main branch using git stash.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git stash
No local changes to save
```
2.Retrieving Stashed Changes:

Later, when you're ready to resume working on those stashed changes, you can retrieve them.
Challenge: Apply the most recent stash back onto the main branch using git stash pop.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git stash pop
No stash entries found.
```

3.Branch Merging Conflicts (Continued):

Merge conflicts can arise when the same lines of code are modified in both branches being merged.
Challenge: Simulate a merge conflict scenario (you can create conflicting changes in a file on both main and a new feature branch). Then, try merging again and resolve the conflicts manually using your text editor.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ vi readme.txt

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git add .

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git commit -m "New conflict"
[main 5ccbe1a] New conflict
 1 file changed, 1 insertion(+), 1 deletion(-)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git switch ft/new-feature
Switched to branch 'ft/new-feature'

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$ vi readme.txt

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$ git add .
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$ git commit -m "New edit on branch"
[ft/new-feature feb24f7] New edit on branch
 1 file changed, 1 insertion(+), 1 deletion(-)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (ft/new-feature)
$ git switch main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 4 commits.
  (use "git push" to publish your local commits)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git merge ft/new-feature
Auto-merging readme.txt
CONFLICT (content): Merge conflict in readme.txt
Automatic merge failed; fix conflicts and then commit the result.

```
4.Resolving Merge Conflicts with a Merge Tool:

Explore using a merge tool like git mergetool to help you visualize and resolve merge conflicts more efficiently.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|MERGING)
$ git merge ft/new-feature
error: Merging is not possible because you have unmerged files.
hint: Fix them up in the work tree, and then use 'git add/rm <file>'
hint: as appropriate to mark resolution and make a commit.
fatal: Exiting because of an unresolved conflict.

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|MERGING)
$ git mergetool

This message is displayed because 'merge.tool' is not configured.
See 'git mergetool --tool-help' or 'git help config' for more details.
'git mergetool' will now attempt to use one of the following tools:
opendiff kdiff3 tkdiff xxdiff meld tortoisemerge gvimdiff diffuse diffmerge ecmerge p4merge araxis bc codecompare smerge emerge vimdiff nvimdiff
Merging:
readme.txt

Normal merge conflict for 'readme.txt':
  {local}: modified file
  {remote}: modified file
Hit return to start merge resolution tool (vimdiff):
4 files to edit

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|MERGING)
$ git add .

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|MERGING)
$ git commit -m "Conflict resolved"
[main 1b9e812] Conflict resolved

```

5.Understanding Detached HEAD State:

Detached HEAD refers to a state where your working directory is not associated with any specific branch. Research the implications and how to recover from this state using commands like git checkout <branch-name>.

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git checkout 7c1f0ac
Note: switching to '7c1f0ac'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 7c1f0ac Edit on main

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced ((7c1f0ac...))
$ git checkout main
Previous HEAD position was 7c1f0ac Edit on main
Switched to branch 'main'
Your branch is ahead of 'origin/main' by 6 commits.
  (use "git push" to publish your local commits)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$
```

6.Ignoring Files/Directories:

You might have files or directories you don't want to track in Git. Create a .gitignore file to specify these exclusions.
Challenge: Add a pattern like /tmp to your .gitignore file to exclude all temporary files and directories from version control. more about ignoring files here

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 6/15)
$ vi .gitignore

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 6/15)
$ git add .
warning: in the working copy of '.gitignore', LF will be replaced by CRLF the next time Git touches it

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 6/15)
$ git commit -m "Git ignore"
[detached HEAD bf15ecd] Git ignore
 1 file changed, 1 insertion(+)
 create mode 100644 .gitignore
```

7.Working with Tags:

Tags act like bookmarks in your Git history. Create a tag to mark a specific point in your development.
Challenge: Use git tag v1.0 to create a tag named v1.0 on the current commit in your main branch. git tags

```
Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 6/15)
$ git tag v1.0
```

8.Listing and Deleting Tags:

Challenge: Use git tag to list all existing tags. Then, use git tag -d <tag-name> to delete a specific tag (replace <tag-name> with the actual tag you want to remove).

```
$ git tag
v1.0

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main|REBASE 6/15)
$ git tag -d v1.0
Deleted tag 'v1.0' (was bf15ecd)

```

9.Pushing Local Work to Remote Repositories:

Once you're happy with your local changes and branches, it's time to share them with others.
Challenge: Assuming you've set up a remote repository on a Git hosting platform (like GitHub), push the changes with the actual branch you want to push to push your local branch to the remote repository.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git push
Enumerating objects: 21, done.
Counting objects: 100% (21/21), done.
Delta compression using up to 4 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (19/19), 1.60 KiB | 234.00 KiB/s, done.
Total 19 (delta 8), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (8/8), completed with 1 local object.
To https://github.com/Ntwalii/Git-exercises-advanced.git
   724b9b8..0fc18ca  main -> main

```

10.Pulling Changes from Remote Repositories:

Collaboration often involves pulling changes from the remote repository made by others.
Challenge: Navigate to Github and make some changes inside your README file that you created on your main branch and in your local environment use git pull origin <branch-name> (replace <branch-name> with the actual branch you want to pull) to fetch changes from the remote repository's main branch and merge them into your local main branch. Address any merge conflicts that might arise.

```

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git pull origin main
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 3.36 KiB | 215.00 KiB/s, done.
From https://github.com/Ntwalii/Git-exercises-advanced
 * branch            main       -> FETCH_HEAD
   0fc18ca..73373a4  main       -> origin/main
Updating 0fc18ca..73373a4
Fast-forward
 README.md | 214 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 214 insertions(+)

Ntwali@DESKTOP-CP6B3NG MINGW64 ~/Desktop/Personal/The Gym/Git-exercises-advanced (main)
$ git merge
Already up to date.
```
