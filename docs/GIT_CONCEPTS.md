# Git Concepts: The "Why" Behind Our Workflow

Welcome! If you're new to Git or collaborative development, some of the steps in our `CONTRIBUTING.md` might seem complex. This guide explains the "why" behind our process.

---

### 🤔 Why do we "fork" the repository? Can't we all just clone the original?

This is a great question about **permissions and project safety**.

The main repository (called `upstream`) is locked down. Only a few trusted maintainers have permission to write directly to it. This prevents accidental or malicious changes to the official project.

A **fork** is your personal copy of the repository on GitHub. You have full write access to your fork.

*   **The Workflow:** You push your changes to **your fork**, and then you open a **Pull Request (PR)**. A PR is a formal request to the project maintainers, asking them to review your work and merge it into the official repository.

This model allows anyone to contribute without giving them risky permissions on the main project.

---

### 🤔 What are branches? Why do I need to create a new one for every task?

Think of a branch as an **independent workspace** or a parallel timeline. When you create a branch, you create an isolated environment to work on your new feature or bug fix without affecting the stable `main` branch.

**Why not just work directly on your `main` branch?**

1.  **Isolation:** Your `main` branch should always be a clean mirror of the official project's `main` branch. If you work directly on it, it becomes a mix of stable code and your unfinished work.
2.  **Parallel Work:** Branches allow you to work on multiple things at once. You can switch from a half-finished feature to an urgent bug fix by simply switching branches.
3.  **Clear Code Reviews:** A Pull Request is based on a branch. This allows your teammates to review the specific, self-contained changes for that one task, making the review process clean and focused.

---

### 🤔 What happens when I switch branches? Does it duplicate my files?

No, Git is very efficient! It **does not** duplicate your project files.

When you run `git switch <branch-name>`, Git intelligently modifies your working directory (the files you see in your code editor) to match the state of the new branch.

*   It adds, removes, or modifies **only the files that are different** between the two branches.
*   Files that are identical are left untouched.

Your code editor (like VS Code) will automatically detect these file changes and update its view. You are always working in the same folder, but Git dynamically changes its contents to reflect the branch you've checked out.

---

### 🤔 My Pull Request was rejected and now my fork is outdated. What do I do?

This is a very common scenario. Your fork on GitHub does **not** automatically sync with the main project. You must sync it yourself.

Here is the three-step process:

1.  **Sync Your Local `main`:** First, update your *local* `main` branch with the latest code from the *main project* (`upstream`).
    ```bash
    git switch main
    git pull upstream main
    ```
2.  **Update Your Fork:** Now, push your newly updated local `main` branch up to your fork on GitHub (`origin`). This overwrites the outdated `main` branch on your fork.
    ```bash
    git push origin main
    ```
3.  **Start Fresh:** You are now fully in sync. You can create a new feature branch from your clean `main` branch.

---

### 🤔 Should I delete my fork after the project is done?

**Yes, most of the time.**

A fork's main purpose is to be a temporary staging area for your contributions. Once your work is merged and you don't plan to contribute again soon, you can delete your fork to reduce clutter in your GitHub account.

You can always create a fresh fork if you decide to contribute again in the future.
