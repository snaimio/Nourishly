<div align="center">

# 🍽️ Nourishly
### Native iOS Recipe Discovery & Cloud-Synced Cooking Companion

[![iOS](https://img.shields.io/badge/iOS-17.0%2B-000000?style=for-the-badge&logo=apple&logoColor=white)](https://developer.apple.com/ios/)
[![Swift](https://img.shields.io/badge/Swift-5.9%2B-F05138?style=for-the-badge&logo=swift&logoColor=white)](https://swift.org/)
[![SwiftUI](https://img.shields.io/badge/UI-SwiftUI-0071E3?style=for-the-badge&logo=swift&logoColor=white)](https://developer.apple.com/xcode/swiftui/)
[![Firebase](https://img.shields.io/badge/Backend-Firebase%20%26%20Firestore-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com/)
[![Architecture](https://img.shields.io/badge/Architecture-Clean%20MVVM-8B5CF6?style=for-the-badge)](https://developer.apple.com/)
[![License](https://img.shields.io/badge/License-MIT-CEFF00?style=for-the-badge&logoColor=black)](LICENSE)

<br/>

**A production-grade native iOS application engineered with SwiftUI, Clean MVVM architecture, Firebase Authentication, Cloud Firestore real-time sync, and RESTful API integration.**

<br/>

[Key Technical Highlights](#-key-technical-highlights) •
[Architecture & Design](#-system-architecture) •
[Feature Breakdown](#-features--capabilities) •
[Installation](#-installation--setup) •
[Author](#-author)

</div>

<br/>

---

## 📌 Executive Summary (For Recruiters & Engineering Leads)

**Nourishly** is a full-featured native iOS cooking companion and recipe exploration application designed to demonstrate modern iOS software engineering standards. It is built strictly using declarative **SwiftUI**, **Clean MVVM architectural patterns**, **Firebase Authentication & Cloud Firestore backend integration**, and **asynchronous RESTful networking**.

### 💼 Core Technical Competencies Demonstrated:
- **Clean MVVM Architecture**: Strict separation of concerns across Models, ViewModels, Service layers, and reusable UI components.
- **Full-Stack Cloud Integration**: User identity management (Email/Password & Guest Mode) via **Firebase Auth**, and persistent cloud storage for bookmarks and reviews via **Cloud Firestore**.
- **Asynchronous Networking**: Modern Swift `async/await` concurrency consuming TheMealDB RESTful API with custom JSON decoding, image caching, and graceful error boundaries.
- **Interactive UX Systems**: Step-by-step interactive Cook Mode with regex-driven intelligent timer extraction, background audio cues via **AVFoundation**, and haptic feedback.

---

## 🛠️ Technical Stack & Frameworks

| Domain | Technology / Framework | Implementation Detail |
| :--- | :--- | :--- |
| **Language & UI** | Swift 5.9+, SwiftUI | 100% Declarative UI, NavigationStack, Sheets, Modals, LazyGrids |
| **Architecture** | MVVM + Repository Pattern | `@StateObject`, `@EnvironmentObject`, `@Published`, Unidirectional Data Flow |
| **Authentication** | Firebase Authentication | Email/Password credentials, password resets, and seamless guest mode |
| **Cloud Database** | Cloud Firestore | Real-time user profiles, synced favorite lists, and personal cookbook ratings |
| **Networking** | Swift `URLSession` (REST API) | Async/await endpoints querying categories, recipe details, and random meals |
| **Media & Audio** | AVFoundation & WebKit | Audio playback for countdown timers; embedded video players for tutorials |
| **Local Storage** | `@AppStorage` / UserDefaults | Lightweight client-side preference caching (dark mode, onboarding flags) |
| **Build & Tooling** | Xcode 15+, Swift Package Manager | Modular package dependency resolution and automated schemes |

---

## 🏛️ System Architecture

The application is structured into decoupled layers to ensure testability, scalability, and clean separation of concerns:

```
Nourishly/
├── App/                     # App lifecycle & root container configuration
│   └── NourishlyApp.swift
├── Models/                  # Immutable data structures & Codable schemas
│   ├── Category.swift       # Category domain entities
│   ├── Meal.swift           # Detailed recipe specifications & ingredients
│   ├── Cookbook.swift       # User-cooked logs, ratings, and timestamped notes
│   └── User.swift           # Profile metadata and metrics
├── ViewModels/              # Observable state management & business logic
│   ├── AuthViewModel.swift  # Authentication states, session lifecycle & guest mode
│   └── MealViewModel.swift  # Search indexing, filter state & network data fetching
├── Services/                # Isolated networking and backend communication
│   ├── AuthService.swift    # Firebase Auth API handler
│   ├── FirestoreService.swift # Firestore document CRUD operations
│   ├── FirebaseManager.swift  # Singleton configuration & initialization
│   └── MealService.swift    # Async REST API client (TheMealDB)
├── Views/                   # Declarative SwiftUI view hierarchy
│   ├── Authentication/      # Sign-in, sign-up, password reset, and auth gates
│   ├── Discover/            # Categorical browsing, debounced search & meal details
│   ├── CookMode/            # Step-by-step interactive cooking HUD & smart timer
│   ├── Favorites/           # Cloud-synced user bookmarks
│   ├── Cookbook/            # Cooking history, 5-star ratings & user notes
│   ├── Profile/             # User stats dashboard, settings, and theme toggles
│   └── Components/          # Reusable cards, loading states, and error viewports
└── Resources/               # Assets catalog, colors, and configuration plists
```

---

## 📱 Features & Capabilities

### 1. 🔐 Multi-Tier Authentication & User Profiles
- **Full Credential Lifecycle**: Email/Password account creation, secure sign-in, and automated password reset workflows.
- **Frictionless Guest Mode**: Allows immediate exploration of recipe databases while seamlessly prompting sign-in when attempting to save cloud bookmarks or publish ratings.
- **Session Persistence**: Maintains verified authentication state across application restarts.

### 2. 🍳 Categorical Discovery & Debounced Search
- **Dynamic Category Explorer**: Browse meals filtered by cuisine, diet, or ingredient category.
- **Real-Time Search**: Instant recipe discovery querying RESTful endpoints with pagination support.
- **Surprise Generator**: Randomized meal suggestion module for rapid inspiration.
- **Rich Recipe Specifications**: Displays itemized ingredient measurements, preparation instructions, and direct video tutorials.

### 3. 👨‍🍳 Interactive Cook Mode with Smart Timer Detection
- **Step-by-Step Focus HUD**: Guides users through sequential culinary instructions with high-contrast readability.
- **Automated Timer Parser**: Uses regex parsing to detect cooking durations directly from text (e.g. *"simmer for 15 minutes"*) and instantiates one-tap countdown timers.
- **Audio & Haptic Alerts**: Emits acoustic alerts via `AVAudioPlayer` and physical haptics upon timer completion.

### 4. ❤️ Cloud-Synced Favorites & Personal Cookbook
- **Multi-Device Synchronization**: User bookmarks are synced to Cloud Firestore in real time.
- **Personal Culinary Log**: Automatically records completed recipes into a persistent personal Cookbook.
- **Rating & Review System**: Enables users to attach 1–5 star ratings and custom culinary notes with full editing capabilities.

---

## 🚀 SwiftUI Component Mastery

The user interface leverages modern SwiftUI constructs:
- `NavigationStack` for type-safe path navigation.
- `.searchable(text:)` for integrated search experiences.
- `TabView` with custom accent styling and dynamic badges.
- `AsyncImage` with progressive placeholder loading and image caching.
- `LazyVGrid` and `LazyHStack` for efficient scroll viewport performance.
- `.refreshable` pull-to-refresh data lifecycle.
- `.sheet` and `.alert` modal presentations for user confirmations.
- Responsive design adapting dynamically to all iPhone form factors.

---

## 🏗️ Installation & Setup

### Prerequisites
- macOS Sonoma 14.0 or later
- **Xcode 15.0+**
- **iOS 17.0+** Simulator or physical device
- Swift Package Manager (integrated in Xcode)

### Setup Steps
1. **Clone the repository:**
   ```bash
   git clone https://github.com/snaimio/Nourishly.git
   cd Nourishly
   ```

2. **Open the project in Xcode:**
   ```bash
   open Nourishly.xcodeproj
   ```

3. **Firebase Configuration:**
   - Create a project on the [Firebase Console](https://console.firebase.google.com/).
   - Enable **Authentication** (Email/Password) and **Cloud Firestore Database**.
   - Download `GoogleService-Info.plist` and add it to `Nourishly/Resources/`.

4. **Build and Run:**
   - Select your target simulator (e.g. iPhone 15 Pro) and press `⌘ + R`.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 👨‍💻 Author

**Sheikh Naim**  
*Mobile & Full-Stack Web Developer*  
- **LinkedIn**: [linkedin.com/in/snaimio](https://www.linkedin.com/in/snaimio)  
- **GitHub**: [@snaimio](https://github.com/snaimio)  
- **Portfolio**: [snaimio.github.io](https://snaimio.github.io)
