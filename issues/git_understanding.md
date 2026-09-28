# Git Concept: Staging vs. Committing

**What is the difference between staging and committing?**
Staging (`git add`) is like putting items into a shopping cart; you are selecting and preparing specific changes that you want to include in your next update. Committing (`git commit`) is like checking out at the cash register; it permanently records a snapshot of the items currently in your staging area into the repository's official version history.

**Why does Git separate these two steps?**
Git separates these steps to give developers precise control over their project's history. Instead of forcing you to save every modified file at once, the staging area acts as a buffer. This allows you to review your work, group related changes together, and write a highly specific commit message for that exact group of files, ensuring a clean and readable Git history.

**When would you want to stage changes without committing?**
You want to stage changes without committing when you are working on a large task and making incremental progress. For example, if I fix a database bug and also update a UI component in the same working session, I can stage only the database files, commit them with a message like "Fix database connection timeout," and then stage the UI files for a separate commit. This keeps commits atomic and focused.

## Branching & Team Collaboration

**Why is pushing directly to `main` problematic?**
Pushing directly to `main` (which usually represents the stable production environment) is highly risky because it bypasses all quality control. If broken, untested, or incomplete code is pushed directly, it can immediately break the application for end-users and disrupt other developers who rely on a stable `main` branch to branch off of.

**How do branches help with reviewing code?**
Branches isolate new features or bug fixes from the core codebase. When work is complete on a branch, developers open a Pull Request (PR). This creates a dedicated space for other team members to safely read the isolated changes, run automated tests, and suggest improvements before those changes are ever merged into the main project.

**What happens if two people edit the same file on different branches?**
If two people edit the exact same lines of the same file on different branches and try to merge them into `main`, Git will not overwrite the work automatically. Instead, it flags a "merge conflict." Git halts the process and forces the developers to manually inspect the conflicting lines and decide which version to keep (or how to combine them) before allowing the merge to succeed.