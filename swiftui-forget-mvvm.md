---
title: SwiftUI in 2025: Forget MVVM
anchor: Why you don't need ViewModels in SwiftUI - argument against MVVM
tags: [swiftui, mvvm, architecture, ios, macos, opinion, thomas-ricouard]
description: Thomas Ricouard argues SwiftUI doesn't need MVVM - uses IcySky (BlueSky client) and Medium iOS app as examples
source_url: https://dimillian.medium.com/swiftui-in-2025-forget-mvvm-262ff2bbd2ed
---

## Summary

Thomas Ricouard (Dimillian) argues that **SwiftUI doesn't need ViewModels**. He's the author of IcySky (BlueSky client) and maintains the Medium iOS app — both use SwiftUI without traditional ViewModels.

## Key Arguments

### 1. SwiftUI Was Designed Differently
SwiftUI was designed with a **declarative, data-driven philosophy** from WWDC 2019 (Data Flow Through SwiftUI). It has built-in data flow mechanisms that make separate ViewModels unnecessary.

### 2. ViewModels Are UIKit Baggage
When SwiftUI launched in 2019, developers brought their UIKit patterns:
- "We were so used to the Massive View Controller (MVC) problem that we immediately reached for MVVM as our savior."
- But SwiftUI isn't UIKit — it has its own philosophy.

### 3. SwiftUI Has Built-In Data Flow
SwiftUI provides:
- **@State** — Local view state
- **@Binding** — Shared state between views
- **@ObservedObject / @StateObject** — External observable data
- **@EnvironmentObject** — Global services/data
- **@Environment** — System services and settings

These replace the need for manual ViewModel orchestration.

### 4. Better Alternatives
Instead of ViewModels, use:
- **@Observable macro** (iOS 17+) — Plain classes, no ObservableObject boilerplate
- **Services** (via @Environment) — Business logic in injectables
- **@State** for local state
- **@Bindable** for two-way binding

## Example: No ViewModel Pattern

```swift
// Plain SwiftUI view with services
struct ContentView: View {
    @Environment(\.apiService) private var api
    @State private var items: [Item] = []
    
    var body: some View {
        List(items) { item in
            Text(item.name)
        }
        .task {
            items = await api.fetchItems()
        }
    }
}
```

## Contrast with MVVM

| MVVM Pattern | SwiftUI Alternative |
|--------------|---------------------|
| ViewModel | Plain @Observable class or struct |
| @Published | @State, @Bindable |
| @ObservedObject | @Environment(\.service) |
| Coordinator | NavigationPath |

## Author's Projects

- **IcySky** — BlueSky client (https://github.com/Dimillian/IcySky)
- **Medium iOS app** — Production app without ViewModels

## Community Response

Reddit discussions note:
- "The injected @Environment things ARE observable ViewModels, except they're called 'services.'"
- ViewModels aren't new, but they're useful bridges for UIKit → SwiftUI transition
- Debate continues on when ViewModels are still useful

## For Your SwiftUI Skills

This aligns with the **Dimillian/Skills** approach:
- Use plain services via @Environment
- Leverage @Observable macro (iOS 17+)
- Keep views simple, push logic to services
- No @Published or ObservableObject boilerplate

## Related

- Apple WWDC 2019: Data Flow Through SwiftUI
- IcySky GitHub: https://github.com/Dimillian/IcySky
- @Observable macro (iOS 17+)
