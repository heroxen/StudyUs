# StudyUs
By Heroxen456

**Let's Organize College Life.**

An all-in-one mobile companion for college students that combines academic management (attendance, assignments, classes) with personal life tracking (habits, skills, to-dos) — built for offline-first use with optional cloud backup.

---
## How to Beta Version and use
You can install the beta version build on any device for which this build was provisioned it supports Android & IOS.
Send and open the URL below to install it on a device.
## Downlode Link : https://expo.dev/accounts/hardik456/projects/studyus/builds/6318be2c-58da-4393-b5a2-54d48b961b34

## Overview

StudyUs is a mobile-first student companion designed to solve everyday problems faced during college. Instead of juggling separate tools for timetables, attendance tracking, assignments, and habits, StudyUs brings everything into one organized, cohesive application.

**Who it's for**: College students managing multiple subjects, tracking attendance, meeting assignment deadlines, and building personal habits — all in one place.

---

## Why I Built StudyUs

As I was finishing my first year of college, I realized how fragmented everyday student life could become. My timetable existed separately from my attendance records. Assignment deadlines were easy to lose track of. My personal goals lived somewhere else entirely.

Instead of continuing to manage everything separately, I started building the tool I wished I had from the beginning.

That became StudyUs.

---

## ✨ Features

### 📚 Academic Management

**Subjects**
- Create and manage all your subjects in one place
- Organize by semester and track subject metadata
- Subjects automatically populate dropdowns across all academic features

**Attendance Tracking**
- Mark classes as Present, Absent, or Cancelled
- Auto-calculated attendance percentage per subject
- **"Can I Bunk?" Calculator** — Shows exactly how many classes you can safely miss and how many you must attend to stay above the minimum attendance threshold
- Visual warnings when attendance nears danger zone
- Attendance history view

**Assignments**
- Create assignments with title, subject, description, and deadline
- Track progress with status pipeline: Pending → In Progress → Submitted → Missed → Graded
- Priority levels (High / Medium / Low)
- Grade tracking — log marks received vs. total and see percentage
- Automatic overdue flagging
- Deadline reminders (integration planned)

**Classes & Timetable**
- Add recurring classes once; automatically repeats weekly on selected days
- Include subject, time (hour/minute/AM-PM picker), room, and teacher
- Weekly view grouped by day
- Mark holidays or exam days to suppress class slots

### 🌱 Personal Life Management

**Habits**
- Create habits with frequency (Daily or Weekly)
- **7-day dot grid** showing recent completion history at a glance
- Automatic **streak tracking** (current + longest)
- Mark habits complete directly from the dashboard
- Visual progress and motivation

**Skills**
- Track skill development with a **progress slider** (0–100%)
- Milestone badges unlock at progress thresholds (25%, 50%, 75%, 100%)
- Optional time spent tracking for deliberate practice logging
- Linked resources (YouTube, books, courses) per skill

**To-Do List**
- Quick-add tasks with priority levels
- Sub-tasks / checklists within each task
- Recurring task support (Daily / Weekly / One-Time)
- Mark complete directly in the list
- Separate from academic assignments — for personal daily tasks

### 🏠 Home Dashboard

The most important screen — your daily landing point with **live, interactive widgets**:

- **Greeting header** with your name, today's date, and a daily motivational quote
- **Today & Remaining Classes** — Live counter showing classes happening today and upcoming this week
- **Pending Assignments** — Next few assignments sorted by deadline
- **Attendance Health** — Quick health check per subject: Safe (green) / Warning (amber) / Critical (red)
- **Habits Due Today** — Tap to mark complete directly from the dashboard (no navigation required)
- **Upcoming Deadlines** — Assignments and classes in the next 7 days, merged chronologically
- **Weekly Progress Ring** — Animated circular indicator showing % of this week's goals/habits completed

All widgets are **live and interactive** — no friction to take action on the most common tasks.

### 👤 Profile & Settings

- View and edit your profile
- Manage account settings and theme preferences
- Sign out or delete your account

---

## 🔧 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Mobile Framework** | Expo SDK 54, React Native 0.81.5, Expo Router |
| **Language** | TypeScript 5.9 |
| **State Management** | React Context + AsyncStorage |
| **UI & Animation** | Expo Blur, Expo Linear Gradient, React Native Reanimated |
| **Icons & Fonts** | @expo/vector-icons (SF Symbols + Feather), Nunito + Inter via @expo-google-fonts |
| **Notifications** | expo-notifications (local notifications) |
| **Build System** | pnpm workspaces |
| **Backend (Future)** | Express 5 (cloud backup/restore endpoint prepared) |
| **Database (Future)** | PostgreSQL + Drizzle ORM (configured, not yet used) |

---

## 🏗️ Architecture

**Offline-First Model**

StudyUs prioritizes local availability. All data lives in **AsyncStorage** on your device, enabling the app to work completely offline without any backend dependency.

```
┌─────────────────────────────────────┐
│   Mobile App (Expo + React Native)  │
│   ├── Auth Context                  │
│   ├── App Context (all data)        │
│   ├── Screens & Components          │
│   └── AsyncStorage (persistent)     │
└─────────────────────────────────────┘
              ↓
┌─────────────────────────────────────┐
│  Local Device Storage (AsyncStorage)│
│  (subjects, attendance, assignments,│
│   habits, skills, todos, etc.)      │
└─────────────────────────────────────┘
              ↓
┌─────────────────────────────────────┐
│  Cloud Backup (Optional, Best-Effort)
│  Runs every ~4 seconds after changes│
│  Auto-restored on login             │
└─────────────────────────────────────┘
```

**Key Architectural Decisions**:

- **AsyncStorage-first**: All data stored locally in v1. No mandatory backend calls from mobile.
- **React Context over Redux**: App state is scoped and simple enough for Context; avoids boilerplate.
- **Offline capability**: Full app functionality offline; cloud backup is best-effort sync.
- **Authentication**: Email/password with local persistence. Cloud backup keyed by `sha256(email:passwordHash)`.

---

## 📁 Project Structure

```
StudyUS/
├── artifacts/
│   └── student-os/              # Expo mobile app (main deliverable)
│       ├── app/                 # Screens and navigation
│       │   ├── _layout.tsx      # Root layout, fonts, providers
│       │   ├── splash.tsx       # Splash + auth routing
│       │   ├── onboarding.tsx   # 3-slide onboarding
│       │   ├── auth.tsx         # Login & sign-up
│       │   ├── (tabs)/          # Main 4-tab bottom navigation
│       │   │   ├── index.tsx    # Home dashboard
│       │   │   ├── academic.tsx # Academic tab + inner tabs
│       │   │   ├── personal.tsx # Personal tab + inner tabs
│       │   │   └── profile.tsx  # Profile management
│       ├── components/          # Reusable UI components
│       ├── context/             # Auth & App state (React Context)
│       ├── constants/           # Colors, theme tokens
│       ├── assets/              # Images, icons, fonts
│       └── services/            # API client, storage helpers
├── lib/
│   ├── db/                      # Database schemas (Drizzle ORM)
│   ├── api-client-react/        # API client hooks
│   └── api-zod/                 # Shared validation schemas
├── server/                      # Express API (cloud backup)
├── docs/                        # Documentation
├── package.json                 # Workspace root
├── pnpm-workspace.yaml          # pnpm configuration
├── tsconfig.json                # TypeScript configuration
└── README.md                    # This file
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 24+ (LTS recommended)
- **pnpm** 8+ (`npm install -g pnpm`)
- **Expo CLI** 54+ (installed as a devDependency)
- **Mobile device** or emulator (Android / iOS) for testing

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/studyus.git
   cd studyus
   ```

2. **Install dependencies**

   ```bash
   pnpm install
   ```

3. **Set environment variables**

   Create a `.env` file in the root:

   ```env
   EXPO_PUBLIC_DOMAIN=your-replit-domain.replit.dev
   SESSION_SECRET=your-random-secret-key-here
   ```

   See [Environment Variables](#environment-variables) below.

4. **Start the development server**

   **Mobile app (Expo)**:
   ```bash
   pnpm --filter @workspace/student-os run dev
   ```
   This starts the Expo dev server. Open the Expo app on your phone and scan the QR code, or use an emulator.

   **API server (Express, optional for cloud backup)**:
   ```bash
   pnpm --filter @workspace/api-server run dev
   ```
   Runs on `http://localhost:5000`.

5. **Typecheck**

   ```bash
   pnpm run typecheck
   ```

6. **Build all packages**

   ```bash
   pnpm run build
   ```

---

## 🔐 Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `EXPO_PUBLIC_DOMAIN` | Yes (cloud sync) | The Replit dev/production domain (e.g., `abc.replit.dev`). Used by the mobile app to construct the cloud backup URL. Set automatically in Replit. |
| `SESSION_SECRET` | Yes (API server) | Secret key for Express session encryption. Must be a long random string. Keep it private. |

**For Replit users**: Environment variables are set automatically via Replit secrets. For local development, create a `.env.example` template (see Recommendations below).

---

## 💾 Data & Offline Behavior

### Local Storage
All data is stored locally on your device using **AsyncStorage**:
- Subjects, attendance records, assignments, classes
- Habits, skills, to-dos
- User preferences and settings
- Fully functional offline

### Cloud Backup (Optional)
- Automatic backup runs every ~4 seconds after any data change
- Backup file is keyed by `sha256(email:passwordHash)` — no separate auth token needed
- On login, the latest cloud backup is silently restored to the device
- Best-effort sync — designed to survive network interruptions without data loss

### What Works Offline
- ✅ View all data
- ✅ Create/edit subjects, assignments, classes, habits, skills, todos
- ✅ Mark attendance and update progress
- ✅ Check off habits and tasks
- ✅ All interactive dashboard widgets

### What Requires Internet
- 🔗 Initial login & onboarding (one-time)
- 🔗 Cloud backup sync (automatic but not critical)
- 🔗 Account deletion / logout with backup

---

## 📱 Supported Platforms

- ✅ **iOS** 13+ (via Expo)
- ✅ **Android** 6+ (via Expo)
- ✅ **Web** (via Expo Web, experimental)

---

## 🎨 Design & Theme

StudyUs features a warm, premium design built specifically for college students:

- **Color Palette**: Warm pastels with accessible contrast
- **Fonts**: Nunito (headings — warm, friendly) + Inter (body — legible, modern)
- **Icons**: Feather + SF Symbols (iOS 26+)
- **Animations**: Smooth transitions via React Native Reanimated
- **Dark Mode**: Automatic support based on device settings

Theme tokens are centralized in `constants/colors.ts` for easy customization.

---

## 🔄 Current Status & Roadmap

### ✅ Implemented Features
- [x] Authentication (sign up / login)
- [x] Home dashboard with live widgets
- [x] Subjects management
- [x] Attendance tracking with "Can I Bunk?" calculator
- [x] Assignment tracking with status and grades
- [x] Class timetable (weekly, recurring)
- [x] Habits with streaks and completion grid
- [x] Skills with progress slider and milestones
- [x] To-do list with subtasks
- [x] Offline-first data storage (AsyncStorage)
- [x] Cloud backup (best-effort, automatic)

### 🔄 In Progress
- [ ] Smart notifications (class reminders, assignment deadlines, attendance alerts, habit reminders)
- [ ] Responsive UI refinements (safe area spacing on all screen sizes)
- [ ] To-do repeat type options (Daily / Weekly / One-Time)
- [ ] Time picker UI for class scheduling (improved UX)

### 📋 Planned (Backlog)
- [ ] Exams & exam planner (countdown, study schedule, syllabus tracking)
- [ ] Notes & note-taking (rich text, attachments, subject linking)
- [ ] GPA / CGPA calculator
- [ ] Goals & milestone tracking
- [ ] Journal & mood tracking
- [ ] Finance tracker (expenses, income, budgets)
- [ ] Advanced analytics & insights
- [ ] Semester management (multi-semester archive)
- [ ] Dark mode refinements
- [ ] App Store / Play Store release

---

## 🛠️ Development Tips

**Key Files**:
- `artifacts/student-os/app/_layout.tsx` — Root layout with fonts and providers
- `artifacts/student-os/context/AppContext.tsx` — Central app state (subjects, assignments, habits, etc.)
- `artifacts/student-os/context/AuthContext.tsx` — Auth state and persistence
- `artifacts/student-os/constants/colors.ts` — Theme colors (light + dark modes)
- `artifacts/student-os/components/ProgressRing.tsx` — Circular progress indicator

**Useful Scripts**:
- `pnpm run typecheck` — Run full TypeScript check
- `pnpm run build` — Build all packages
- `pnpm --filter @workspace/api-spec run codegen` — Regenerate API hooks from OpenAPI spec

**Important Notes**:
- Never use bare color strings in `StyleSheet.create()` — use the `useColors()` hook instead (will crash on web)
- Do not use the `uuid` package in Expo — use `generateId()` helper in `storage/storage.ts`
- Expo Go uses HMR (hot module reload) — only restart when changing dependencies

---

## 📄 License

MIT License — see [LICENSE](./LICENSE) file for details.

This project is open-source and welcomes contributions from the student developer community.

---

## 👨‍💻 Creator

**Hardik Sharma**

I built StudyUs to solve the real organizational problems I faced during my first year of college. Instead of managing academics, attendance, assignments, and personal goals across multiple apps, I wanted one organized, intuitive place that students would actually want to use every day.

If you find this helpful or have ideas for improvements, feel free to open an issue or contribute!

---

## 🤝 Contributing

This project is under active development and welcomes contributions. If you'd like to help:

1. **Report Issues** — Found a bug? Open an issue with details
2. **Suggest Features** — Have an idea? Discuss it in an issue first
3. **Submit PRs** — Make improvements and submit a pull request

For larger changes, please open an issue first to discuss the approach.

---

## 📖 Documentation

- **[ARCHITECTURE.md](./docs/ARCHITECTURE.md)** — Detailed architecture and design decisions *(coming soon)*
- **[CONTRIBUTING.md](./CONTRIBUTING.md)** — Contribution guidelines *(coming soon)*
- **[Internal Dev Docs](./replit.md)** — Developer setup and patterns (Replit specific)

---

## 🔒 Security

StudyUs takes security seriously:

- ✅ All authentication is handled locally with secure hashing
- ✅ No API keys or credentials are hardcoded
- ✅ Environment variables are kept separate from source code
- ✅ Supply-chain security: pnpm workspace enforces minimum package release age (1 day) to mitigate npm attacks
- ✅ TypeScript strict mode enabled for type safety

For security concerns, please email [your-email] or open a private security report.

---

## 📞 Support & Feedback

- **Issues & Bugs**: [Open an issue](https://github.com/your-username/studyus/issues)
- **Feature Requests**: [Discussions](https://github.com/your-username/studyus/discussions)
- **Email**: [your-email]

---

**Built with ❤️ for college students. Let's organize college life.**
