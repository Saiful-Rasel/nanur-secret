

## Chapter 1: The First Recipe

### Task A: Setting Up the Recipe Book

Nanu asked me to preserve her family recipes before the old handwritten book became damaged. I decided to create a Git repository named `nanur-secret` to track every change.

First, I configured my Git username and email:

```bash
git config --global user.name "Saiful-Rasel"
git config --global user.email "saifulrasel737rfgmail.com"
```

Then, I created the project folder and initialized Git:

```bash
mkdir nanur-secret
cd nanur-secret
git init
```

Finally, I verified the repository status
**What happened:** Git initialized a new repository inside `nanur-secret`. Now I can track recipe changes, create commits, and preserve the history of Nanu's recipe boo


### Chapter 1 — Task B: The First Recipe

I created `bhapa-pitha.md` and wrote Nanu's bhapa pitha recipe in it. First, I ran `git status` and found that the file was untracked. Then I ran `git add bhapa-pitha.md` to stage the file. After checking `git status` again, I confirmed that the file was ready to be committed.


### Task C: Correcting the Bhapa Pitha Recipe

Nanu corrected the recipe and told me to use one and a half cups of gur instead of two cups. I edited `bhapa-pitha.md` and ran `git diff` to see the changes that were not staged.

Next, I ran `git diff --staged` to check the changes in the staging area. Before running `git add`, the new correction did not appear in the staged diff. After running `git add bhapa-pitha.md`, the change appeared in `git diff --staged`.

**Difference:** `git diff` shows unstaged changes, while `git diff --staged` shows staged changes that are ready to be committed.


### Task E: Unstage an Accidentally Staged File

**Command used:**

```bash
git add bazar-list.txt
git status
git restore --staged bazar-list.txt
git status
```

**What happened:**

I accidentally staged `bazar-list.txt` using `git add bazar-list.txt`. I then used `git restore --staged bazar-list.txt` to unstage the file without deleting it. After running `git status`, the file appeared under `Untracked files`, confirming that it was no longer staged and still existed in my working directory.

**What I learned:**

I learned that `git restore --staged <filename>` unstages a file while preserving its contents. The command `git reset -- <filename>` can also be used for the same purpose. Neither command deletes the file from the working directory in this situation.
