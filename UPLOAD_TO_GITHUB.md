# How to Upload to GitHub

## Step 1: Create GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the **"+"** icon in the top right → **"New repository"**
3. Repository name: `CS468_Project2` (or your preferred name)
4. Description: "AI Context-Aware Study Coach - Mobile app for generating study materials from notes"
5. Choose **Public** or **Private** (as per your requirements)
6. **DO NOT** check "Initialize with README" (we already have files)
7. Click **"Create repository"**

## Step 2: Add All Files and Commit

Run these commands in your terminal (from the project directory):

```bash
# Make sure you're in the project directory
cd <your-project-location>

# Add all files (respects .gitignore)
git add .

# Check what will be committed (optional)
git status

# Create initial commit
git commit -m "Initial commit: AI Context-Aware Study Coach with multi-document scanning"

# Set main branch name
git branch -M main
```

## Step 3: Connect to GitHub and Push

After creating the repository on GitHub, you'll see a page with setup instructions. Use these commands:

```bash
# Add your GitHub repository as remote (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/CS468_Project2.git

# Push to GitHub
git push -u origin main
```

**Note:** If you're asked for credentials:
- **Username:** Your GitHub username
- **Password:** Use a Personal Access Token (not your GitHub password)
  - Go to: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
  - Generate new token with `repo` permissions
  - Use that token as your password

## Step 4: Verify Upload

1. Go to your repository on GitHub
2. Check that all files are there
3. Verify that:
   - ✅ `node_modules/` is NOT uploaded (excluded by .gitignore)
   - ✅ `__pycache__/` is NOT uploaded (excluded by .gitignore)
   - ✅ All your code files ARE uploaded
   - ✅ All documentation files ARE uploaded

## Step 5: Add Collaborators (if needed)

1. Go to your repository → **Settings** → **Collaborators**
2. Click **"Add people"**
3. Enter GitHub usernames and send invitations

## Quick Command Reference

```bash
# Check status
git status

# Add all changes
git add .

# Commit changes
git commit -m "Your commit message"

# Push to GitHub
git push

# Pull latest changes
git pull
```

## Troubleshooting

### If you get "remote origin already exists":
```bash
# Remove existing remote
git remote remove origin

# Add it again with correct URL
git remote add origin https://github.com/YOUR_USERNAME/CS468_Project2.git
```

### If you need to update files later:
```bash
# After making changes
git add .
git commit -m "Description of changes"
git push
```

### If you want to exclude more files:
Edit `.gitignore` and add patterns, then:
```bash
git rm -r --cached .
git add .
git commit -m "Update .gitignore"
```

