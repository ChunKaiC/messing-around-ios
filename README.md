# messing-around-ios

A sandbox for learning native iOS development with Swift and SwiftUI. One Xcode project per numbered folder, each introducing concepts the previous ones didn't.

## Goals

- Write idiomatic Swift: value types, optionals, protocol-oriented design, generics, concurrency.
- Think in SwiftUI: declarative layout, state ownership, data flow, navigation.
- Build complete apps that handle empty and error states and survive a relaunch.
- Learn the platform: persistence, networking, notifications, widgets, system frameworks.
- Ship: tests, accessibility, profiling, TestFlight.

## Milestones

- [ ] **1. Fundamentals.** Swift basics, protocols and conformance, views and modifiers, stacks, `@State`/`@Binding`, basic controls.
- [ ] **2. Lists, navigation, data flow.** `List`, `NavigationStack`, sheets, `@Observable`, `@Environment`. Protocol-oriented programming: protocol extensions, constrained generics, `some` vs `any`, composition over inheritance.
- [ ] **3. Persistence.** `@AppStorage`, `Codable`, SwiftData (`@Model`, `@Query`, relationships).
- [ ] **4. Networking and concurrency.** `URLSession`, `async`/`await`, `.task` and cancellation, `@MainActor`, `Sendable`, actors.
- [ ] **5. Polish.** Animation, gestures, Swift Charts, dark mode, Dynamic Type, VoiceOver.
- [ ] **6. System frameworks.** Notifications, WidgetKit, App Intents, MapKit, Core Location, HealthKit.
- [ ] **7. Shipping.** Swift Testing, dependency injection, local Swift packages, Instruments, TestFlight.

## Projects

| # | Project | Milestone | What it teaches |
|---|---------|-----------|-----------------|
| 1 | Tip Calculator | 1 | State driving UI, forms, currency formatting |
| 2 | To-Do List | 2 | Lists, navigation, shared state, a `TaskStore` protocol backed by JSON |
| 3 | Habit Tracker | 3, 5 | SwiftData, streak logic with unit tests, a Swift Charts heatmap |
| 4 | Weather App | 4 | Networking, loading and error states, location permissions, a `WeatherService` protocol with live and mock implementations |
| 5 | Pomodoro Timer | 5, 6 | Animation, background behaviour, notifications, Live Activities |
| 6 | Run Tracker | 6 | MapKit, background location, HealthKit (needs a real device) |
| 7 | Capstone | 7 | An app you'd actually use: local packages, tested logic layer, accessibility, TestFlight build |

## Working rules

- Finish a project before starting the next: it runs, handles bad input, and has a short README.
- Type the code rather than pasting it.
- Revisit earlier projects and refactor them as you learn more.

## Resources

- [The Swift Programming Language](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/)
- [100 Days of SwiftUI](https://www.hackingwithswift.com/100/swiftui)
- [Apple's SwiftUI tutorials](https://developer.apple.com/tutorials/swiftui)
- [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
