# Ajheryuk — Live Education Course App UI

> A modern, beautifully crafted Flutter UI for a live online education platform — featuring animated course cards, a structured navigation system, real-time messaging, and a seamless enrollment scheduling flow.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [App Flow](#app-flow)
- [Project Structure](#project-structure)
- [Tech Stack & Dependencies](#tech-stack--dependencies)
- [Getting Started](#getting-started)
- [Running the App](#running-the-app)
- [Assets](#assets)
- [License](#license)

---

## Overview

**Ajheryuk** is a Flutter-based mobile UI project that demonstrates a full user interface for a live online education and course-discovery application. The project covers the complete user journey — from the splash/get-started screen and authentication (login & sign up), through to a feature-rich home dashboard, course browsing with an animated horizontal carousel, detailed course pages with instructor profiles and lesson lists, an interactive time-slot scheduling bottom sheet, a real-time-style messages inbox, and a profile section — all tied together with a smooth, animated bottom navigation bar.

This project is a **UI prototype / frontend skeleton** built for design implementation practice and portfolio demonstration. State management is handled using **Flutter Riverpod**, and the typography is powered by **Google Fonts (Poppins)**.

---

## Features

| Feature | Description |
|---|---|
| 🚀 **Get Started Screen** | Branded splash/landing screen with app logo and a call-to-action button |
| 🔐 **Login Screen** | Email & password login form with show/hide password toggle, social login buttons (Facebook & Google), and navigation to Sign Up |
| 📝 **Sign Up Screen** | Full name, email, and password registration with social sign-up options and Terms & Privacy links |
| 🏠 **Dashboard** | User profile navbar, weekly live stream banner, category filter chips, and an animated horizontal course card carousel |
| 🃏 **Animated Course Cards** | Horizontal scroll carousel with dynamic blur, scale, and opacity effects as cards move off-center |
| 📖 **Course Detail Page** | Full-screen course detail with a video preview card, course tags, description, instructor profile, lesson list, and a floating "Follow Class" button |
| 📅 **Time Slot Scheduling** | Draggable bottom sheet with a grid of available/unavailable time slots, interactive selection via Riverpod state, and a date + time confirmation row |
| 💬 **Messages Screen** | Inbox-style message list with avatar, sender name, last message preview, timestamp, and unread count badge; includes a search bar |
| 🔍 **Discovery Screen** | Placeholder screen for content exploration (extensible) |
| 👤 **Profile Screen** | Placeholder screen for user profile (extensible) |
| 🧭 **Bottom Navigation Bar** | Custom animated bottom nav with fill/outline SVG icon switching and an unread message count badge |
| 🎨 **Design System** | Consistent use of brand color `#EC5F5F` (coral red), `#0082CD` (blue), Poppins font, and rounded UI components |

---

## App Flow

```
App Launch
    │
    ▼
┌─────────────────┐
│   Get Started   │  ← Logo + "Get Started" button
└────────┬────────┘
         │ Navigate to Login
         ▼
┌─────────────────┐
│     Login       │  ← Email, Password, Social Login (Facebook / Google)
│                 │  ← "Forgot password?" link
│                 │  ← "Sign Up" link (navigates with slide animation)
└────────┬────────┘
         │ On "Log in" tapped → Navigate to main app
         ▼
┌──────────────────────────────────────────────┐
│              ViewerScreens (PageView)         │
│                                              │
│  ┌──────────┐  ┌───────────┐  ┌───────────┐  ┌─────────┐ │
│  │Dashboard │  │ Discovery │  │ Messages  │  │ Profile │ │
│  └──────────┘  └───────────┘  └───────────┘  └─────────┘ │
│                                                            │
│       ↑ Controlled by CustomBottomNavigationBar            │
└───────────────────┬──────────────────────────┘
                    │ Tap a course card
                    ▼
         ┌────────────────────────┐
         │   DetailCardCarousel   │
         │  - Video preview card  │
         │  - Course title & tags │
         │  - Instructor profile  │
         │  - Lesson list         │
         │  - "Follow Class" CTA  │
         └────────────┬───────────┘
                      │ Tap "Follow Class"
                      ▼
         ┌────────────────────────────┐
         │  Time Slot Bottom Sheet    │
         │  - Available time grid     │
         │  - Select slot (animated)  │
         │  - Date & time checkbox    │
         │  - "Join & Save" button    │
         └────────────────────────────┘
```

---

## Project Structure

```
ajheryuk-app-ui/
├── lib/
│   ├── main.dart                        # App entry point, ProviderScope setup
│   ├── models/
│   │   ├── carousels.dart               # CardData model + dummy course data list
│   │   └── messages.dart                # Message model + dummy messages data
│   ├── providers/
│   │   ├── general_provider.dart        # selectedIndex, pageController, obscurePassword, checkbox providers
│   │   └── time_slot_provider.dart      # Time slot selection state provider
│   ├── screens/
│   │   ├── get_started.dart             # Landing / splash screen
│   │   ├── viewer_screens.dart          # Main PageView host + CustomBottomNavigationBar
│   │   ├── dashboard.dart               # Home dashboard (navbar, stream, category, cards)
│   │   ├── discovery.dart               # Discovery screen placeholder
│   │   ├── messages.dart                # Messages inbox screen
│   │   ├── profile.dart                 # Profile screen placeholder
│   │   ├── detail_card_carousel.dart    # Course detail + time slot booking bottom sheet
│   │   └── auth/
│   │       ├── login.dart               # Login screen
│   │       └── signup.dart              # Sign up screen
│   └── widgets/
│       ├── widget_bottom_navigation.dart  # Animated custom bottom navigation bar
│       ├── widget_card_course.dart        # Horizontal animated course card carousel
│       ├── widget_category.dart           # Category filter chip bar
│       ├── widget_navbar_profile.dart     # Dashboard top navbar with profile avatar
│       └── widget_user_stream.dart        # Upcoming live stream banner widget
├── assets/
│   ├── images/                          # App logo, background images, course thumbnails
│   │   └── media/                       # Social media icons (Facebook, Google)
│   ├── person/                          # Instructor and user avatar images
│   └── bottomnavigation/               # Bottom nav icons (fill & outline variants)
├── pubspec.yaml                         # Flutter dependencies & asset declarations
└── analysis_options.yaml                # Dart lint configuration
```

---

## Tech Stack & Dependencies

| Package | Version | Purpose |
|---|---|---|
| `flutter` | SDK | Core framework |
| `flutter_riverpod` | ^2.6.1 | Reactive state management |
| `google_fonts` | ^6.2.1 | Poppins typography |
| `flutter_svg` | ^2.1.0 | SVG asset rendering |
| `font_awesome_flutter` | ^10.8.0 | Icon library |
| `cupertino_icons` | ^1.0.8 | iOS-style icons |

**Dart SDK:** `^3.8.0`

---

## Getting Started

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install) installed (version compatible with Dart `^3.8.0`)
- A connected device or emulator (Android / iOS / Desktop)
- `flutter doctor` returns no critical errors

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/agungkurniawanid/ajheryuk-app-ui.git
   cd ajheryuk-app-ui
   ```

2. **Install dependencies**
   ```bash
   flutter pub get
   ```

3. **Verify assets are configured**
   Ensure the following asset directories exist as declared in `pubspec.yaml`:
   ```
   assets/images/
   assets/images/media/
   assets/person/
   assets/bottomnavigation/
   ```

---

## Running the App

```bash
# Run in debug mode on connected device
flutter run

# Run on a specific device
flutter run -d <device-id>

# List available devices
flutter devices

# Build APK (Android)
flutter build apk --release

# Build for iOS
flutter build ios --release
```

---

## Assets

The project uses local asset images grouped into three directories:

| Directory | Contents |
|---|---|
| `assets/images/` | App logo (`Logo.png`, `Logo Mark.png`), course card background images (`Base Background.png`, `bg (2).png` – `bg (9).png`) |
| `assets/images/media/` | Social login icons (`facebook.png`, `google.png`) |
| `assets/person/` | Instructor/user profile avatars (`person (11).jpg` – `person (19).jpg`) |
| `assets/bottomnavigation/` | Navigation icons in both fill and outline variants (e.g. `menu-fill.png`, `menu-outline.png`) |

---

## License

This project is open source and available for personal use, learning, and portfolio purposes.

---

---

# Ajheryuk — Aplikasi UI Kursus Pendidikan Live

> Tampilan antarmuka Flutter yang modern dan elegan untuk platform pendidikan online berbasis live — dilengkapi kartu kursus beranimasi, sistem navigasi terstruktur, pesan real-time, dan alur penjadwalan pendaftaran yang mulus.

---

## 📌 Daftar Isi

- [Gambaran Umum](#gambaran-umum)
- [Fitur](#fitur)
- [Alur Aplikasi](#alur-aplikasi)
- [Struktur Proyek](#struktur-proyek)
- [Tech Stack & Dependensi](#tech-stack--dependensi)
- [Memulai](#memulai)
- [Menjalankan Aplikasi](#menjalankan-aplikasi)
- [Aset](#aset)

---

## Gambaran Umum

**Ajheryuk** adalah proyek UI mobile berbasis Flutter yang menampilkan antarmuka lengkap untuk aplikasi pendidikan online dan penemuan kursus secara live. Proyek ini mencakup perjalanan pengguna secara menyeluruh — mulai dari layar splash/get-started dan autentikasi (login & daftar), hingga dashboard utama yang kaya fitur, penelusuran kursus dengan carousel horizontal beranimasi, halaman detail kursus lengkap dengan profil instruktur dan daftar pelajaran, bottom sheet interaktif untuk pemilihan jadwal waktu, kotak masuk pesan bergaya real-time, dan bagian profil — semuanya disatukan dengan bottom navigation bar yang animasinya halus.

Proyek ini merupakan **prototipe UI / kerangka frontend** yang dibangun untuk praktik implementasi desain dan demonstrasi portofolio. Manajemen state ditangani menggunakan **Flutter Riverpod**, dan tipografi menggunakan **Google Fonts (Poppins)**.

---

## Fitur

| Fitur | Keterangan |
|---|---|
| 🚀 **Layar Get Started** | Layar splash/landing bermerek dengan logo aplikasi dan tombol ajakan bertindak |
| 🔐 **Layar Login** | Formulir login email & password dengan toggle tampil/sembunyikan password, tombol login sosial (Facebook & Google), dan navigasi ke Daftar |
| 📝 **Layar Daftar (Sign Up)** | Pendaftaran dengan nama lengkap, email, dan password beserta opsi daftar via sosial media, dan tautan Syarat & Privasi |
| 🏠 **Dashboard** | Navbar profil pengguna, banner live stream mingguan, chip filter kategori, dan carousel kartu kursus horizontal beranimasi |
| 🃏 **Kartu Kursus Beranimasi** | Carousel scroll horizontal dengan efek blur, skala, dan opasitas dinamis saat kartu bergerak dari tengah layar |
| 📖 **Halaman Detail Kursus** | Detail kursus layar penuh dengan pratinjau video, tag kursus, deskripsi, profil instruktur, daftar pelajaran, dan tombol "Follow Class" mengambang |
| 📅 **Penjadwalan Slot Waktu** | Bottom sheet yang bisa diseret dengan grid slot waktu tersedia/tidak tersedia, pemilihan interaktif via state Riverpod, dan baris konfirmasi tanggal & waktu |
| 💬 **Layar Pesan** | Daftar pesan bergaya kotak masuk dengan avatar, nama pengirim, pratinjau pesan terakhir, timestamp, dan lencana jumlah belum dibaca; disertai search bar |
| 🔍 **Layar Discovery** | Layar placeholder untuk eksplorasi konten (dapat dikembangkan) |
| 👤 **Layar Profil** | Layar placeholder untuk profil pengguna (dapat dikembangkan) |
| 🧭 **Bottom Navigation Bar** | Navigasi bawah kustom beranimasi dengan pergantian ikon fill/outline dan lencana jumlah pesan belum dibaca |
| 🎨 **Sistem Desain** | Penggunaan konsisten warna merek `#EC5F5F` (coral red), `#0082CD` (biru), font Poppins, dan komponen UI dengan sudut membulat |

---

## Alur Aplikasi

```
Aplikasi Dibuka
    │
    ▼
┌─────────────────┐
│   Get Started   │  ← Logo + tombol "Get Started"
└────────┬────────┘
         │ Navigasi ke Login
         ▼
┌─────────────────┐
│     Login       │  ← Email, Password, Login Sosial (Facebook / Google)
│                 │  ← Tautan "Forgot password?"
│                 │  ← Tautan "Sign Up" (navigasi dengan animasi slide)
└────────┬────────┘
         │ Tombol "Log in" ditekan → Navigasi ke aplikasi utama
         ▼
┌──────────────────────────────────────────────┐
│         ViewerScreens (PageView)              │
│                                              │
│  ┌──────────┐  ┌───────────┐  ┌───────────┐  ┌─────────┐ │
│  │Dashboard │  │ Discovery │  │  Pesan    │  │ Profil  │ │
│  └──────────┘  └───────────┘  └───────────┘  └─────────┘ │
│                                                            │
│     ↑ Dikontrol oleh CustomBottomNavigationBar             │
└───────────────────┬──────────────────────────┘
                    │ Tekan kartu kursus
                    ▼
         ┌────────────────────────┐
         │   DetailCardCarousel   │
         │  - Pratinjau video     │
         │  - Judul & tag kursus  │
         │  - Profil instruktur   │
         │  - Daftar pelajaran    │
         │  - CTA "Follow Class"  │
         └────────────┬───────────┘
                      │ Tekan "Follow Class"
                      ▼
         ┌────────────────────────────┐
         │  Bottom Sheet Jadwal       │
         │  - Grid slot waktu         │
         │  - Pilih slot (animasi)    │
         │  - Checkbox tanggal & jam  │
         │  - Tombol "Join & Save"    │
         └────────────────────────────┘
```

---

## Struktur Proyek

```
ajheryuk-app-ui/
├── lib/
│   ├── main.dart                        # Entry point aplikasi, setup ProviderScope
│   ├── models/
│   │   ├── carousels.dart               # Model CardData + data dummy daftar kursus
│   │   └── messages.dart                # Model Message + data dummy pesan
│   ├── providers/
│   │   ├── general_provider.dart        # Provider: selectedIndex, pageController, obscurePassword, checkbox
│   │   └── time_slot_provider.dart      # Provider state pemilihan slot waktu
│   ├── screens/
│   │   ├── get_started.dart             # Layar landing / splash
│   │   ├── viewer_screens.dart          # Host PageView utama + CustomBottomNavigationBar
│   │   ├── dashboard.dart               # Dashboard utama (navbar, stream, kategori, kartu)
│   │   ├── discovery.dart               # Placeholder layar discovery
│   │   ├── messages.dart                # Layar kotak masuk pesan
│   │   ├── profile.dart                 # Placeholder layar profil
│   │   ├── detail_card_carousel.dart    # Detail kursus + bottom sheet pemesanan jadwal
│   │   └── auth/
│   │       ├── login.dart               # Layar login
│   │       └── signup.dart              # Layar daftar
│   └── widgets/
│       ├── widget_bottom_navigation.dart  # Bottom navigation bar kustom beranimasi
│       ├── widget_card_course.dart        # Carousel kartu kursus horizontal beranimasi
│       ├── widget_category.dart           # Bar chip filter kategori
│       ├── widget_navbar_profile.dart     # Navbar atas dashboard dengan avatar profil
│       └── widget_user_stream.dart        # Widget banner live stream mendatang
├── assets/
│   ├── images/                          # Logo aplikasi, gambar latar, thumbnail kursus
│   │   └── media/                       # Ikon media sosial (Facebook, Google)
│   ├── person/                          # Foto avatar instruktur dan pengguna
│   └── bottomnavigation/               # Ikon navigasi bawah dalam varian fill dan outline
├── pubspec.yaml                         # Dependensi Flutter & deklarasi aset
└── analysis_options.yaml                # Konfigurasi lint Dart
```

---

## Tech Stack & Dependensi

| Package | Versi | Kegunaan |
|---|---|---|
| `flutter` | SDK | Framework utama |
| `flutter_riverpod` | ^2.6.1 | Manajemen state reaktif |
| `google_fonts` | ^6.2.1 | Tipografi Poppins |
| `flutter_svg` | ^2.1.0 | Rendering aset SVG |
| `font_awesome_flutter` | ^10.8.0 | Pustaka ikon |
| `cupertino_icons` | ^1.0.8 | Ikon bergaya iOS |

**Dart SDK:** `^3.8.0`

---

## Memulai

### Prasyarat

- [Flutter SDK](https://docs.flutter.dev/get-started/install) terpasang (versi kompatibel dengan Dart `^3.8.0`)
- Perangkat terhubung atau emulator (Android / iOS / Desktop)
- `flutter doctor` tidak menampilkan error kritis

### Instalasi

1. **Clone repositori**
   ```bash
   git clone https://github.com/agungkurniawanid/ajheryuk-app-ui.git
   cd ajheryuk-app-ui
   ```

2. **Install dependensi**
   ```bash
   flutter pub get
   ```

3. **Pastikan aset sudah dikonfigurasi**
   Pastikan direktori aset berikut ada sesuai deklarasi di `pubspec.yaml`:
   ```
   assets/images/
   assets/images/media/
   assets/person/
   assets/bottomnavigation/
   ```

---

## Menjalankan Aplikasi

```bash
# Jalankan dalam mode debug di perangkat yang terhubung
flutter run

# Jalankan di perangkat tertentu
flutter run -d <device-id>

# Daftar perangkat yang tersedia
flutter devices

# Build APK (Android)
flutter build apk --release

# Build untuk iOS
flutter build ios --release
```

---

## Aset

Proyek menggunakan gambar aset lokal yang dikelompokkan dalam tiga direktori:

| Direktori | Isi |
|---|---|
| `assets/images/` | Logo aplikasi (`Logo.png`, `Logo Mark.png`), gambar latar kartu kursus (`Base Background.png`, `bg (2).png` – `bg (9).png`) |
| `assets/images/media/` | Ikon login sosial (`facebook.png`, `google.png`) |
| `assets/person/` | Avatar profil instruktur/pengguna (`person (11).jpg` – `person (19).jpg`) |
| `assets/bottomnavigation/` | Ikon navigasi dalam varian fill dan outline (mis. `menu-fill.png`, `menu-outline.png`) |
