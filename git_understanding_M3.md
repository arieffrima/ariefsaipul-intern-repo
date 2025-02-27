# Understanding Staging vs. Committing in Git

## Difference Between Staging and Committing
- Staging (`git add`): Prepares changes to be included in the next commit without permanently saving them in Git’s history.
- Committing (`git commit`): Saves staged changes permanently in the repository, creating a new snapshot in Git’s history.

## Why Does Git Separate Staging and Committing?
1. Because it can choose which changes to commit instead of committing all modifications at once.
2. Helps group related changes together in meaningful commits.
3. Unfinished or experimental changes can stay in the working directory without affecting committed work.

## When Would You Stage Changes Without Committing?
- When Grouping Changes, helps separate feature updates from bug fixes into different commits.
- To Review Before Committing, we can check changes using `git diff --staged` before committing.
- When Not Ready to Commit, If changes are incomplete, we can stage them and commit later when fully prepared.
