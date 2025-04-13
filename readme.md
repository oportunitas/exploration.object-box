# 📦 Event Manager ObjectBox App

## ✍️ Author Information

| **Author**          | Taib Izzat Samawi              |
|----------------------|---------------------------------|
| **NRP**             | 5025221085 (085 mod 4 = 1)     |

🎉 This project demonstrates how to build a Flutter app with **ObjectBox**

---

## 🛠️ Getting Started
### 1️⃣ Prerequisites

Ensure you have the following installed:

- **Flutter SDK**: [Install Flutter](https://flutter.dev/docs/get-started/install)
- **Dart SDK**: Comes with Flutter
- **ObjectBox CLI**: Install via `dart pub global activate objectbox_generator`
- **Platform-specific tools**:
  - Android Studio (for Android)
  - Xcode (for iOS/macOS)
  - Visual Studio (for Windows)
  - GTK development libraries (for Linux)

---

### 2️⃣ Clone the Repository

```bash
git clone https://github.com/your-repo/event_manager_objectbox.git
cd event_manager_objectbox
```

---

### 3️⃣ Install Dependencies

Run the following command to fetch all dependencies:

```bash
flutter pub get
```

---

### 4️⃣ Generate ObjectBox Code

ObjectBox uses code generation to create database bindings. Run:

```bash
flutter pub run build_runner build
```

This will generate the `objectbox.g.dart` file based on your `model.dart` file.

---

### 5️⃣ Run the App

To run the app on your desired platform:

- **Android/iOS**: Use `flutter run` with a connected device or emulator.
- **Linux/macOS/Windows**: Use `flutter run` on your desktop.

---

## 🌟 Key Features of ObjectBox

ObjectBox is a super-fast database designed for mobile and IoT applications. Here's why it's awesome:

- **High Performance**: Faster than SQLite and other alternatives.
- **Relations**: Supports one-to-one, one-to-many, and many-to-many relationships.
- **Cross-Platform**: Works seamlessly on Android, iOS, Linux, macOS, and Windows.
- **Reactive Streams**: Automatically update your UI when data changes.

---

## 🏗️ Developing ObjectBox Apps

Here’s how you can develop apps with ObjectBox:

### 1️⃣ Define Your Data Model

Create a Dart class for each entity you want to store in the database. For example:

```dart
// filepath: lib/model.dart
import 'package:objectbox/objectbox.dart';

@Entity()
class Event {
  int id = 0; // ObjectBox requires an ID field
  String name;
  DateTime date;

  Event({required this.name, required this.date});
}
```

### 2️⃣ Generate the ObjectBox Code

Run the following command to generate the necessary bindings:

```bash
flutter pub run build_runner build
```

### 3️⃣ Open the Database

Use the generated `objectbox.g.dart` file to open the database:

```dart
// filepath: lib/main.dart
import 'objectbox.g.dart';

late final Store store;

void main() async {
  store = await openStore();
  runApp(MyApp());
}
```

### 4️⃣ Perform CRUD Operations

Use the `Box` API to create, read, update, and delete objects:

```dart
final box = store.box<Event>();

// Create
final event = Event(name: "Flutter Meetup", date: DateTime.now());
box.put(event);

// Read
final events = box.getAll();

// Update
event.name = "Updated Meetup";
box.put(event);

// Delete
box.remove(event.id);
```

---

## 📂 Project Structure

Here’s an overview of the project structure:

```
event_manager/
├── lib/
│   ├── main.dart                # App entry point
│   ├── model.dart               # ObjectBox data models
│   ├── objectbox-model.json     # ObjectBox schema
│   └── objectbox.g.dart         # Generated ObjectBox code
├── android/                     # Android-specific code
├── ios/                         # iOS-specific code
├── linux/                       # Linux-specific code
├── macos/                       # macOS-specific code
├── windows/                     # Windows-specific code
├── pubspec.yaml                 # Flutter dependencies
└── README.md                    # Project documentation
```

---

## 🐛 Troubleshooting

### Common Issues

1. **Code Generation Fails**: Ensure `build_runner` and `objectbox_generator` are added to `dev_dependencies` in `pubspec.yaml`.
2. **Database Not Opening**: Check if `objectbox.g.dart` is generated and imported correctly.

---