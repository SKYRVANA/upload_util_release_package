# Quick Reference

Fast commands for common tasks.

---

## 🚀 First Time Setup

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
git init
git add .
git commit -m "Initial commit: Setup release repository"
git remote add origin https://github.com/SKYRVANA/upload_util_release_package.git
git branch -M main
git push -u origin main
```

---

## 📝 Update version.json

```bash
# Edit version.json with new version info
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
nano version.json  # or use any text editor

# Commit and push
git add version.json
git commit -m "Update version to v1.1.0"
git push origin main
```

---

## 🔄 Update Any File

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
git add .
git commit -m "Update documentation"
git push origin main
```

---

## 🏷️ Create GitHub Release (Web)

1. Go to: https://github.com/SKYRVANA/upload_util_release_package/releases
2. Click: "Draft a new release"
3. Tag: `v1.1.0`
4. Title: `v1.1.0 - Description`
5. Upload: DMG and EXE files
6. Click: "Publish release"

---

## 🏷️ Create GitHub Release (CLI)

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/package"

# After building executables
gh release create v1.1.0 \
  --title "v1.1.0 - Feature Update" \
  --notes "Release notes here" \
  SD_Card_Upload_Utility_v1.1.0_macOS.dmg \
  SD_Card_Upload_Utility_v1.1.0_Windows.exe
```

---

## 🔍 Check Repository Status

```bash
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
git status
git log --oneline -5
```

---

## 🌐 Important URLs

- **Repository**: https://github.com/SKYRVANA/upload_util_release_package
- **Releases**: https://github.com/SKYRVANA/upload_util_release_package/releases
- **version.json (raw)**: https://raw.githubusercontent.com/SKYRVANA/upload_util_release_package/main/version.json

---

## 📦 Complete Release Workflow

```bash
# 1. Build executables
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/package"
./build_macos.sh

# 2. Create GitHub Release (web interface)
# Upload DMG/EXE to: https://github.com/SKYRVANA/upload_util_release_package/releases

# 3. Update version.json
cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"
nano version.json

# 4. Commit and push
git add version.json
git commit -m "Release v1.1.0"
git push origin main
```

---

## 🔧 Troubleshooting

### Fix remote URL
```bash
git remote set-url origin https://github.com/SKYRVANA/upload_util_release_package.git
```

### Pull latest changes
```bash
git pull origin main
```

### See remotes
```bash
git remote -v
```

### Reset to last commit
```bash
git reset --hard HEAD
```

---

## 📋 version.json Template

```json
{
  "version": "1.1.0",
  "download_url": "https://github.com/SKYRVANA/upload_util_release_package/releases/download/v1.1.0/SD_Card_Upload_Utility_v1.1.0_macOS.dmg",
  "release_notes": "Brief description of what's new"
}
```

---

## ✅ Verification Commands

```bash
# Check if version.json is accessible
curl https://raw.githubusercontent.com/SKYRVANA/upload_util_release_package/main/version.json

# Check repository exists
curl -I https://github.com/SKYRVANA/upload_util_release_package

# Check release download URL
curl -I "https://github.com/SKYRVANA/upload_util_release_package/releases/download/v1.0.0/SD_Card_Upload_Utility_v1.0.0_macOS.dmg"
```

---

## 📱 One-Liner Commands

```bash
# Quick commit all changes
git add . && git commit -m "Update" && git push

# View commit history
git log --oneline --graph --all -10

# Undo last commit (keep changes)
git reset --soft HEAD~1

# Check what will be committed
git diff --staged

# Remove file from staging
git reset HEAD filename.txt
```

---

**Pro Tip**: Create aliases in your `~/.zshrc` or `~/.bashrc`:

```bash
alias release-cd='cd "/Users/shrikrushnabhagwat/Downloads/Mac Upload Utility/upload_util_release_package"'
alias release-push='git add . && git commit -m "Update" && git push'
alias release-status='git status'
```

Then use: `release-cd`, `release-push`, `release-status`
