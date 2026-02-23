# {{APP_NAME}} — iOS App Genesis Prompt

## 1. Project Overview

Build an iOS app called **"{{APP_NAME}}"** — {{APP_ONE_LINE_DESCRIPTION}}.

{{APP_DETAILED_DESCRIPTION}}

---

## 2. Technical Requirements

- **iOS version:** iOS 17+
- **Framework:** SwiftUI
- **Architecture:** MVVM with Swift Concurrency (async/await, actors)
- **Device support:** iPhone and iPad compatible (responsive layout)
- **Orientation:** {{ORIENTATION}}
  &lt;!-- e.g., "Portrait primary, iPad supports landscape" / "Landscape only" --&gt;
- **StoreKit 2** for In-App Purchases
- **AVSpeechSynthesizer** for Text-to-Speech (if applicable)
- **UserDefaults + FileManager** for local persistence
- **No backend required** unless explicitly noted below

### Additional Frameworks (app-specific)

{{ADDITIONAL_FRAMEWORKS}}

*Examples:*
- *AVFoundation + AudioToolbox for real-time audio generation*
- *URLSession for external API calls (e.g., Claude API, weather API)*
- *Core Location for location services*
- *UserNotifications for local notifications*
- *WidgetKit for home screen widgets*
- *AppIntents for Siri Shortcuts*
- *AdMob / Google Mobile Ads SDK for ad monetization*

### Required Xcode Capabilities

- In-App Purchase
- {{ADDITIONAL_CAPABILITIES}}

*Examples: Push Notifications, Background Modes: Audio, Location Services.*

---

## 3. Design System

### Color Palette

```swift
{{COLOR_PALETTE}}
```

*Define both Light and Dark mode values if applicable. Example keys:
background, surface, textPrimary, textSecondary, accent, accentLight, divider.
Plus any app-specific colors (layer indicators, category tints, etc.)*

### Typography

```swift
{{TYPOGRAPHY}}
```

*Define font families, sizes, weights for:
Headlines/titles, Body text, UI labels/buttons,
Any special-purpose text (serif reading fonts, rounded child-friendly fonts, etc.)*

### Spacing &amp; Touch Targets

- Horizontal padding: {{HORIZONTAL_PADDING}}pt
- Minimum touch target: {{MIN_TOUCH_TARGET}}pt (44pt default, 60pt+ for child apps)
- Card internal padding: 16pt, gaps: 12pt
- Paragraph spacing (if reading app): 20pt

### Animations

- Screen transitions: 0.3s ease-out fade
- Interactive elements: subtle scale (0.98) on press
- Loading states: gentle pulse animation
- {{ANIMATION_PHILOSOPHY}}
  *e.g., "No jarring animations—everything should feel mindful" / "Organic wave visualizations"*

### App Icon Concept

{{APP_ICON_DESCRIPTION}}

---

## 4. App Structure

```
{{APP_NAME}}/
├── {{APP_NAME}}App.swift
├── Models/
│   ├── {{MODEL_FILES}}
│   └── ...
├── Views/
│   ├── {{VIEW_FILES_AND_SUBFOLDERS}}
│   └── ...
├── Services/
│   ├── StoreKitManager.swift
│   ├── {{SERVICE_FILES}}
│   └── ...
├── Data/
│   └── {{DATA_FILES}}
└── Assets.xcassets/
```

*List all model, view, and service files relevant to your app.
Include subfolder organization (e.g., Views/Home/, Views/Settings/, Views/Paywall/).*

---

## 5. Data Models

{{DATA_MODELS}}

*Define all Swift structs, enums, and classes with their properties.
Include Identifiable, Codable conformances.
Include computed properties and helper methods.*

---

## 6. Screen Specifications

{{SCREEN_SPECIFICATIONS}}

*For each screen, specify:*
- *Layout description (scroll view, split view, tab view, etc.)*
- *Component breakdown with visual hierarchy*
- *User interaction flows*
- *State variations (free vs. premium, empty vs. populated, online vs. offline)*
- *ASCII mockups where helpful*

---

## 7. In-App Purchase Configuration

### Product IDs

```swift
// Bundle identifier base: {{BUNDLE_ID}}

{{IAP_PRODUCT_IDS}}
```

*Examples:*
- *Non-consumable: "com.domain.app.featurename" at $X.XX*
- *Auto-renewable subscription: "com.domain.app.premium.monthly" at $X.XX/month*
- *Bundle: "com.domain.app.bundle.all" at $X.XX*

### StoreKit 2 Implementation

Use the modern StoreKit 2 Swift API:
- `Product.products(for:)` to load products
- `product.purchase()` for transactions
- `Transaction.currentEntitlements` for checking active purchases
- Listen for `Transaction.updates` for real-time transaction handling
- `AppStore.sync()` for restore purchases

### Purchase Flow

1. User taps locked feature / content
2. {{PARENTAL_GATE_STEP}}
   *("Show parental gate (math challenge) — required for Kids apps" or "N/A")*
3. Present purchase sheet with feature preview, price, and "Buy" button
4. {{BUNDLE_UPSELL}}
   *("Also show 'Get All Packs — $X.XX' option" or "N/A")*
5. Process purchase via StoreKit 2
6. On success, unlock content and persist state
7. Include "Restore Purchases" button in Settings and Paywall

### Premium State Management

- Store purchase status with receipt validation
- Check entitlements on app launch
- Update UI reactively via `@Published` / `@Observable`

### Paywall Design

{{PAYWALL_DESCRIPTION}}

*Describe the paywall screen: what triggers it, layout, feature comparison,
pricing display, CTA button styling, restore purchases link, terms &amp; privacy links.*

---

## 8. Ad Monetization (if applicable)

{{AD_CONFIGURATION}}

*If using ads, specify:*
- *Ad SDK (e.g., Google AdMob)*
- *Ad types and placements (banner, interstitial, app open, rewarded)*
- *Frequency caps*
- *Ad unit IDs (test + production placeholders)*
- *Premium vs free ad visibility matrix*
- *Revenue model estimates*
- *SDK setup instructions (CocoaPods/SPM, Info.plist keys, initialization)*

*If no ads: "No ads. Revenue is IAP-only."*
*If Kids App: "No behavioral advertising permitted (Kids App compliance)."*

---

## 9. App-Specific Core Features

{{CORE_FEATURES}}

*This is where the unique functionality of your app goes. Examples:*
- *Audio engine with signal generation layers*
- *AI API integration with system prompts*
- *Text-to-speech with multi-language support*
- *Content browsing with reading progress*
- *Real-time visualizations*
- *Offline caching strategies*
- *Timer/scheduler functionality*
- *Widget and Siri Shortcuts integration*
- *Location-based features*

---

## 10. Content / Data Specification

{{CONTENT_SPECIFICATION}}

*Define all bundled content:*
- *Stories, vocabulary items, audio presets, etc.*
- *Content categories and distribution*
- *Content format (fields per item)*
- *Source attribution and licensing*
- *Placeholder vs. final content strategy*

---

## 11. Settings Screen

**Sections:**

{{SETTINGS_SECTIONS}}

*Common sections:*
- *App-specific preferences (voice, speed, theme, etc.)*
- *Notification preferences (if applicable)*
- *Account: Restore Purchases, Subscription status*
- *About: App version, Acknowledgments, Privacy Policy link, Rate App link*

### Cross-Promotion Banner (Settings footer)

```
┌─────────────────────────────────────────────────┐
│ [App Icon]  {{PROMO_TEXT}}                      │
│                                           →     │
└─────────────────────────────────────────────────┘
```

- Full width, tappable
- Opens App Store via `SKStoreProductViewController` or `UIApplication.shared.open(url)`
- {{PROMO_PARENTAL_GATE}}
  *("Behind parental gate (Kids apps)" or "Direct link")*
- Cross-promoted app URL: {{PROMO_APP_URL}}
- Subtle styling, does not dominate the settings screen

---

## 12. Persistence

### UserDefaults Keys

```swift
enum StorageKeys {
    static let isPremium = "isPremium"
    {{ADDITIONAL_STORAGE_KEYS}}
}
```

### File Storage (if needed)

{{FILE_STORAGE_STRATEGY}}

*Examples: Documents directory for progress JSON files,
Cached API responses for offline access,
Keychain for sensitive data (reward tracking, etc.)*

---

## 13. Offline Behavior

### Works Offline
{{OFFLINE_AVAILABLE}}

*Examples: All bundled content, TTS, reading progress, cached API responses.*

### Requires Internet
{{ONLINE_REQUIRED}}

*Examples: AI API calls, purchases/restore, weather data, initial content fetch.*

### Offline Indicators
- Subtle banner when offline: "You're offline. Some features limited."
- Disable network-dependent features gracefully with user-friendly messages

---

## 14. Kids App Compliance (if applicable)

{{KIDS_COMPLIANCE}}

*If this is a Kids App, include:*
- [ ] *No third-party analytics*
- [ ] *No behavioral advertising*
- [ ] *No external links without parental gate*
- [ ] *Parental gate before IAP*
- [ ] *Privacy policy URL ready*
- [ ] *Age rating set (e.g., "Made for Kids, Ages 5 and Under")*
- [ ] *"Made for Kids" flag enabled in App Store Connect*

*If not a Kids App: "Not applicable — standard App Store guidelines apply."*

---

## 15. Build Configuration &amp; Compliance

### Encryption Export Compliance

Add to `Info.plist`:

```xml
&lt;key&gt;ITSAppUsesNonExemptEncryption&lt;/key&gt;
&lt;false/&gt;
```

This prevents the manual encryption compliance questionnaire from blocking
**every single TestFlight build** in App Store Connect. Set to `false` if the app:
- Does NOT use custom encryption
- Only uses standard HTTPS (URLSession) for network calls
- Only uses Apple-provided encryption (StoreKit, etc.)

If your app uses custom encryption beyond standard HTTPS, set to `true`
and prepare export compliance documentation.

### App Transport Security

Standard ATS is fine for most apps. If you need non-HTTPS endpoints (rare):

```xml
&lt;key&gt;NSAppTransportSecurity&lt;/key&gt;
&lt;dict&gt;
    &lt;key&gt;NSExceptionDomains&lt;/key&gt;
    &lt;dict&gt;
        &lt;!-- Add specific domains only if needed --&gt;
    &lt;/dict&gt;
&lt;/dict&gt;
```

### Background Modes (if applicable)

```xml
&lt;key&gt;UIBackgroundModes&lt;/key&gt;
&lt;array&gt;
    {{BACKGROUND_MODES}}
    &lt;!-- Examples: &lt;string&gt;audio&lt;/string&gt;, &lt;string&gt;location&lt;/string&gt; --&gt;
&lt;/array&gt;
```

### Orientation Lock (if applicable)

```xml
&lt;key&gt;UISupportedInterfaceOrientations&lt;/key&gt;
&lt;array&gt;
    {{SUPPORTED_ORIENTATIONS}}
    &lt;!-- Portrait: UIInterfaceOrientationPortrait --&gt;
    &lt;!-- Landscape: UIInterfaceOrientationLandscapeLeft, UIInterfaceOrientationLandscapeRight --&gt;
&lt;/array&gt;
```

### Privacy Usage Descriptions

Add all required `NS...UsageDescription` keys to `Info.plist`:

```xml
{{PRIVACY_USAGE_DESCRIPTIONS}}
```

*Examples: NSSpeechRecognitionUsageDescription,
NSLocationWhenInUseUsageDescription, NSMicrophoneUsageDescription.*

---

## 16. App Store Metadata

### App Identity

| Field | Value |
|-------|-------|
| **App Name** | {{APP_NAME}} |
| **Bundle ID** | {{BUNDLE_ID}} |
| **Subtitle** | {{APP_SUBTITLE}} (max 30 characters) |
| **Primary Category** | {{PRIMARY_CATEGORY}} |
| **Secondary Category** | {{SECONDARY_CATEGORY}} |
| **Age Rating** | {{AGE_RATING}} |

### Description

```
{{APP_STORE_DESCRIPTION}}
```

*Write a compelling App Store description:*
- *Lead with the value proposition (first 3 lines visible before "more")*
- *Feature highlights*
- *Free vs. premium comparison*
- *Honest disclaimers if applicable*
- *4000 character max*

### Promotional Text

```
{{PROMOTIONAL_TEXT}}
```

*170 characters max. Can be updated without a new app version.*

### Keywords

```
{{KEYWORDS}}
```

*100 characters max, comma-separated. No spaces after commas.
Focus on discoverability. Avoid repeating words from app name.*

### What's New (for updates)

```
{{WHATS_NEW}}
```

### App Review Notes

```
{{APP_REVIEW_NOTES}}
```

*Include anything the review team needs to know:*
- *How to test IAP (sandbox account if needed)*
- *Explanation of non-obvious features*
- *Disclaimers (e.g., health/science claims)*
- *Background audio justification*
- *Demo credentials if login required*

### Screenshots Specification

| Device | Size | Orientation | Count |
|--------|------|-------------|-------|
| iPhone 6.9" | 1320 × 2868 | {{ORIENTATION}} | 6-10 |
| iPhone 6.7" | 1290 × 2796 | {{ORIENTATION}} | 6-10 |
| iPad 13" | 2064 × 2752 | {{ORIENTATION}} | 6-10 |

*Plan screenshot content:*
1. *Hero shot (main feature)*
2. *Key feature #1*
3. *Key feature #2*
4. *Premium/paywall value prop*
5. *Settings/customization*
*(Continue as needed, up to 10 per device)*

### Privacy Nutrition Label

```
{{PRIVACY_NUTRITION_LABEL}}
```

*Options:*
- *"Data Not Collected: We do not collect any data from this app."*
- *Or specify: Data Used to Track You / Data Linked to You / Data Not Linked to You*

### Privacy Policy URL

{{PRIVACY_POLICY_URL}}

### Support URL

{{SUPPORT_URL}}

### Marketing URL (optional)

{{MARKETING_URL}}

---

## 17. Data &amp; Privacy Compliance

- {{DATA_COLLECTION_POLICY}}
  *e.g., "No personal data collected" / "Location used on-device only"*
- {{ANALYTICS_POLICY}}
  *e.g., "No analytics SDK" / "Firebase Analytics with anonymized data"*
- App Tracking Transparency: {{ATT_REQUIRED}}
  *"NOT required (no tracking)" / "Required — implement ATT prompt"*
- GDPR/CCPA: {{GDPR_NOTES}}

---

## 18. Implementation Priority

### Phase 1: Core Experience
{{PHASE_1_TASKS}}

### Phase 2: Polish &amp; Secondary Features
{{PHASE_2_TASKS}}

### Phase 3: Monetization
{{PHASE_3_TASKS}}

### Phase 4: Final Polish &amp; Submission
- Dark mode support (if not already implemented)
- iPad layout optimization
- Accessibility (VoiceOver, Dynamic Type)
- Error handling and edge cases
- App Store assets (screenshots, preview video)
- TestFlight beta testing

---

## 19. Build &amp; Release Checklist

### Pre-Submission
- [ ] All core features functional and tested
- [ ] StoreKit 2 purchases work in sandbox
- [ ] Restore purchases works
- [ ] `ITSAppUsesNonExemptEncryption` set to `false` in Info.plist
- [ ] Privacy nutrition labels accurate in App Store Connect
- [ ] Privacy policy URL is live and accessible
- [ ] App Review notes written
- [ ] All placeholder values replaced (API keys, product IDs, URLs)
- [ ] No test/debug code in release build
- [ ] Performance profiled with Instruments
- {{ADDITIONAL_CHECKLIST_ITEMS}}

### App Store Connect Setup
- [ ] App record created with correct Bundle ID
- [ ] In-App Purchase products created and approved
- [ ] Screenshots uploaded for all required device sizes
- [ ] Description, keywords, and promotional text finalized
- [ ] Age rating questionnaire completed
- [ ] Pricing and availability set
- [ ] App Review information filled in (contact, notes, demo account)
- [ ] Build uploaded and selected
- [ ] Submit for review

---

## 20. App Entry Point

```swift
// Note: the struct name must be valid Swift — PascalCase, no spaces or hyphens.
// e.g., "Zen Tales" becomes ZenTalesApp, "MosquiGo" becomes MosquiGoApp.
@main
struct {{APP_NAME}}App: App {
    @StateObject private var storeManager = StoreKitManager()
    {{ADDITIONAL_STATE_OBJECTS}}

    var body: some Scene {
        WindowGroup {
            {{ROOT_VIEW}}()
                .environmentObject(storeManager)
                {{ADDITIONAL_ENVIRONMENT_OBJECTS}}
                .onAppear {
                    Task {
                        await storeManager.checkEntitlement()
                    }
                }
        }
    }
}
```

---

## 21. Deliverable

A complete, buildable Xcode project with:
- All core functionality implemented
- Full UI matching design spec
- StoreKit 2 IAP setup (with placeholder product IDs)
- {{ADDITIONAL_DELIVERABLES}}
- Light and dark mode support
- Placeholder content where final content is pending
- All `{{PLACEHOLDER}}` values documented for easy replacement before release

---

## 22. Placeholder Reference

Before submission, search the project for `{{` and replace all placeholders:

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `YOUR_API_KEY` | External API key | Obfuscated in production |
| `com.domain.app.*` | Product IDs | Match App Store Connect |
| `PROMO_APP_ID` | Cross-promoted app's App Store ID | `id6504167889` |
| `PRIVACY_POLICY_URL` | Live privacy policy page | `https://yourdomain.com/privacy` |
| {{ADDITIONAL_PLACEHOLDERS}} | | |

---

## 23. Notes

{{ADDITIONAL_NOTES}}

*Any final notes, known limitations, future roadmap ideas, scientific references,
third-party attribution, or other context the builder needs.*

