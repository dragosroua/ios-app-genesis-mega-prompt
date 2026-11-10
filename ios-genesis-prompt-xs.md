# {{APP_NAME}} — iOS App

## Overview
Build a complete iOS app called **{{APP_NAME}}**.

{{APP_ONE_LINE_DESCRIPTION}}

{{APP_DETAILED_DESCRIPTION}}

## Technical Requirements
- iOS 17+
- SwiftUI
- MVVM with Swift Concurrency (async/await)
- iPhone primary, responsive for iPad
- {{ORIENTATION}}
- StoreKit 2 for IAP (if monetized)
- UserDefaults + FileManager for persistence
- No backend unless specified

Additional frameworks: {{ADDITIONAL_FRAMEWORKS}}

## Design System
- Colors: {{COLOR_PALETTE}} (support light/dark)
- Typography: system fonts, clear hierarchy (title, body, caption)
- Spacing: 16pt horizontal padding, 12pt gaps, 44pt min touch targets
- Animations: simple 0.3s transitions

## Data Models
{{DATA_MODELS}}

Use simple Codable structs. Keep them small.

## Screens
{{SCREEN_SPECIFICATIONS}}

For each screen include:
- Layout description
- Main interactions
- Empty / loading / error states where relevant

## Core Features
{{CORE_FEATURES}}

## Persistence
Store these in UserDefaults or files:
{{STORAGE_KEYS_AND_STRATEGY}}

## IAP (if applicable)
Product IDs: {{IAP_PRODUCT_IDS}}

Use StoreKit 2. Unlock content after purchase and persist the state.

## Implementation Notes
- Generate a working Xcode project structure
- Prefer clean, readable SwiftUI
- Use @State, @Observable, or @StateObject appropriately
- Add basic error handling
- Make it compile and run

## Output
1. List the files you will create
2. Then write the full code for each file
3. Keep comments minimal
