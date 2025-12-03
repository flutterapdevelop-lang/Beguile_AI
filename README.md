# Beguile AI - iOS Build Guide

## Quick Reference
| Field | Value |
|-------|-------|
| **Bundle ID** | `com.beguile.app` |
| **App Name** | Beguile AI |
| **Min iOS** | 15.5 |
| **Flutter SDK** | ≥3.10.0 |
| **Dart SDK** | ≥3.0.0 <4.0.0 |

---

## Prerequisites

- macOS with Xcode 15+ installed
- Flutter SDK 3.10.0 or higher
- CocoaPods installed (`sudo gem install cocoapods`)
- Apple Developer Account with valid provisioning profiles
- Firebase `GoogleService-Info.plist` (already included in `ios/Runner/`)

---

## Build Steps

### 1. Install Dependencies
```bash
flutter pub get
```

### 2. Install iOS Pods
```bash
cd ios
pod install --repo-update
cd ..
```

### 3. Open in Xcode
```bash
open ios/Runner.xcworkspace
```

### 4. Configure Signing
In Xcode:
1. Select **Runner** target
2. Go to **Signing & Capabilities**
3. Select your **Team**
4. Ensure Bundle Identifier is `com.beguile.app`
5. Let Xcode manage signing or configure your provisioning profiles

### 5. Build for Release
```bash
flutter build ios --release
```

Or archive from Xcode:
- **Product → Archive** (with a real device selected or "Any iOS Device")

---

## Firebase Setup
The app uses Firebase for:
- Authentication (Email, Google Sign-In, Apple Sign-In)
- The `GoogleService-Info.plist` is already in `ios/Runner/`

If you need to regenerate:
1. Go to Firebase Console → Project Settings → iOS app
2. Download `GoogleService-Info.plist`
3. Replace `ios/Runner/GoogleService-Info.plist`

---

## In-App Purchases
The app uses `in_app_purchase` package. Make sure your App Store Connect has:
- In-app purchase products configured
- Agreements signed

---

## Key Dependencies
| Package | Purpose |
|---------|---------|
| `firebase_auth` | Authentication |
| `google_sign_in` | Google Sign-In |
| `sign_in_with_apple` | Apple Sign-In |
| `in_app_purchase` | Subscriptions/IAP |
| `flutter_riverpod` | State management |
| `go_router` | Navigation |
| `hive_flutter` | Local storage |

---

## Troubleshooting

### Pod Install Fails
```bash
cd ios
rm -rf Pods Podfile.lock
pod cache clean --all
pod install --repo-update
```

### Signing Issues
- Ensure certificates are valid in Keychain
- Check provisioning profiles in Apple Developer portal
- Bundle ID must match: `com.beguile.app`

### Build Errors
```bash
flutter clean
flutter pub get
cd ios && pod install --repo-update && cd ..
flutter build ios --release
```

---

## App Store Submission Checklist
- [ ] Screenshots for all required device sizes
- [ ] App icon (already configured in `Assets.xcassets`)
- [ ] Privacy Policy URL
- [ ] App Store description
- [ ] In-app purchase products configured
- [ ] Sign-in with Apple configured in Capabilities

---

## Contact
Reach out if you have questions about the codebase or build process.
