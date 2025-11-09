# HelloMaui - .NET MAUI Hello World App

This is a cross-platform Hello World application built with .NET MAUI that runs on:
- **macOS** (via Mac Catalyst)
- **Windows** 
- **Android**
- **iOS**

## Prerequisites

1. **.NET 8.0 SDK or later**
   - Download from: https://dotnet.microsoft.com/download

2. **MAUI Workload**
   ```bash
   dotnet workload install maui
   ```

3. **Platform-Specific Requirements**:
   
   **For macOS/iOS development:**
   - Xcode (from Mac App Store)
   - Accept Xcode license:
     ```bash
     sudo xcodebuild -license
     ```
   
   **For Android:**
   - Android SDK (installed automatically with MAUI workload)
   
   **For Windows:**
   - Windows 10/11 with Windows SDK

## How to Run

### On macOS (Mac Catalyst)
```bash
dotnet build -t:Run -f net8.0-maccatalyst
```

### On Windows
```bash
dotnet build -t:Run -f net8.0-windows10.0.19041.0
```

### On Android
With an emulator running or device connected:
```bash
dotnet build -t:Run -f net8.0-android
```

### On iOS
With a simulator running or device connected:
```bash
dotnet build -t:Run -f net8.0-ios
```

## Project Structure

- `App.xaml` / `App.xaml.cs` - Application entry point
- `AppShell.xaml` / `AppShell.xaml.cs` - Shell configuration
- `MainPage.xaml` / `MainPage.xaml.cs` - Main page with "Hello, World!" UI
- `MauiProgram.cs` - MAUI app configuration
- `Platforms/` - Platform-specific code for Android, iOS, MacCatalyst, and Windows
- `Resources/` - Images, fonts, styles, and other resources

## Features

The app includes:
- A "Hello, World!" label
- A clickable button that counts clicks
- Cross-platform styling
- Responsive layout

## Building for Release

### Android APK
```bash
dotnet publish -f net8.0-android -c Release
```

### iOS IPA
```bash
dotnet publish -f net8.0-ios -c Release
```

### macOS App
```bash
dotnet publish -f net8.0-maccatalyst -c Release
```

### Windows MSIX
```bash
dotnet publish -f net8.0-windows10.0.19041.0 -c Release
```

## Troubleshooting

If you encounter issues:

1. **Restore workloads:**
   ```bash
   dotnet workload restore
   ```

2. **Clean and rebuild:**
   ```bash
   dotnet clean
   dotnet build
   ```

3. **Check .NET version:**
   ```bash
   dotnet --version
   ```

## Learn More

- [.NET MAUI Documentation](https://docs.microsoft.com/dotnet/maui/)
- [.NET MAUI Samples](https://github.com/dotnet/maui-samples)
