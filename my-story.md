

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
