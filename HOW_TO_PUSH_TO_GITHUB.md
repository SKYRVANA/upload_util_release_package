# How to Push to GitHub

Step-by-step guide to push this repository to GitHub.

---

## Prerequisites

1. **Git installed** on your computer
   ```bash
   git --version  # Check if installed
   ```
   If not installed:
   - macOS: `brew install git` or download from https://git-scm.com
   - Windows: Download from https://git-scm.com

2. **GitHub account** at https://github.com
   - If you don't have one, create a free account

3. **GitHub CLI (optional but recommended)**
   ```bash
   brew install gh  # macOS
   # or download from https://cli.github.com/
   ```

---

## Method 1: Using GitHub Web Interface + Command Line (Easiest)

### Step 1: Create Repository on GitHub

1. Go to https://github.com/SKYRVANA
2. Click the **"+"** button (top-right) → **"New repository"**
3. Fill in details:
   - **Repository name**: `upload_util_release_package`
   - **Description**: "Release packages for SD Card Upload Utility"
   - **Visibility**: ✅ **Public** (IMPORTANT: Must be public for raw file access)
   - **Initialize**: ❌ Do NOT check any boxes (no README, .gitignore, or license)
4. Click **"Create repository"**

### Step 2: Initialize Local Git Repository

Open Terminal and navigate to this folder:

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
```

Initialize Git:

```bash
# Initialize repository
git init

# Add all files
git add .

# Create first commit
git commit -m "Initial commit: Setup release repository"
```

### Step 3: Connect to GitHub

```bash
# Add GitHub as remote (replace SKYRVANA with your username if different)
git remote add origin https://github.com/SKYRVANA/upload_util_release_package.git

# Rename branch to main (if needed)
git branch -M main

# Push to GitHub
git push -u origin main
```

### Step 4: Verify

1. Go to https://github.com/SKYRVANA/upload_util_release_package
2. You should see all files: README.md, version.json, etc.
3. Test version.json URL:
   ```
   https://raw.githubusercontent.com/SKYRVANA/upload_util_release_package/main/version.json
   ```

---

## Method 2: Using GitHub CLI (Faster)

### Step 1: Authenticate

```bash
gh auth login
```

Follow the prompts to authenticate with your GitHub account.

### Step 2: Initialize and Push

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"

# Initialize git
git init
git add .
git commit -m "Initial commit: Setup release repository"

# Create repository on GitHub and push
gh repo create SKYRVANA/upload_util_release_package --public --source=. --push

# Description will be prompted or use:
gh repo create SKYRVANA/upload_util_release_package \
  --public \
  --description "Release packages for SD Card Upload Utility" \
  --source=. \
  --push
```

---

## Method 3: Using GitHub Desktop (GUI)

### Step 1: Download GitHub Desktop

Download from https://desktop.github.com/

### Step 2: Initialize Repository

1. Open GitHub Desktop
2. File → Add Local Repository
3. Choose: `/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package`
4. Click "Create a repository" if prompted
5. Fill in details and click "Create Repository"

### Step 3: Publish to GitHub

1. Click "Publish repository" button (top bar)
2. Set name: `upload_util_release_package`
3. Description: "Release packages for SD Card Upload Utility"
4. ✅ Keep code private: **UNCHECKED** (must be public)
5. Click "Publish Repository"

---

## Updating the Repository Later

When you need to update files (like version.json):

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"

# Make your changes (edit version.json, README.md, etc.)

# Stage changes
git add .

# Commit with message
git commit -m "Update version to 1.1.0"

# Push to GitHub
git push origin main
```

---

## Typical Workflow for New Release

### 1. Build Executables

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/package"
./build_macos.sh
# Creates: SD_Card_Upload_Utility_v1.1.0_macOS.dmg
```

### 2. Create GitHub Release

1. Go to https://github.com/SKYRVANA/upload_util_release_package/releases
2. Click "Draft a new release"
3. Tag: `v1.1.0`
4. Title: `v1.1.0 - Feature Update`
5. Description: Write release notes
6. Upload DMG and EXE files
7. Click "Publish release"

### 3. Update version.json

Edit `version.json`:
```json
{
  "version": "1.1.0",
  "download_url": "https://github.com/SKYRVANA/upload_util_release_package/releases/download/v1.1.0/SD_Card_Upload_Utility_v1.1.0_macOS.dmg",
  "release_notes": "New features and improvements"
}
```

### 4. Commit and Push

```bash
git add version.json
git commit -m "Update version.json to v1.1.0"
git push origin main
```

---

## Important Notes

### ✅ DO:
- ✅ Make repository **PUBLIC** (required for auto-update to work)
- ✅ Keep `version.json` in repository root (main branch)
- ✅ Use GitHub Releases for binary files (DMG, EXE)
- ✅ Update `version.json` after each release
- ✅ Write clear commit messages

### ❌ DON'T:
- ❌ Don't commit large binary files (DMG, EXE) to the repository
  - Use GitHub Releases instead
  - Binaries in git make repo very large
- ❌ Don't make repository private (auto-update won't work)
- ❌ Don't forget to update version.json after releases

---

## Repository Structure (What Gets Pushed)

```
upload_util_release_package/
├── .gitignore                  # Ignores temp files
├── README.md                   # Main documentation
├── version.json                # Version info (CRITICAL)
├── INSTALLATION.md             # Installation guide
├── HOW_TO_PUSH_TO_GITHUB.md   # This file
└── releases/
    └── README.md               # Release notes
```

**Note**: Binary files (DMG, EXE) are hosted on GitHub Releases, not in the repository itself.

---

## Troubleshooting

### Error: "remote origin already exists"
```bash
git remote remove origin
git remote add origin https://github.com/SKYRVANA/upload_util_release_package.git
```

### Error: "Permission denied (publickey)"

Using HTTPS instead of SSH:
```bash
git remote set-url origin https://github.com/SKYRVANA/upload_util_release_package.git
```

Or setup SSH key: https://docs.github.com/en/authentication/connecting-to-github-with-ssh

### Error: "Repository not found"

Make sure:
1. Repository exists on GitHub
2. You have access to it
3. URL is correct (check username: SKYRVANA)

### Error: "failed to push some refs"

Pull first:
```bash
git pull origin main --rebase
git push origin main
```

---

## Verification Checklist

After pushing, verify:

- [ ] Repository is visible at https://github.com/SKYRVANA/upload_util_release_package
- [ ] Repository is **Public** (check settings)
- [ ] `version.json` exists in root
- [ ] `version.json` is accessible at raw URL:
  ```
  https://raw.githubusercontent.com/SKYRVANA/upload_util_release_package/main/version.json
  ```
- [ ] README.md displays properly on GitHub
- [ ] All files are present

---

## Next Steps

After pushing the repository:

1. **Create First Release**: Follow RELEASE_GUIDE.md to create v1.0.0 release
2. **Upload Binaries**: Upload DMG and EXE files to GitHub Releases
3. **Update version.json**: Update with actual download URLs
4. **Test Auto-Update**: Launch the app to test update detection

---

## Getting Help

- **GitHub Docs**: https://docs.github.com/en/get-started
- **Git Basics**: https://git-scm.com/book/en/v2/Getting-Started-Git-Basics
- **GitHub CLI**: https://cli.github.com/manual/

---

**Last Updated**: January 2025
