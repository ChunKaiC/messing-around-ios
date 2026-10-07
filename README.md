# messing-around-ios

A sandbox for learning native iOS development with Swift and SwiftUI. Each project lives in its own folder and is small enough to finish, but each one introduces a few concepts the previous ones didn't.

## Goals

- **Write idiomatic Swift.** Value types, optionals, protocol-oriented design, generics, closures, error handling, and structured concurrency (`async`/`await`, actors).
- **Think in SwiftUI.** Declarative layout, state ownership, data flow, navigation, and animation, without reaching for UIKit by default.
- **Build complete apps, not tutorials.** Every project should launch, handle empty and error states, and survive a relaunch.
- **Learn the platform, not just the UI framework.** Persistence, networking, notifications, widgets, sensors, and system frameworks.
- **Pick up professional habits.** Testing, previews, accessibility, localization, Instruments, and shipping through TestFlight.

## Setup

- Xcode 26 or later, targeting the latest iOS SDK
- An iPhone simulator for most projects; a physical device for anything using sensors, camera, notifications, or HealthKit
- A free Apple ID is enough to run on a device; a paid developer account is only needed from Milestone 6 onward

## Repo layout

```
messing-around-ios/
├── README.md
├── 01-tip-calculator/
├── 02-.../
└── notes/            # things learned, gotchas, links worth keeping
```

One Xcode project per numbered folder. Each project gets a short `README.md` covering what it does, what it was meant to teach, and what was hard.

## Milestones

### Milestone 1: Swift and SwiftUI fundamentals

- [ ] Swift basics: `let`/`var`, optionals, structs vs classes, enums with associated values, closures
- [ ] Protocols and conformance: `Identifiable`, `Hashable`, `Equatable`, `Codable`, and writing your own
- [ ] Views, modifiers, and why modifier order matters
- [ ] Layout with `VStack`, `HStack`, `ZStack`, `Spacer`, and `Grid`
- [ ] Local state with `@State` and passing it down with `@Binding`
- [ ] Controls: `TextField`, `Picker`, `Toggle`, `Slider`, `Button`
- [ ] Xcode previews and the simulator

### Milestone 2: Lists, navigation, and data flow

- [ ] `List`, `ForEach`, `Identifiable`, swipe actions, and edit mode
- [ ] `NavigationStack` with value-based navigation and `navigationDestination`
- [ ] Sheets, alerts, and confirmation dialogs
- [ ] Shared state with `@Observable`, `@Bindable`, and `@Environment`
- [ ] Separating model, view, and logic so views stay small

Protocol-oriented programming:

- [ ] Protocol extensions and default implementations
- [ ] Generics with constraints and associated types
- [ ] `some` vs `any`: opaque types and existentials, and when each is appropriate
- [ ] Composition over inheritance: small protocols combined, instead of class hierarchies
- [ ] Protocols as seams: hiding storage or networking behind a protocol so it can be swapped or mocked

### Milestone 3: Persistence

- [ ] `@AppStorage` and `UserDefaults` for small settings
- [ ] `Codable` and writing JSON to the documents directory
- [ ] SwiftData: `@Model`, `@Query`, relationships, and migrations
- [ ] Search, sorting, and filtering

### Milestone 4: Networking and concurrency

- [ ] `URLSession` with `async`/`await`, decoding JSON with `Codable`
- [ ] Loading, empty, and error states as an explicit enum
- [ ] `.task`, cancellation, and `@MainActor`
- [ ] `AsyncImage`, pagination, pull to refresh
- [ ] Swift 6 strict concurrency: `Sendable`, actors, and data-race safety

### Milestone 5: Polish

- [ ] Animations, transitions, and `matchedGeometryEffect`
- [ ] Gestures and custom drawing with `Shape` and `Canvas`
- [ ] Swift Charts
- [ ] Dark mode, Dynamic Type, VoiceOver, and localization
- [ ] Custom `ViewModifier`s and reusable components

### Milestone 6: System frameworks

- [ ] Local notifications
- [ ] WidgetKit and App Intents
- [ ] MapKit and Core Location
- [ ] Camera and PhotosUI
- [ ] HealthKit or Core Motion
- [ ] Bridging to UIKit with `UIViewRepresentable` when SwiftUI falls short

### Milestone 7: Shipping

- [ ] Unit tests with Swift Testing and UI tests with XCUITest
- [ ] Dependency injection so logic is testable without the network
- [ ] Swift Package Manager: splitting an app into local packages
- [ ] Profiling with Instruments (hangs, memory, SwiftUI view updates)
- [ ] CloudKit sync, Sign in with Apple, or a custom backend
- [ ] App icons, privacy manifests, TestFlight, and an App Store submission

## Projects

Ordered by difficulty. The table is the plan; details for each are below.

| # | Project | Milestone | Main concepts |
|---|---------|-----------|---------------|
| 1 | Tip Calculator | 1 | `@State`, forms, formatting |
| 2 | Dice and Coin | 1 | Buttons, randomness, basic animation |
| 3 | Unit Converter | 1 | `Picker`, `Measurement`, computed properties |
| 4 | Guess the Flag | 1 | Images, alerts, game state |
| 5 | To-Do List | 2 | `List`, navigation, `@Observable`, storage protocol |
| 6 | Flashcards | 2 | Sheets, gestures, data flow between screens |
| 7 | Habit Tracker | 3 | SwiftData, `@Query`, date math |
| 8 | Expense Tracker | 3, 5 | Relationships, filtering, Swift Charts |
| 9 | Weather App | 4 | `URLSession`, `async`/`await`, Core Location, service protocol |
| 10 | Movie Browser | 4 | Pagination, search, image caching, favourites |
| 11 | Pomodoro Timer | 5, 6 | Timers, notifications, Live Activities |
| 12 | Drawing Pad | 5 | `Canvas`, gestures, undo/redo, export |
| 13 | Run Tracker | 6 | MapKit, background location, HealthKit |
| 14 | Recipe Box with Widgets | 6 | WidgetKit, App Intents, PhotosUI |
| 15 | Capstone | 7 | Everything, shipped to TestFlight |

### Beginner

**1. Tip Calculator.** Enter a bill, pick a tip percentage, split between people. Teaches how state drives the UI and how to format currency properly with `FormatStyle`.

**2. Dice and Coin.** Roll dice or flip a coin with a tap or a shake. First look at animation and SF Symbols.

**3. Unit Converter.** Convert length, temperature, and weight. Uses Foundation's `Measurement` API instead of hand-rolled maths, and is a good exercise in modelling with enums.

**4. Guess the Flag.** Show three flags, ask the user to pick the right one, keep score. Introduces game state, alerts, and restarting cleanly.

### Intermediate

**5. To-Do List.** Add, edit, complete, reorder, and delete tasks. The classic for a reason: it covers lists, navigation, and shared state in one go. Put persistence behind a `TaskStore` protocol: implement it with JSON first, then swap in SwiftData after Milestone 3 without touching the views.

**6. Flashcards.** Decks of cards with a swipe-to-answer study mode. Teaches drag gestures, card-stack layout, and passing data through multiple screens.

**7. Habit Tracker.** Daily habits with streaks and a calendar heatmap. First real SwiftData project; streak logic is a good target for unit tests because the date edge cases are easy to get wrong.

**8. Expense Tracker.** Log expenses by category, view monthly totals and charts. Adds model relationships, predicates, and Swift Charts.

**9. Weather App.** Current conditions and forecast for the user's location and saved cities. First networking project; use a free API such as Open-Meteo, which needs no API key. Forces you to handle permissions, loading, and failure. Define a `WeatherService` protocol with a live implementation and a mock one, so previews and tests never hit the network.

**10. Movie Browser.** Search and browse a public API such as TMDB, with detail screens and offline favourites. Covers pagination, debounced search, image caching, and combining remote data with local persistence.

### Advanced

**11. Pomodoro Timer.** Focus timer that keeps working when the app is backgrounded. Notifications, a Live Activity on the Lock Screen and Dynamic Island, and the realisation that you can't just run a `Timer` forever.

**12. Drawing Pad.** Freehand drawing with colours, stroke widths, undo/redo, and export to Photos. Deep dive into `Canvas`, gesture handling, and performance under frequent redraws.

**13. Run Tracker.** Record a run on a map with distance, pace, and splits, then save it to Health. Background location, MapKit polylines, HealthKit authorization, and battery trade-offs. Needs a real device.

**14. Recipe Box with Widgets.** Recipes with photos, ingredient scaling, and a cooking mode, plus a Home Screen widget and Siri/Shortcuts support through App Intents. Teaches app groups and sharing data between an app and its extensions.

**15. Capstone.** An app of your own choosing that you would actually use. Requirements: a modular architecture with local Swift packages, test coverage on the logic layer, sync across devices, full accessibility support, and a TestFlight build.

## Working rules

- Finish a project before starting the next one. "Finished" means it runs, handles bad input, and has a README.
- Type the code rather than pasting it.
- When something is confusing, write it down in `notes/`.
- Revisit an early project after each milestone and refactor it with what's new.

## Resources

- [The Swift Programming Language](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/) for the language itself
- [Apple's SwiftUI tutorials](https://developer.apple.com/tutorials/swiftui) and [Develop in Swift](https://developer.apple.com/tutorials/develop-in-swift)
- [100 Days of SwiftUI](https://www.hackingwithswift.com/100/swiftui) for a structured daily course
- [Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/) for how iOS apps are expected to look and behave
- [WWDC session videos](https://developer.apple.com/videos/) for anything framework-specific
