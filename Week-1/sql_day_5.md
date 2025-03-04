# SQL Day 5

## Git Basics & Stash Command
### Introduction to Git Workflow:
- Git allows multiple users to collaborate on the same project.
- Changes are made in **branches** to prevent direct modifications to the main branch.
- Git provides **stash** to save incomplete work temporarily.

### Git Stash Commands:
```sh
# Save changes without committing
git stash save "WIP: Interest Calculation Module"

# Add a file to staging
git add module.py

# List all stashed changes
git stash list

# Show a specific stash
git stash show stash@{0}

# Apply and remove the latest stash
git stash pop
```

## GitHub Learning Platform
- Explored interactive Git tutorials at: [Learn Git Branching](https://learngitbranching.js.org/)

### Git Commands for Feature Branch Workflow:
```sh
# Create and switch to a new branch
git checkout -b bugFix

# Commit changes
git commit -m "Fixed a bug"

# Switch back to main branch
git checkout main

# Commit new changes
git commit -m "Updated main branch"

# Merge feature branch into main
git merge bugFix
```

## Summary:
- Learned **Git stash** to save temporary changes.
- Practiced **Git branching & merging**.
- Explored **GitHub interactive learning platform**.
- Strengthened version control skills for collaborative development.
