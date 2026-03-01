# ConnectHub (Capstone) — Flutter Mobile App

A professional **Connection Request** mobile app built for a capstone project. Users can create profiles, browse/filter other users, send connection requests, accept/decline requests, and manage connections. (Optional) After connecting, users can store simple message history (not real-time).

## ✅ Capstone Requirements Covered

### Authentication & User Management
- Register / Login / Logout
- Secure session persistence
- Protected routes (authenticated vs unauthenticated users)

### Personalization
- Profile (bio, interests, location)
- Personalized dashboard (“Welcome back, {name}”)
- User-specific records only (requests/connections belong to the user)

### CRUD (Full)
- Create / View / Edit / Delete profile
- Send request
- Accept/decline request
- Remove connection
- (Optional) Create/View messages per connection (stored, not sockets)

### UI/UX Standards
- Consistent theme & spacing
- Loading states / empty states
- Confirmation before delete
- Error handling + feedback

---

# 🧱 Tech Stack
- Flutter
- State Management: Provider / Riverpod / BLoC (choose one)
- REST API: NodeJS/Express backend
- Auth: Firebase Auth **OR** JWT
- Database: MySQL (backend)

> Recommended for capstone clarity:
> - Firebase Auth for login (easy + secure)
> - Backend uses Firebase UID as user_id mapping OR JWT if you prefer

---

# 📱 Features
- Auth flow (Register/Login/Logout)
- Profile setup + edit
- Browse users
- Search/filter by:
  - Location
  - Interests
- Connection requests:
  - Send request
  - Accept/decline
- Connections list
- (Optional) Messages (stored history, not real-time)

---

# ✅ Folder Structure (Recommended)

lib/
├── core/
│   ├── constants/
│   ├── themes/
│   └── utils/
│
├── models/
│   ├── profile.dart
│   ├── connection_request.dart
│   ├── connection.dart
│   └── message.dart (optional)
│
├── services/
│   ├── api_service.dart
│   ├── auth_service.dart
│   └── storage_service.dart (optional)
│
├── providers/ (or bloc/)
│   ├── auth_provider.dart
│   ├── profile_provider.dart
│   ├── browse_provider.dart
│   ├── requests_provider.dart
│   └── connections_provider.dart
│
├── pages/
│   ├── auth/
│   │   ├── login_page.dart
│   │   └── register_page.dart
│   ├── dashboard/
│   │   └── dashboard_page.dart
│   ├── profile/
│   │   ├── edit_profile_page.dart
│   │   └── profile_page.dart
│   ├── browse/
│   │   ├── browse_page.dart
│   │   └── user_details_page.dart
│   ├── requests/
│   │   └── requests_page.dart
│   ├── connections/
│   │   ├── connections_page.dart
│   │   └── chat_page.dart (optional)
│   └── settings/
│       └── settings_page.dart (optional)
│
├── widgets/
│   ├── app_button.dart
│   ├── app_textfield.dart
│   ├── empty_state.dart
│   └── loading_overlay.dart
│
└── main.dart

---

# 🔐 Authentication Flow (Interview-Ready)
1. App launch → check auth state
2. If logged in → Dashboard
3. If not logged in → Login
4. On register → create user → create profile record (backend) → go Dashboard

---

# 🌐 API Base URL Setup

Create a `.env`-style config or constants file.

Example:
- `lib/core/constants/api_constants.dart`

```dart
class ApiConstants {
  static const String baseUrl = "http://localhost:4000/api";
}

