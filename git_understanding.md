# Understanding Merge Conflicts in Git

## What Caused the Conflict?

The conflict occurred because the same lines in the same file were modified differently in the `main` and my `feature-branch` branches. Git couldn't automatically determine which changes to keep, requiring manual resolution.

## How Did You Resolve It?

The conflict was resolved by manually editing the conflicted file to merge the desired changes from both branches. This involved reviewing both sets of changes, deciding on the final content, and then committing the resolved file.

## What Did You Learn?

This exercise emphasized the importance of clear communication and coordination in collaborative projects to minimize conflicts. It also provided hands-on experience with GitHub Desktop’s conflict resolution tools, highlighting the need for careful review during merges to ensure code integrity.

# Understanding Staging vs. Committing in Git

## Difference Between Staging and Committing

- **Staging (`git add`)**: Prepares changes to be included in the next commit without permanently saving them in Git’s history.
- **Committing (`git commit`)**: Saves staged changes permanently in the repository, creating a new snapshot in Git’s history.

## Why Does Git Separate Staging and Committing?

1. **Allows Selective Changes**: You can choose which changes to commit instead of committing all modifications at once.
2. **Supports Clean and Organized Commits**: Helps group related changes together in meaningful commits.
3. **Prevents Mistakes**: Unfinished or experimental changes can stay in the working directory without affecting committed work.

## When Would You Stage Changes Without Committing?

- **When Grouping Changes**: Helps separate feature updates from bug fixes into different commits.
- **To Review Before Committing**: You can check changes using `git diff --staged` before committing.
- **When Not Ready to Commit**: If changes are incomplete, you can stage them and commit later when fully prepared.

---

## Why Teams Use Branches Instead of Pushing Directly to Main

### **Why is pushing directly to main problematic?**

- Risk of Breaking the Code, if changes are pushed directly to `main`, any issue or bug introduced could break the code for everyone on the team.
- Collaboration Conflicts, multiple developers working on the same branch (e.g., `main`) could result in conflicting changes that are harder to resolve.

### **How do branches help with reviewing code?**

- Isolated Changes, branches allow developers to work on new features or bug fixes without affecting the main codebase. This makes reviewing and testing easier.
- Code Review, once changes are complete, branches can be submitted via pull requests for a team member to review the code before merging.

### **What happens if two people edit the same file on different branches?**

- Merge Conflicts, if two people modify the same lines in the same file, Git will encounter a conflict when merging. Developers will need to manually resolve the conflict by deciding which changes to keep.
