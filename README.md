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

```

4. Splitting a Commit:

Imagine "Create third and fourth files" describes too much at once. Separate them for better tracking with two different commit messages: "Create Third File" and "Create fourth file".
Challenge: Leverage git reset to separate the files into individual commits with distinct messages. learn more about splitting commits here

```

```
