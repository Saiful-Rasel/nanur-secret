

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


## Chapter 3: The Eid Special

### Task A: Create and Switch Branch

**Commands used:**
```bash
git branch eid-special
git checkout eid-special
```

**What I learned:** I created a separate branch named `eid-special` to work on Eid recipes without immediately changing the `main` branch.

### Task B: Add Two Recipes in Separate Commits

I created `biryani.md` and `shemai.md` on the `eid-special` branch and committed them separately.

```bash
git add biryani.md
git commit -m "feat: add Eid biryani recipe"

git add shemai.md
git commit -m "feat: add shemai dessert recipe"
```

**What I learned:** Separate commits make it easier to track and review individual changes.

### Task C: Merge into Main

I switched back to `main` and checked the files before merging. The new recipes were available on `eid-special`, but were not initially present on `main`.

```bash
git checkout main
git merge eid-special
git log --oneline --graph --all
```

After merging, both recipes became available on `main`.

### Challenge: Create and Resolve a Merge Conflict

I created a `conflict-demo` branch and changed the same spice line in `biryani.md` differently on the two branches. When I merged `conflict-demo` into `main`, Git reported a merge conflict.

I opened the file, reviewed both versions, removed the conflict markers, and kept the desired final content. Then I staged and committed the resolution.

```bash
git add biryani.md
git commit -m "fix: resolve biryani spice merge conflict"
```

**What I learned:** A merge conflict occurs when Git cannot automatically combine conflicting changes. I must review the changes, choose or combine the correct content, remove conflict markers, and commit the resolution.




## Chapter 4: Mitu Joins In

### Task A: Create and Push GitHub Repository
I created a GitHub repository, connected my local repository using `git remote add origin`, and pushed my commits using `git push`.

### Task B: Mitu Clones and Adds a Recipe
I cloned the repository into another folder to simulate Mitu working from Chattogram. I created `chittagong-mezban.md`, committed the file, and pushed it to GitHub.

Commands used:
- `git clone <repository-url>`
- `git add chittagong-mezban.md`
- `git commit -m "feat: add Chittagong mezban recipe"`
- `git push`

### Task C: Fetch and Merge
Back in my original repository, I downloaded remote updates and merged them into my local main branch.

Commands used:
- `git fetch origin`
- `git merge origin/main`

### Task D: Pull New Changes
Mitu added serving notes to the recipe, committed the changes, and pushed them to GitHub. I then used `git pull` in my original repository to bring those changes into my local branch.

### What I Learned
- `git clone` creates a local copy of a remote repository.
- `git fetch origin` downloads remote updates without integrating them into the current local branch.
- `git merge origin/main` integrates the fetched changes into my local branch.
- `git pull` normally fetches remote updates and then integrates them using merge or rebase.
- `git push` sends my local commits to the remote repository.
- Fetch and merge give me separate steps to inspect and integrate changes, while pull combines fetching and integration into one command.

and main ans is git fetch and git merge are two separate commands. git fetch origin downloads the latest commits from the remote repository without integrating them into the current local branch. Then, git merge origin/main integrates those changes into the local main branch.
git pull normally performs both steps in one command: it fetches remote changes and then integrates them using merge or rebase, depending on the configuration.
In short: fetch + merge gives you more control because you can inspect changes between the two steps, while pull is a convenient way to fetch and integrate changes in one command. Neither command automatically pushes your local changes to GitHub; use git push for that.



## Chapter 5 — Half-Cooked Halua and Time Travel

### Task A: Save Halua Work with Git Stash

While I was preparing the halua recipe, Nanu reminded me that I had forgotten to add cardamom to the biryani. I used `git stash` to temporarily save my unfinished halua work so I could fix the biryani first.

**Commands used:**

```bash
git status
git stash push -m "WIP: half-cooked halua"
git switch eid-special
nano biryani.md
git add biryani.md
git commit -m "fix: add cardamom to biryani recipe"
git switch chapter-5-stash
git stash list
git stash pop
git status
```

**What I learned:**

The `git stash` command temporarily saves unfinished changes so I can switch tasks without making an incomplete commit. After fixing and committing the biryani recipe, I used `git stash pop` to restore my halua work.

### Task B: Organize Recipes and Delete an Old Recipe

I organized the recipe files into a `recipes/` directory using `git mv`. I also removed an old recipe using `git rm` and inspected the commit history.

**Commands used:**

```bash
mkdir -p recipes
git mv bhapa-pitha.md recipes/bhapa-pitha.md
git mv biryani.md recipes/biryani.md
git mv shemai.md recipes/shemai.md
git mv chittagong-mezban.md recipes/chittagong-mezban.md
git mv halua.md recipes/halua.md
git rm old-recipe.md
git status
git add -A
git commit -m "refactor: organize recipes into folders"
git log --stat -M
```

**What I learned:**

- `git mv` moves or renames files and stages the changes.
- `git rm` removes a tracked file and stages its deletion.
- `git log --stat -M` displays commit history, file-change statistics, and helps Git detect renamed files.

### Task C: Inspect a Commit with Git Show

I used `git log --oneline` to find a commit SHA and then inspected that commit using `git show`.

**Commands used:**

```bash
git log --oneline
git show 4c41f75
```

**What I learned:**

The `git show` command displays information about a specific commit, including its commit message and the changes introduced by it. This helps me understand how my recipe book changed over time.

### Task D: Experiment with Git Reset Hard on a Test Branch

I created a separate test branch named `reset-test` to experiment with `git reset --hard` without affecting `main`.

**Commands used:**

```bash
git switch -c reset-test
git log --oneline
git status
git reset --hard 4c41f75
git reset --hard 3e647ef
git log --oneline -5
git status
git reflog -5
```

First, I reset to `4c41f75`, which was already the current commit. This did not move the branch backward, but it discarded the staged changes I had made to `bazar-list.txt`.

Then I reset to the older commit `3e647ef`. The `reset-test` branch moved back to that commit, and the working directory returned to the state recorded in that older commit. The later recipe-organization commit was no longer part of the current history of `reset-test`, although another branch could still reference it.

**What I learned:**

The `git reset --hard` command moves the current branch to a specified commit and resets both the staging area and working directory. It can discard staged and unstaged changes to tracked files. I performed this experiment on `reset-test`, not on `main`.

### Question: Why Are Rebase and Reset Hard Dangerous on a Shared Branch?

**Rebase:** Rebase rewrites commit history and can create new commit IDs. If other developers have already based their work on the original commits, this can cause confusing history and integration problems.

**Reset hard:** `git reset --hard` moves the current branch to another commit and resets the staging area and working directory. It can discard uncommitted tracked-file changes and move later commits out of the branch's current history. On a shared branch, this can disrupt other developers who depend on those commits.

**Safer approach:** Avoid rewriting shared history that other people depend on. When an existing shared commit needs to be undone, `git revert` is often safer because it creates a new commit that reverses the earlier change instead of rewriting history.

### What I Learned in Chapter 5

This chapter taught me how to pause unfinished work with `git stash`, organize and delete files with Git, inspect commits with `git show`, and move through commit history using `git reset --hard`. I also learned why destructive Git commands must be used carefully, especially on shared branches.
