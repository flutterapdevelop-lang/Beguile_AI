# Beguile AI - iOS Build

**Bundle ID:** `com.beguile.app`  
**Min iOS:** 15.5

## Build Steps

```bash
flutter pub get
cd ios && pod install --repo-update && cd ..
open ios/Runner.xcworkspace
```

In Xcode:
1. Select your Team in Signing & Capabilities
2. Archive and upload to App Store Connect

That's it.
