# Releases Folder

This folder is optional and can be used to organize release binaries by version.

## Structure

```
releases/
├── v1.0.0/
│   ├── SD_Card_Upload_Utility_v1.0.0_macOS.dmg
│   └── SD_Card_Upload_Utility_v1.0.0_Windows.exe
├── v1.1.0/
│   ├── SD_Card_Upload_Utility_v1.1.0_macOS.dmg
│   └── SD_Card_Upload_Utility_v1.1.0_Windows.exe
└── ...
```

## Note

**GitHub Releases is Recommended**: Instead of committing large binary files to the repository, use GitHub Releases to host the actual binaries. This folder can be used for:
- Local organization before uploading to GitHub
- Backup copies
- Archive of old versions

## Best Practice

1. Build executables using the build scripts
2. Upload directly to GitHub Releases (not to this folder)
3. Update `version.json` in the repository root
4. Keep this folder for reference only (add `*.dmg` and `*.exe` to .gitignore)

For detailed instructions, see the main project's RELEASE_GUIDE.md.
