#### What does each command do?

- `git checkout main -- <file>`: Restores a file from the main branch, discarding local changes.
- `git cherry-pick <commit>`: Applies a specific commit from another branch to the current branch.
- `git log`: Shows the commit history and how changes evolved.
- `git blame <file>`: Shows who last modified each line in a file and when.

#### When would you use it in a real project?

- `git checkout main -- <file>`: When you want to discard changes in a file and return to the version in main.
- `git cherry-pick <commit>`: When you want to apply a specific commit from another branch without merging the whole branch.
- `git log`: When you need to see the commit history or track changes.
- `git blame <file>`: When you want to find out who changed a specific line in a file.

#### What surprised you while testing these commands?

- `git cherry-pick` is useful for applying specific commits from other branches without merging the entire branch.
- `git blame` is really helpful for tracking down who changed a line of code, especially in team projects.
