# Installation Guide

Complete installation instructions for SD Card Upload Utility.

---

## macOS Installation

### System Requirements
- macOS 10.13 (High Sierra) or later
- 200 MB free disk space
- Internet connection for authentication and uploads

### Installation Steps

1. **Download** the DMG file
   - Go to [Releases](https://github.com/SKYRVANA/upload_util_release_package/releases)
   - Download `SD_Card_Upload_Utility_v1.0.0_macOS.dmg`

2. **Open** the DMG file
   - Double-click the downloaded DMG file
   - A new window will open showing the application

3. **Install** the application
   - Drag "SD Card Upload Utility" to the Applications folder
   - Wait for the copy to complete

4. **First Launch** (Important!)
   - Open Applications folder
   - **Right-click** on "SD Card Upload Utility"
   - Select **"Open"** from the menu
   - Click **"Open"** in the security dialog

   *Why?* macOS Gatekeeper blocks unsigned apps on first launch. After the first time, you can launch normally.

5. **Verify Installation**
   - The application should launch and show the login screen
   - You're ready to use the app!

### Troubleshooting macOS

**Problem**: "SD Card Upload Utility" is damaged and can't be opened
- **Solution**: The app was quarantined by macOS. Run this command in Terminal:
  ```bash
  xattr -cr "/Applications/SD Card Upload Utility.app"
  ```

**Problem**: Application won't open at all
- **Solution 1**: Make sure you have macOS 10.13 or later
- **Solution 2**: Try removing and reinstalling the app
- **Solution 3**: Check Console.app for error messages

**Problem**: "You do not have permission to open the application"
- **Solution**: Repair permissions:
  ```bash
  sudo chmod -R 755 "/Applications/SD Card Upload Utility.app"
  ```

---

## Windows Installation

### System Requirements
- Windows 10 or later (64-bit)
- 200 MB free disk space
- Internet connection for authentication and uploads

### Installation Steps

1. **Download** the EXE file
   - Go to [Releases](https://github.com/SKYRVANA/upload_util_release_package/releases)
   - Download `SD_Card_Upload_Utility_v1.0.0_Windows.exe`

2. **Run** the installer
   - Double-click the downloaded EXE file

3. **Handle Windows SmartScreen** (if appears)
   - Click **"More info"**
   - Click **"Run anyway"**

   *Why?* The app is not code-signed, so Windows shows this warning for your protection.

4. **Install Location** (Optional)
   - Default: `C:\Program Files\SD Card Upload Utility\`
   - You can choose a different location if needed

5. **Complete Installation**
   - Click through the installation wizard
   - Choose to create desktop shortcut (optional)
   - Click "Finish"

6. **First Launch**
   - Double-click the desktop shortcut or find in Start menu
   - The application should launch and show the login screen

### Troubleshooting Windows

**Problem**: Windows Defender blocks the application
- **Solution**:
  1. Click "More info"
  2. Click "Run anyway"
  3. Or add an exception in Windows Defender settings

**Problem**: Application crashes on startup
- **Solution 1**: Install Visual C++ Redistributable:
  - Download from: https://aka.ms/vs/17/release/vc_redist.x64.exe
  - Install and restart
- **Solution 2**: Run as Administrator (right-click → Run as administrator)

**Problem**: "Missing DLL" error
- **Solution**: Reinstall the application with administrator privileges

---

## Uninstallation

### macOS
1. Open Applications folder
2. Drag "SD Card Upload Utility" to Trash
3. Empty Trash
4. (Optional) Remove preferences:
   ```bash
   rm -rf ~/Library/Preferences/com.skyrvana.sdcardupload.*
   ```

### Windows
1. Open Settings → Apps → Installed apps
2. Find "SD Card Upload Utility"
3. Click "..." → Uninstall
4. Follow the uninstall wizard

---

## Updating

The application includes an automatic update checker:

1. **Before Login**: If a new version is available, you'll see a dialog
   - Click "Download Update" to get the new version
   - Or click "Skip" to continue with current version

2. **After Login**: Check the bottom-right corner for update notifications
   - Click "Update Now" button if it appears

3. **Manual Update**:
   - Download the latest version from [Releases](https://github.com/SKYRVANA/upload_util_release_package/releases)
   - Install over the existing version (no need to uninstall first)

---

## Network Configuration

### Firewall Settings

The application needs to access:
- **Supabase**: `https://supabase.skyrvana.com` (Authentication)
- **Google Drive API**: `https://www.googleapis.com` (File uploads)
- **GitHub**: `https://raw.githubusercontent.com` (Update checks)

If your firewall blocks the app, add these domains to the allowlist.

### Proxy Settings

The application uses system proxy settings automatically. If you're behind a corporate proxy, configure it in your system settings.

---

## First Time Setup

After installation:

1. **Launch** the application
2. **Login** with your credentials (or reset password if needed)
3. **Insert** an SD card to test
4. **Select** the drive and enter a test Order ID
5. **Upload** a small test to verify everything works

---

## Getting Help

- **Documentation**: See [README.md](README.md)
- **Issues**: Report bugs on the [Issues page](https://github.com/SKYRVANA/upload_util_release_package/issues)
- **Updates**: Check [Releases](https://github.com/SKYRVANA/upload_util_release_package/releases) for latest version

---

**Last Updated**: January 2025
