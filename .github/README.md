# GitHub Actions CI/CD Setup

This repository includes automated builds for all platforms using GitHub Actions.

## Workflows

### 1. **CI Build** (`.github/workflows/build.yml`)
Runs on every push to `main` or `develop` branches and on pull requests.

**Builds:**
- ✅ Android (on Ubuntu)
- ✅ iOS (on macOS)
- ✅ macOS (on macOS)
- ✅ Windows (on Windows)

**Artifacts:** Build outputs are uploaded as artifacts for download.

### 2. **Release Build** (`.github/workflows/release.yml`)
Runs when you create a Git tag (e.g., `v1.0.0`).

**Creates:**
- Production builds for all platforms
- GitHub Release with downloadable binaries

## How to Use

### Setting Up the Repository

1. **Create a GitHub repository:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Hello World MAUI app"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/maui-dot-net.git
   git push -u origin main
   ```

2. **The workflows will automatically run** when you push to GitHub.

### Viewing Build Results

1. Go to your repository on GitHub
2. Click the **Actions** tab
3. See all workflow runs and download artifacts

### Creating a Release

To build release versions for all platforms:

```bash
# Create and push a tag
git tag v1.0.0
git push origin v1.0.0
```

The release workflow will:
1. Build for all platforms
2. Create a GitHub Release
3. Attach the binaries to the release

### Downloading Built Apps

After a workflow completes:

1. Go to **Actions** → Click on the workflow run
2. Scroll to **Artifacts** section
3. Download:
   - `windows-build` - Windows MSIX/executable
   - `macos-build` - macOS app bundle
   - `ios-build` - iOS app bundle
   - `android-build` - Android APK

## Platform-Specific Notes

### Windows
- Builds on `windows-latest` runner
- Produces MSIX package for Windows 10/11
- Can be installed directly on Windows machines

### macOS
- Builds on `macos-latest` runner
- Produces .app bundle for macOS
- Requires code signing for distribution (can be added later)

### iOS
- Builds on `macos-latest` runner
- Produces .app bundle for iOS
- Requires Apple Developer account and certificates for device deployment

### Android
- Builds on `ubuntu-latest` runner (fastest and cheapest)
- Produces APK file
- Can be installed directly on Android devices

## Customization

### Add Code Signing

For production releases, you'll want to add code signing:

**iOS/macOS:**
Add secrets for:
- `IOS_CERTIFICATE`
- `IOS_PROVISIONING_PROFILE`
- `APPLE_DEVELOPER_ID`

**Android:**
Add secrets for:
- `ANDROID_KEYSTORE`
- `KEYSTORE_PASSWORD`
- `KEY_ALIAS`
- `KEY_PASSWORD`

**Windows:**
Add secrets for:
- `WINDOWS_CERTIFICATE`
- `CERTIFICATE_PASSWORD`

### Modify Build Settings

Edit the `.github/workflows/*.yml` files to:
- Change trigger branches
- Add automated tests
- Modify build configurations
- Add deployment steps

## Cost Considerations

GitHub Actions is free for public repositories with generous limits:
- 2,000 minutes/month for private repos
- Unlimited for public repos

**Runner costs vary:**
- Ubuntu: 1x multiplier (cheapest)
- Windows: 2x multiplier
- macOS: 10x multiplier (most expensive)

The current setup is optimized to use appropriate runners for each platform.

## Troubleshooting

If builds fail:

1. Check the Actions tab for error logs
2. Common issues:
   - Missing workload installation
   - Platform-specific SDK requirements
   - Resource file paths (case-sensitive on Linux/macOS)

3. Test locally first with the same commands used in the workflow

## Next Steps

- [ ] Add automated testing
- [ ] Set up code signing
- [ ] Add deployment to app stores
- [ ] Configure versioning automation
- [ ] Add PR preview builds
