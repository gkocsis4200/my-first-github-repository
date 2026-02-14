# How to Change the Default Branch in GitHub

This guide explains how to change the default branch for your GitHub repository.

## What is a Default Branch?

The default branch is the base branch for pull requests and code commits in your repository. When someone visits your repository, they see the content from the default branch. GitHub uses `main` as the default branch name for new repositories, though older repositories may use `master`.

## Why Change the Default Branch?

You might want to change the default branch to:
- Switch from `master` to `main` (or vice versa)
- Use a different branch name that better fits your workflow (e.g., `develop`, `production`)
- Reorganize your repository structure

## Prerequisites

Before changing the default branch:
1. Make sure the new branch exists in your repository
2. Ensure the new branch has the content you want as the default
3. Have admin permissions for the repository

## Method 1: Using GitHub Web Interface (Recommended)

### Step-by-Step Instructions:

1. **Navigate to Your Repository**
   - Go to your repository on GitHub.com
   - Example: `https://github.com/username/repository-name`

2. **Open Repository Settings**
   - Click on the **Settings** tab (top navigation bar)
   - You need admin permissions to access this tab

3. **Find Branches Settings**
   - In the left sidebar, click on **Branches**
   - Or navigate directly to: `https://github.com/username/repository-name/settings/branches`

4. **Change the Default Branch**
   - Look for the "Default branch" section at the top
   - Click the switch/pencil icon (⇄) next to the current default branch name
   - Select your desired branch from the dropdown menu
   - Click **Update** or **I understand, update the default branch**

5. **Confirm the Change**
   - GitHub will show a confirmation dialog explaining the implications
   - Click **I understand, update the default branch** to confirm

6. **Verify the Change**
   - The new branch should now show as the default
   - Visit your repository homepage to confirm it displays the new default branch

## Method 2: Using GitHub CLI (gh)

If you have the GitHub CLI installed, you can change the default branch from the command line:

```bash
# Change the default branch
gh repo edit --default-branch <new-branch-name>

# Example: Change to 'develop' branch
gh repo edit --default-branch develop
```

## Method 3: Using Git Commands

Note: You cannot change the default branch using only Git commands. The default branch setting is a GitHub repository setting, not a Git setting. However, you can prepare a new branch locally before changing it on GitHub:

```bash
# Create a new branch from your current branch
git checkout -b new-branch-name

# Push the new branch to GitHub
git push -u origin new-branch-name

# Then use Method 1 or 2 to change the default branch on GitHub
```

## Important Considerations

### After Changing the Default Branch:

1. **Update Local Repositories**
   - Team members need to update their local repositories:
   ```bash
   git fetch origin
   git branch -m old-branch-name new-branch-name
   git fetch origin
   git branch -u origin/new-branch-name new-branch-name
   git remote set-head origin -a
   ```

2. **Update CI/CD Pipelines**
   - Check and update any continuous integration or deployment configurations
   - Update branch references in workflows (e.g., GitHub Actions, Jenkins, CircleCI)

3. **Update Documentation**
   - Update any documentation that references the old default branch name
   - Update README files, contributing guides, etc.

4. **Update Branch Protection Rules**
   - Review and update any branch protection rules
   - The new default branch may need the same protections as the old one

5. **Notify Your Team**
   - Inform all contributors about the change
   - Provide instructions for updating their local repositories

## Troubleshooting

### "Branch not found" Error
- Ensure the branch exists in the remote repository
- Push the branch to GitHub if it only exists locally

### Cannot See Settings Tab
- You need admin permissions for the repository
- Contact the repository owner to change the default branch or grant you admin access

### Old Branch Still Shows
- Clear your browser cache
- Perform a hard refresh (Ctrl+Shift+R or Cmd+Shift+R)

## Best Practices

1. **Backup First**: Create a backup branch before making major changes
2. **Communicate**: Notify your team before changing the default branch
3. **Timing**: Change the default branch during low-activity periods
4. **Documentation**: Update all documentation that references branch names
5. **Testing**: Test that CI/CD pipelines work with the new default branch

## Additional Resources

- [GitHub Documentation: Managing the default branch](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch)
- [GitHub Documentation: Renaming a branch](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/renaming-a-branch)

## Summary

Changing the default branch is a simple process through GitHub's web interface, but requires careful coordination with your team and proper updates to your development workflow. Always ensure you have a backup and communicate the change to all contributors.
