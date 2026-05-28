# rn-enterprise-upgrade-guide
# React Native Upgrade Guide (0.63 → 0.77)

## Project Upgrade Overview

This document outlines the migration and upgrade process for the React Native application from **React Native 0.63** to **React Native 0.77**.

The primary objective of this upgrade is to modernize the mobile application stack, improve platform compatibility, enhance performance, and ensure long-term maintainability.

### Why Upgrade to React Native 0.77

Upgrading from React Native 0.63 to 0.77 provides several critical improvements:

* Improved Android and iOS platform compatibility
* Enhanced application performance with Hermes engine improvements
* Better memory management and startup optimization
* Improved Metro bundler stability
* Updated Gradle, Kotlin, and native build support
* Compatibility with latest Android SDK and Xcode versions
* Improved debugging and developer tooling
* Security and dependency vulnerability fixes
* Better TypeScript and modern JavaScript support

### Key Benefits Achieved

* Reduced application startup time
* Improved build stability
* Compatibility with Android 14 / iOS latest versions
* Modernized dependency ecosystem
* Improved CI/CD compatibility
* Reduced deprecated API usage
* Better future upgrade maintainability

---

# Upgrade Summary

| Item               | Details                                                   |
| ------------------ | --------------------------------------------------------- |
| Previous Version   | React Native 0.63                                         |
| Target Version     | React Native 0.77                                         |
| Upgrade Type       | Incremental Migration                                     |
| Migration Strategy | Step-by-step version alignment with dependency validation |
| JavaScript Engine  | Hermes Enabled                                            |
| New Architecture   | Evaluated / Optional                                      |
| Platforms          | Android & iOS                                             |

## Upgrade Strategy

The migration was performed using an **incremental upgrade approach** instead of a direct version jump to reduce compatibility risks and isolate breaking changes effectively.

### Recommended Upgrade Path

```text
0.63 → 0.64 → 0.66 → 0.68 → 0.70 → 0.72 → 0.74 → 0.77
```

### Migration Activities

* Core React Native framework upgrade
* Native dependency alignment
* Android Gradle migration
* iOS Pod updates
* Metro configuration modernization
* Hermes enablement
* Deprecated API replacement
* Navigation compatibility fixes
* Build pipeline validation

---

# Environment & Tooling Updates

## Updated Development Environment

| Tool                  | Previous    | Updated           |
| --------------------- | ----------- | ----------------- |
| Node.js               | 12.x / 14.x | 18.x / 20.x       |
| npm                   | 6.x         | 10.x              |
| Yarn                  | 1.x         | 1.22+             |
| CocoaPods             | 1.10.x      | 1.15+             |
| Xcode                 | 12.x        | 15+               |
| Android Studio        | 4.x         | Hedgehog / Iguana |
| Gradle                | 6.x         | 8.x               |
| Android Gradle Plugin | 4.x         | 8.x               |
| Java/JDK              | 8           | 17                |
| Kotlin                | 1.3.x       | 1.9.x             |
| Hermes                | Disabled    | Enabled           |
| Flipper               | Enabled     | Removed / Updated |

---

# Dependency Updates

> Replace the sample entries below with actual project dependencies.

| Package                        | Old Version | New Version | Notes                         |
| ------------------------------ | ----------- | ----------- | ----------------------------- |
| react-native                   | 0.63.x      | 0.77.x      | Major framework upgrade       |
| react                          | 16.x        | 18.x        | React compatibility update    |
| @react-navigation/native       | 5.x         | 7.x         | Navigation API changes        |
| react-native-reanimated        | 1.x         | 3.x         | Babel plugin updates required |
| react-native-gesture-handler   | 1.x         | 2.x         | Updated gesture APIs          |
| react-native-screens           | 2.x         | 4.x         | Native screen optimizations   |
| react-native-safe-area-context | 3.x         | 5.x         | Updated provider setup        |
| axios                          | x.x         | x.x         | Compatibility verified        |
| redux                          | x.x         | x.x         | No major breaking changes     |
| react-native-vector-icons      | x.x         | x.x         | Font linking validation       |
| firebase packages              | x.x         | x.x         | Modular migration updates     |

---

# Native Configuration Changes

## Android Configuration Updates

### Updated Android SDK Configuration

```gradle
compileSdkVersion = 34
targetSdkVersion = 34
minSdkVersion = 24
```

### Gradle Wrapper Update

```properties
distributionUrl=https\://services.gradle.org/distributions/gradle-8.x-all.zip
```

### Android Gradle Plugin

```gradle
classpath("com.android.tools.build:gradle:8.x.x")
```

### Kotlin Version

```gradle
ext.kotlinVersion = "1.9.x"
```

### Hermes Enablement

```gradle
enableHermes: true
```

### Packaging Updates

```gradle
packagingOptions {
    pickFirst '**/*.so'
}
```

---

## iOS Configuration Updates

### Updated iOS Deployment Target

```ruby
platform :ios, '14.0'
```

### Pod Install Configuration

```ruby
use_frameworks! :linkage => :static
```

### Hermes Configuration

```ruby
:hermes_enabled => true
```

### Pod Installation

```bash
cd ios
pod install --repo-update
```

---

## Metro Bundler Changes

Updated Metro configuration to support:

* New asset resolution
* Improved transformer support
* Modern package exports
* SVG/asset handling compatibility

---

## New Architecture Considerations

> Optional depending on project readiness.

### Evaluated Features

* Fabric Renderer
* TurboModules
* Bridgeless architecture

### Current Status

```text
New Architecture: Disabled / Planned for future migration
```

---

# Breaking Changes & Fixes

## Deprecated APIs Replaced

| Deprecated API            | Replacement                    |
| ------------------------- | ------------------------------ |
| componentWillMount        | useEffect / componentDidMount  |
| componentWillReceiveProps | useEffect                      |
| UIManager direct calls    | Updated native module handling |
| Legacy Linking APIs       | Updated Linking module         |

---

## Navigation Migration

### Updated Navigation APIs

* Migrated from older stack APIs
* Updated screen registration patterns
* Updated deep linking configuration

⚠️ **Important:** Navigation state persistence logic required manual adjustment.

---

## Metro Bundler Updates

### Changes Applied

* Updated metro.config.js
* Babel configuration alignment
* Asset transformer compatibility fixes

---

## Permission Handling Updates

### Android Permissions

Updated runtime permission handling for:

* Notifications
* Media access
* Storage permissions
* Camera access

### iOS Permissions

Updated:

* Info.plist entries
* Permission usage descriptions

---

## Library Compatibility Fixes

### Manual Fixes Applied

* Reanimated Babel plugin ordering fix
* Gesture handler root view updates
* Android namespace migration
* Flipper removal for release stability
* Legacy package replacements

---

# Testing & Validation

## Android Build Verification

```bash
cd android
./gradlew clean
./gradlew assembleDebug
./gradlew assembleRelease
```

---

## iOS Build Verification

```bash
cd ios
pod install
xcodebuild clean
```

Build verified using:

* Debug mode
* Release mode
* Physical device testing

---

# Smoke Testing Checklist

* [x] App launch
* [x] Authentication flow
* [x] API integration
* [x] Navigation flow
* [x] Push notifications
* [x] Deep linking
* [x] Offline handling
* [x] Camera/gallery access
* [x] Background/foreground transitions

---

# Regression Testing Notes

Validated:

* Existing business workflows
* API integrations
* Redux/state persistence
* Crash-free startup
* Performance baselines

---

# Performance Validation

## Verified Metrics

* App startup performance
* Memory usage
* Screen rendering performance
* APK/IPA size impact
* Bundle generation stability

---

# Known Issues

## Temporary Workarounds

| Issue                                          | Workaround          |
| ---------------------------------------------- | ------------------- |
| Some third-party packages not fully compatible | Patched temporarily |
| Flipper instability                            | Disabled            |
| Legacy native modules                          | Pending migration   |

---

## Future Cleanup Tasks

* Remove deprecated utility wrappers
* Enable New Architecture evaluation
* Migrate remaining legacy native modules
* Dependency optimization cleanup

---

# Rollback Plan

## Backup Strategy

Before upgrade:

* Git branch backup created
* Release tag generated
* Production APK/IPA archived

---

## Git Tagging

```bash
git tag rn-0.63-backup
git push origin rn-0.63-backup
```

---

## Rollback Steps

If deployment fails:

```bash
git checkout rn-0.63-backup
yarn install
cd ios && pod install
```

Rebuild application and redeploy previous stable version.

---

# Setup Instructions

## Install Dependencies

```bash
yarn install
```

or

```bash
npm install
```

---

## Install iOS Pods

```bash
cd ios
pod install --repo-update
cd ..
```

---

# Running the Application

## Start Metro

```bash
yarn start
```

---

## Run Android

```bash
yarn android
```

---

## Run iOS

```bash
yarn ios
```

---

# Clear Cache Commands

## Metro Cache

```bash
yarn start --reset-cache
```

## Android Clean

```bash
cd android
./gradlew clean
```

## iOS Clean

```bash
cd ios
xcodebuild clean
```

---

# Recommended Commit Message

## Conventional Commit

```text
chore: upgrade React Native from 0.63 to 0.77
```

## Detailed Commit Description

```text
- Upgraded React Native from 0.63 to 0.77
- Updated Android Gradle Plugin and Gradle wrapper
- Migrated project to JDK 17 and Kotlin 1.9
- Enabled Hermes engine
- Updated iOS Pod configurations
- Refactored deprecated APIs
- Updated navigation and gesture handler dependencies
- Applied Metro and Babel configuration changes
- Fixed native build compatibility issues
- Performed Android and iOS regression testing
```

---

# Pull Request Description

## Summary

This PR upgrades the React Native application from version 0.63 to 0.77 to modernize the application stack and improve platform compatibility, performance, and maintainability.

---

## Scope of Upgrade

* React Native core upgrade
* Android native build modernization
* iOS dependency updates
* Hermes enablement
* Dependency compatibility alignment
* Metro/Babel configuration updates

---

## Major Dependency Updates

* React Native 0.63 → 0.77
* React 16 → 18
* Navigation library updates
* Reanimated migration
* Gesture Handler migration

---

## Risks

* Third-party native module compatibility
* Navigation behavior regressions
* Platform-specific runtime issues
* CI/CD pipeline adjustments

---

## Testing Completed

* Android debug/release build validation
* iOS debug/release build validation
* Smoke testing
* Regression testing
* Performance verification

---

# Final Notes

## Recommendations for Future Upgrades

* Avoid large version gaps between upgrades
* Upgrade React Native incrementally every 3–6 months
* Monitor deprecated APIs continuously
* Maintain dependency compatibility matrix
* Keep Android/iOS tooling aligned with RN releases

---

## Suggested Maintenance Practices

* Run dependency audits regularly
* Automate build validation in CI/CD
* Use Renovate/Dependabot for monitoring
* Maintain release notes for every framework upgrade
* Validate third-party package support before upgrades

---

# References

* React Native Upgrade Helper
* React Native Official Documentation
* Android Developer Documentation
* Apple iOS Developer Documentation

---

# Maintainers

| Name             | Role                  |
| ---------------- | --------------------- |
| [Ganesh Patil] | Mobile Architect      |


---
