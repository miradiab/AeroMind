# AeroMind Git Workflow

This guide explains how our team works with Git and GitHub using the terminal.

It is written for beginners.

---

## 1. Important Git Terms

### Repository

A repository, or repo, is the project folder tracked by Git.

For us, the repository is:

```text
AeroMind
```

### Main Branch

`main` is the stable shared version of the project.

We should not normally make changes directly on `main`.

### Branch

A branch is a separate workspace for your changes.

Example:

```text
data/asrs-profiling
```

### Commit

A commit is a saved checkpoint of your work.

Example:

```text
data: add ASRS profiling
```

### Pull

`git pull` downloads the latest changes from GitHub.

### Push

`git push` uploads your commits to GitHub.

### Pull Request

A Pull Request, or PR, asks the team to review your branch and merge it into `main`.

---

## 2. First-Time Setup

You only clone the repository once.

Open Git Bash and go to the folder where you want to store the project.

Run:

```bash
git clone https://github.com/miradjab/AeroMind.git
```

Enter the project:

```bash
cd AeroMind
```

Check that Git is working:

```bash
git status
```

You should see something similar to:

```text
On branch main
Your branch is up to date with 'origin/main'.
```

---

## 3. Starting a New Task

Before starting a new task, switch to `main`:

```bash
git switch main
```

Download the latest team changes:

```bash
git pull
```

Then create a new branch for your task:

```bash
git switch -c data/asrs-profiling
```

Other examples:

```bash
git switch -c data/cmaps-profiling
git switch -c data/faa-sdr-profiling
git switch -c docs/update-data-sources
```

Now you can work without directly changing `main`.

---

## 4. Work Normally

Edit your notebooks, reports, documentation, or code using your normal editor.

Examples:

```text
notebooks/data_profiling/asrs_profiling.ipynb
reports/profiling/asrs_profile.md
docs/data_sources.md
```

You do not need to run a Git command after every small edit.

---

## 5. Check What Changed

Use:

```bash
git status
```

This tells you:

- which files changed
- which files are new
- which files were deleted
- which branch you are currently on

Use `git status` often.

---

## 6. Add Your Changes

When you are ready to save your work to Git:

```bash
git add .
```

Then check again:

```bash
git status
```

Your files should now appear under:

```text
Changes to be committed
```

---

## 7. Commit Your Work

Create a commit:

```bash
git commit -m "data: add ASRS profiling"
```

Good commit messages:

```text
data: add C-MAPSS profiling
data: clean ASRS extraction
docs: update data source documentation
fix: handle missing report IDs
```

Avoid unclear commit messages such as:

```text
update
stuff
changes
final
final2
```

---

## 8. Push Your Branch

The first time you push a new branch:

```bash
git push -u origin data/asrs-profiling
```

Replace `data/asrs-profiling` with your actual branch name.

After the first push, future pushes from the same branch can usually be:

```bash
git push
```

---

## 9. Create a Pull Request

After pushing your branch:

1. Open the AeroMind repository on GitHub.
2. GitHub will usually show your recently pushed branch.
3. Click **Compare & pull request**.
4. Make sure the base branch is `main`.
5. Make sure the compare branch is your branch.
6. Write a short description of what you changed.
7. Create the Pull Request.
8. Have another teammate review it before merging.

---

## 10. After Your Pull Request Is Merged

Return to Git Bash.

Switch back to `main`:

```bash
git switch main
```

Download the newly merged changes:

```bash
git pull
```

Delete your old local branch:

```bash
git branch -d data/asrs-profiling
```

Replace the branch name with your own.

Then create a new branch when you start your next task.

---

## 11. Useful Terminal and Git Commands

### Show your current folder

```bash
pwd
```

### List files and folders

```bash
ls
```

### See your branches

```bash
git branch
```

The current branch will have a `*` next to it.

Example:

```text
  main
* data/asrs-profiling
```

### Check your Git status

```bash
git status
```

### Download the latest changes

```bash
git pull
```

### Upload your commits

```bash
git push
```

### View recent commits

```bash
git log --oneline
```

Press `q` to exit the log view.

---

## 12. Branch Naming

Use branch names that describe the work being done.

Recommended patterns:

```text
data/<task>
docs/<task>
fix/<task>
feature/<task>
```

Examples:

```text
data/asrs-profiling
data/cmaps-cleaning
docs/update-readme
fix/asrs-parser
feature/text-extraction
```

Avoid names such as:

```text
mybranch
test
test2
final
mira-branch
```

Branches should describe the task, not the person.

---

## 13. Important Team Rules

### Do not work directly on `main`

Create a branch before starting your task.

### Always pull before starting new work

Run:

```bash
git switch main
git pull
```

Then create your branch.

This makes sure your new branch starts from the latest project version.

### Do not upload large files

Do not commit:

- large PDFs
- full raw datasets
- ZIP archives
- trained model files
- temporary files
- API keys
- passwords
- `.env` files

Small dataset samples may be stored in:

```text
data/samples/
```

### Never commit secrets

Do not put passwords or API keys directly inside notebooks or Python files.

---

## 14. If Something Goes Wrong

Do not start trying random Git commands.

First run:

```bash
git status
```

Read the message Git gives you.

If you are unsure, copy the output and ask the team.

Be especially careful with commands such as:

```text
git reset --hard
git clean -fd
git push --force
```

These commands can delete work or overwrite Git history.

Do not use them unless you understand exactly what they do.

---

## 15. Merge Conflicts

If Git tells you there is a merge conflict, do not randomly delete or overwrite files.

First run:

```bash
git status
```

Git will tell you which files are affected.

If you are unsure how to resolve the conflict, ask the team before continuing.

---

## 16. Daily Cheat Sheet

### Start a task

```bash
git switch main
git pull
git switch -c data/my-task
```

### After doing your work

```bash
git status
git add .
git commit -m "data: describe what you changed"
git push -u origin data/my-task
```

Then create a Pull Request on GitHub.

### After the Pull Request is merged

```bash
git switch main
git pull
git branch -d data/my-task
```

---

## 17. Commands to Learn First

You do not need to learn all of Git immediately.

Focus on these commands first:

```bash
git status
git switch
git pull
git add
git commit
git push
```

Once these become comfortable, we can learn more advanced Git features when the project actually needs them.