SQL(DAY-5)

## Git Basics and Git Bash Terminal  
We revised Git commands from the previous day and explored additional commands.

### Why Use Git?  
Git allows multiple users to work in the same environment. Instead of making changes directly to the main branch (which can crash the project), developers work on branches and merge changes when ready.

### Git Stash  
When switching branches, Git stash helps save current changes without committing them, allowing work on another task.

### Common Git Stash Commands:
```bash
# Save current changes temporarily
git stash save "WIP: Interest calculation module"

# Add a file to the staging area
git add module.py

# List all files in the directory
ls -lrt

# View all saved stashes
git stash list

# Show details of a specific stash
git stash show stash@{0}

# Apply and remove the latest stash
git stash pop
```

---

## Learn Git Branching  
Practiced Git branching concepts using an interactive tutorial: [Learn Git Branching](https://learngitbranching.js.org/)

### Git Branching Commands:
```bash
# Create a new branch and switch to it
git checkout -b bugFix

# Make changes and commit
git commit -m "Bug fix changes"

# Switch back to the main branch
git checkout main

# Commit changes in the main branch
git commit -m "Main branch updates"

# Merge the bugFix branch into the main branch
git merge bugFix
```

---

In the afternoon session, we applied these Git commands and worked on solving Git-related challenges.

## Summary:
- Learned **Git stash** to save temporary changes.
- Practiced **Git branching & merging**.
- Explored **GitHub interactive learning platform**.
- Strengthened version control skills for collaborative development.
