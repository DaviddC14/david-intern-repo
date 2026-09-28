# Git Concept: Staging vs. Committing

**What is the difference between staging and committing?**
Staging (`git add`) is like putting items into a shopping cart; you are selecting and preparing specific changes that you want to include in your next update. Committing (`git commit`) is like checking out at the cash register; it permanently records a snapshot of the items currently in your staging area into the repository's official version history.

**Why does Git separate these two steps?**
Git separates these steps to give developers precise control over their project's history. Instead of forcing you to save every modified file at once, the staging area acts as a buffer. This allows you to review your work, group related changes together, and write a highly specific commit message for that exact group of files, ensuring a clean and readable Git history.

**When would you want to stage changes without committing?**
You want to stage changes without committing when you are working on a large task and making incremental progress. For example, if I fix a database bug and also update a UI component in the same working session, I can stage only the database files, commit them with a message like "Fix database connection timeout," and then stage the UI files for a separate commit. This keeps commits atomic and focused.


## Merge Conflicts & Conflict Resolution

**What caused the conflict?**
The merge conflict was intentionally caused by editing the exact same line of the same file on two separate branches (e.g., `main` and a feature branch). When I attempted to merge the feature branch back into `main`, Git could not automatically determine which version of the line was the correct one to keep, so it halted the merge process.

**How did you resolve it?**
I opened the conflicted file in VS Code. The editor clearly highlighted the conflict zones, showing the "Current Change" (from the branch I was on) and the "Incoming Change" (from the branch being merged). I reviewed the code, used the VS Code UI button to "Accept Both Changes" (or manually edited the lines to combine them logically), saved the file, and finally staged (`git add`) and committed the resolved file to complete the merge.

**What did you learn?**
I learned that merge conflicts are a completely normal, expected part of team collaboration, not an "error" to panic over. They are simply Git's safety mechanism to prevent accidental data loss. I also learned that modern IDEs like VS Code make resolving these conflicts highly visual and straightforward.