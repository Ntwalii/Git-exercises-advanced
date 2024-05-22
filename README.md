# GIT ADVANCED EXERCISES

Part 1: Refining Git History (10 Challenges)

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

