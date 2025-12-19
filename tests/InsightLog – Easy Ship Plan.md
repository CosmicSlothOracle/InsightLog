# InsightLog – Easy Ship Plan

## Team Workflow & Best Practice Examples (Beginner-Friendly Guide)

**Repository:** <https://github.com/CosmicSlothOracle/InsightLog>

**Goal:** Ship two very simple fixes while demonstrating a clean, professional Git workflow (branches, pull requests, reviews, and reporting). This guide explains every concept and command in detail so beginners can learn effectively.

---

## 1. What We Ship (Minimal Scope)

We're fixing two small but important issues that affect new contributors:

1. **Bug Fix 1:** README / Getting Started is fork-correct (clone URL, directory name, run command)
2. **Bug Fix 2:** License information is consistent between README and LICENSE file
3. **Optional bonus:** Add a small CONTRIBUTING.md documenting team workflow and commit conventions

### Definition of Done

Before we consider this complete, we must ensure:

1. ✅ Each fix is visible and reviewed via pull request
2. ✅ Pull requests explain what changed and why
3. ✅ No direct commits to main (we always use branches)
4. ✅ New contributors can run the project within 3 minutes

---

## 2. Understanding the Two Easy Bugs

### Bug 1 – README Getting Started is not fork-correct

**What is a "fork"?**
A fork is your own copy of someone else's repository. When you fork a project on GitHub, you create an independent copy that you can modify. The original repository is called the "upstream" repository.

**The Problem:**

- **Symptom:** The README file contains clone or run instructions that reference the wrong repository or directory name
- **Why this matters:** When someone clones your fork, they need exact commands that work. If the README says to clone from a different repository, new contributors get confused
- **Fix:** Update README so all commands exactly match this fork's repository URL and directory structure

**Acceptance Criteria:**
A fresh clone works without guessing. Someone should be able to:

1. Copy the clone command from README
2. Paste it into their terminal
3. Follow the rest of the README steps exactly
4. Everything works on the first try

**Mini Test (How to verify the fix works):**

```bash
# Step 1: Clone the repository
git clone https://github.com/CosmicSlothOracle/InsightLog

# Step 2: Navigate into the directory
cd InsightLog

# Step 3: Follow README steps exactly
# (Run whatever commands the README says to run)
```

If all steps work without modification, the bug is fixed!

---

### Bug 2 – License mismatch

**What is a license?**
A license tells people what they can and cannot do with your code. It's a legal document that protects both you and users of your software.

**The Problem:**

- **Symptom:** README lists a different license than what's in the LICENSE file
- **Why this matters:** Legal confusion. If someone wants to use your code, they need to know the actual license terms. Having conflicting information is unprofessional and can cause legal issues
- **Fix:** Treat LICENSE file as the source of truth and align README to match it exactly

**Acceptance Criteria:**
No contradictions remain. Both files should say the same thing about the license.

---

## 3. Roles & Task Distribution

**Laurin:** Bug 2 – License consistency + mini CONTRIBUTING.md (branch: `docs/license-consistency`)

**Michelle-Joy:** Bug 1 – README Getting Started fix (branch: `docs/readme-getting-started`)

---

## 4. Professional Report Workflow (Explained for Beginners)

### What is an Issue?

An **issue** is like a bug report or task description on GitHub. It's a way to:

- Document problems that need fixing
- Discuss solutions before coding
- Track progress on tasks
- Link code changes (pull requests) to the problem they solve

### Issue Example

**Title:** `README Getting Started cannot be executed 1:1 in fork`

**Description:**

```
Onboarding steps do not match the fork and confuse new contributors.
When someone clones this repository and follows the README instructions,
they encounter errors because the commands reference the wrong repository
or directory names.

**Steps to reproduce:**
1. Clone the repository
2. Follow README getting started section
3. Commands fail or reference wrong paths

**Expected behavior:**
All commands in README should work exactly as written for this fork.

**Acceptance criteria:**
Setup works in under 3 minutes for a new contributor.
```

---

### What is a Pull Request (PR)?

A **pull request** (PR) is a way to propose changes to a repository. Here's how it works:

1. You create a branch (a separate copy of the code)
2. You make changes on that branch
3. You push the branch to GitHub
4. You open a "pull request" asking to merge your changes into the main branch
5. Others review your code
6. If approved, your changes get merged into the main codebase

**Why use pull requests?**

- Code review: Others can check your work before it goes live
- Discussion: Team can discuss changes before merging
- Testing: Changes can be tested before merging
- History: Every change is documented and linked to discussions

### Pull Request Example

**Title:** `docs(readme): fix getting started commands`

**Description:**

```
## Why this change is needed
New contributors could not reproduce the setup because the README
contained commands referencing the upstream repository instead of this fork.

## What changed
- Updated clone URL to match this fork: `https://github.com/CosmicSlothOracle/InsightLog`
- Fixed directory name in commands (was `insightlog`, now `InsightLog`)
- Verified all commands work end-to-end

## How tested
1. Created a fresh clone in a temporary directory
2. Followed README steps exactly as written
3. All commands executed successfully
4. Project runs without errors

## Related
Fixes #[issue-number] (if you created an issue first)
```

---

### What is Code Review?

**Code review** is when other team members look at your changes before they're merged. They check for:

- Bugs or errors
- Code quality and style
- Whether the solution is correct
- Suggestions for improvement

### Review Comment Examples

**1. Nit (Minor suggestion, not blocking):**

> "Nit: Could Windows and macOS steps be separated for readability? It might be clearer to have separate sections for each OS."

**2. Suggestion (Helpful improvement, optional):**

> "Suggestion: Add virtual environment creation for reproducibility. This would help ensure everyone uses the same Python version."

**3. Blocking (Must fix before merging):**

> "Blocking: Please re-test with a fresh clone. I tried the steps and got an error on step 3. Can you verify this works?"

**Types of review comments:**

- **Approval:** ✅ "Looks good, ready to merge!"
- **Request changes:** ❌ "Please fix these issues before merging"
- **Comment:** 💬 "Just a thought, not required"

---

## 5. Commit Messages (How to Write Good Ones)

### What is a Commit?

A **commit** is a snapshot of your changes at a specific point in time. Think of it like saving your work, but with a message describing what you changed.

### Commit Message Examples

```
docs(readme): fix clone and run steps for fork
```

```
docs(license): align README license with LICENSE file
```

```
chore: add CONTRIBUTING with team workflow
```

### Understanding Commit Message Format

**Format:** `type(scope): description`

- **Type:** What kind of change is this?

  - `docs` = documentation changes
  - `fix` = bug fix
  - `feat` = new feature
  - `chore` = maintenance tasks
  - `refactor` = code restructuring
  - `test` = adding tests

- **Scope (optional):** What part of the codebase?

  - `readme` = README file
  - `license` = license files
  - `api` = API code
  - etc.

- **Description:** What did you do? (imperative mood)

### Commit Rules

1. **Imperative mood** (add, fix, align) - Write as if completing the sentence "This commit will..."

   - ✅ Good: "fix getting started commands"
   - ❌ Bad: "fixed getting started commands" or "fixes getting started commands"

2. **First line ≤ 72 characters** - This keeps commit logs readable in terminals

3. **Explain what was broken and why** (if it's a bug fix)
   - ✅ Good: "fix clone URL pointing to upstream instead of fork"
   - ❌ Bad: "update README"

---

## 6. Git Command Cheat Sheet (Explained Step-by-Step)

### Prerequisites: Understanding Git Basics

**What is Git?**
Git is a version control system. It tracks changes to your files over time, like a time machine for your code.

**Key Git Concepts:**

- **Repository (repo):** A folder that Git is tracking
- **Branch:** A separate line of development (like a parallel universe for your code)
- **Commit:** A saved snapshot of changes
- **Remote:** A copy of your repository on a server (like GitHub)
- **Origin:** The default name for your remote repository

---

### Step-by-Step Git Workflow

#### Step 1: Create a Feature Branch

**Command:**

```bash
git checkout -b docs/readme-getting-started
```

**What this does:**

- `git checkout` = Switch to a different branch
- `-b` = Create a new branch (if it doesn't exist)
- `docs/readme-getting-started` = The name of your new branch

**Why create a branch?**

- Keeps main branch stable and working
- Allows multiple people to work on different things simultaneously
- Easy to discard changes if something goes wrong
- Required for pull requests

**Branch naming convention:**

- `docs/` = documentation changes
- `fix/` = bug fixes
- `feat/` = new features
- `chore/` = maintenance

**Where to run this:**
In your terminal, navigate to the repository folder first:

```bash
cd C:\Users\skank\Cyber_Project_Forked_Cloned\InsightLog
git checkout -b docs/readme-getting-started
```

---

#### Step 2: Make Your Changes

Edit the files you need to fix (README.md, LICENSE, etc.) using your text editor.

**How to check what you changed:**

```bash
git status
```

This shows:

- Which files you modified
- Which files are new
- Which files are staged (ready to commit)

**How to see the actual changes:**

```bash
git diff
```

This shows line-by-line what changed (red = removed, green = added).

---

#### Step 3: Stage Your Changes

**Command:**

```bash
git add README.md
```

**What this does:**

- "Stages" the file, marking it as ready to be committed
- Think of it like putting items in a shopping cart before checkout

**Why stage files?**

- You can commit some files but not others
- You can review what you're about to commit
- Git requires staging before committing

**Stage multiple files:**

```bash
git add README.md LICENSE
```

**Stage all changed files:**

```bash
git add .
```

(Use carefully - make sure you want to commit everything!)

**Where to run this:**
Same directory as before (your repository folder).

---

#### Step 4: Commit Your Changes

**Command:**

```bash
git commit -m "docs(readme): fix getting started commands"
```

**What this does:**

- Creates a commit (saves your changes) with the message you provided
- `-m` = message flag (allows you to write the message directly in the command)

**Why commit?**

- Saves your work at this point in time
- Creates a history of what changed and why
- Required before you can push to GitHub

**Alternative (longer message):**

```bash
git commit -m "docs(readme): fix getting started commands

- Updated clone URL to match fork
- Fixed directory name in commands
- Verified all steps work end-to-end"
```

**Where to run this:**
Same directory as before.

---

#### Step 5: Push Your Branch to GitHub

**Command:**

```bash
git push -u origin docs/readme-getting-started
```

**What this does:**

- `git push` = Upload your commits to GitHub
- `-u` = Set upstream (tracks this branch on GitHub, so future pushes are easier)
- `origin` = The name of your remote repository (GitHub)
- `docs/readme-getting-started` = The branch name to push

**Why push?**

- Makes your changes visible on GitHub
- Required to create a pull request
- Backs up your work to the cloud

**First time pushing a branch:**
Always use `-u` the first time. After that, you can just use:

```bash
git push
```

**Where to run this:**
Same directory as before.

**What happens next:**
GitHub will show you a link to create a pull request, or you can go to the repository page and GitHub will suggest creating one.

---

### Additional Useful Git Commands

**See your commit history:**

```bash
git log
```

Press `q` to exit the log view.

**See which branch you're on:**

```bash
git branch
```

The current branch has an asterisk (\*) next to it.

**Switch back to main branch:**

```bash
git checkout main
```

**Update your local main branch with latest changes:**

```bash
git checkout main
git pull origin main
```

**Delete a local branch (after merging):**

```bash
git branch -d docs/readme-getting-started
```

---

## 7. Mini Exercise (10 Minutes - Step by Step)

Follow these steps to complete your first contribution:

### Step 1: Create Issue or Describe Problem in PR

**Option A: Create an issue on GitHub**

1. Go to your repository on GitHub
2. Click "Issues" tab
3. Click "New Issue"
4. Fill in title and description
5. Click "Submit new issue"

**Option B: Describe in PR directly**
You can skip creating an issue and just describe the problem in your pull request description.

---

### Step 2: Create Feature Branch

**In your terminal:**

```bash
# Make sure you're in the repository folder
cd C:\Users\skank\Cyber_Project_Forked_Cloned\InsightLog

# Make sure you're on main and it's up to date
git checkout main
git pull origin main

# Create your feature branch
git checkout -b docs/readme-getting-started
# (or docs/license-consistency for the other task)
```

---

### Step 3: Apply Fix and Test Locally

1. **Edit the file(s)** you need to fix (README.md, LICENSE, etc.)
2. **Test your changes:**
   - For README: Try following the instructions yourself
   - For LICENSE: Read both files and verify they match
3. **Verify your changes:**

   ```bash
   git status    # See what files changed
   git diff      # See the actual changes
   ```

---

### Step 4: Commit, Push, and Open PR

**Commit your changes:**

```bash
git add README.md
git commit -m "docs(readme): fix getting started commands"
```

**Push to GitHub:**

```bash
git push -u origin docs/readme-getting-started
```

**Create Pull Request:**

1. Go to your repository on GitHub
2. You should see a banner saying "Compare & pull request" - click it
3. Or go to "Pull requests" tab → "New pull request"
4. Select your branch
5. Fill in title and description
6. Click "Create pull request"

---

### Step 5: Review, Squash-Merge, Test Main

**What is Squash-Merge?**
When you merge a pull request, you can choose how to combine the commits:

- **Merge commit:** Keeps all individual commits from the branch
- **Squash and merge:** Combines all commits into one clean commit
- **Rebase and merge:** Replays commits on top of main (advanced)

For this exercise, use **Squash and merge** to keep history clean.

**After merging:**

1. **Update your local main:**

   ```bash
   git checkout main
   git pull origin main
   ```

2. **Test that everything works:**

   - Verify your changes are in main
   - Test the project still works
   - Delete your feature branch (optional):

     ```bash
     git branch -d docs/readme-getting-started
     ```

---

## 8. Report Summary Text (Reusable Template)

When documenting what was accomplished, you can use this template:

```
We fixed two low-risk onboarding issues: a fork-correct README and consistent
license information. All changes were implemented using feature branches,
pull requests, and peer review. The main challenge was ensuring consistency
between upstream and fork, solved via fresh-clone testing.

**Changes made:**
- Updated README clone URL and directory references to match fork
- Aligned README license statement with LICENSE file
- Added CONTRIBUTING.md with team workflow guidelines

**Process followed:**
- Each fix was developed on a separate feature branch
- Changes were reviewed via pull requests before merging
- All fixes tested with fresh clones to verify correctness
- No direct commits to main branch

**Outcome:**
New contributors can now clone and run the project within 3 minutes without
encountering errors or confusion.
```

---

## 9. Glossary of Terms (Quick Reference)

- **Branch:** A separate line of development. Like a parallel universe for your code.
- **Clone:** Download a copy of a repository to your computer.
- **Commit:** A saved snapshot of your changes with a message describing what changed.
- **Fork:** Your own copy of someone else's repository on GitHub.
- **Issue:** A bug report or task description on GitHub.
- **Main/Master:** The primary branch of a repository (usually the "production" version).
- **Merge:** Combining changes from one branch into another.
- **Pull Request (PR):** A proposal to merge your changes into the main branch.
- **Push:** Upload your commits to GitHub.
- **Remote:** A copy of your repository on a server (like GitHub).
- **Repository (Repo):** A folder that Git is tracking for version control.
- **Stage:** Mark files as ready to be committed (using `git add`).
- **Upstream:** The original repository that you forked from.

---

## 10. Common Mistakes to Avoid

1. **Committing directly to main:** Always create a branch first!
2. **Vague commit messages:** Be specific about what changed and why.
3. **Not testing changes:** Always test your fixes before committing.
4. **Forgetting to pull latest changes:** Update main before creating a new branch.
5. **Pushing without committing:** You must commit before you can push.
6. **Not staging files:** Use `git add` before `git commit`.

---

## Final Notes

This workflow might seem like extra steps, but it's the professional standard because it:

- Prevents breaking the main codebase
- Enables code review and collaboration
- Creates a clear history of what changed and why
- Makes it easy to undo mistakes
- Allows multiple people to work simultaneously

Remember: **Practice makes perfect!** The first time might feel slow, but it becomes natural quickly.

Good luck with your contributions! 🚀
