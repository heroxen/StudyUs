# StudyUs Screenshot Guide

This guide helps you capture the right screenshots to showcase StudyUs features in the GitHub README.

---

## 📱 Where to Store Screenshots

```
docs/
└── assets/
    ├── studyus-showcase.png        # Hero banner (app on multiple phones)
    └── screenshots/
        ├── dashboard.png            # Home screen
        ├── attendance.png           # Attendance tracker
        ├── assignments.png          # Assignments list
        ├── classes.png              # Class timetable
        ├── habits.png               # Habits tracker
        └── skills.png               # Skills tracker
```

---

## 📸 Screenshot Specifications

**Device**: iPhone 12 or Android equivalent (375px width, 812px height is ideal)  
**Format**: PNG with transparent background preferred, or white/system background  
**Size**: Aim for ~100KB per screenshot (compress if larger)  
**Display**: Landscape view is fine but portrait is better for mobile app  
**Content**: Real, populated data — not empty states  

---

## 🎯 Key Screenshots to Capture

### 1. **Dashboard** (`dashboard.jpg`)

**What it shows**: Home screen — the most important screen

**Content to display**:
- [ ] Greeting with name and date
- [ ] "Today & Remaining Classes" live counter
- [ ] Pending assignments (at least 2-3)
- [ ] Attendance health per subject (show mix of green/amber/red statuses)
- [ ] Habits due today section (at least 2-3 habits)
- [ ] Upcoming deadlines list

**Purpose**: Demonstrates the all-in-one view; shows how students see their daily overview

**Pro tip**: Scroll the dashboard to show multiple widgets — capture the full flow

---

### 2. **Attendance** (`attendance.jpg`)

**What it shows**: Attendance tracking and "Can I Bunk?" calculator

**Content to display**:
- [ ] Subject list with attendance percentages
- [ ] Status indicators (safe, warning, critical)
- [ ] "Can I Bunk?" calculator for at least one subject showing:
  - Current attendance percentage
  - Minimum required threshold
  - Classes attended / total
  - Classes that can be safely missed
- [ ] Past attendance records or date picker

**Purpose**: Shows the core academic tracking feature; emphasize the "Can I Bunk?" logic (unique feature)

**Pro tip**: Show a subject near the warning threshold to highlight the feature

---

### 3. **Assignments** (`assignments.jpg`)

**What it shows**: Assignment tracking with status and deadlines

**Content to display**:
- [ ] Multiple assignments with titles
- [ ] Status pills (Pending, In Progress, Submitted, etc.) — show variety
- [ ] Due dates (include overdue ones if possible)
- [ ] Priority levels (High/Medium/Low) — visual differentiation
- [ ] Subject association
- [ ] Grade tracking (show at least one "Graded" assignment with marks)

**Purpose**: Demonstrates deadline management and status tracking

**Pro tip**: Include an overdue assignment (red highlight) to show visual warnings

---

### 4. **Classes / Timetable** (`classes.jpg`)

**What it shows**: Weekly class schedule

**Content to display**:
- [ ] Weekly view (Mon-Sun)
- [ ] Multiple classes on different days
- [ ] Time slots (start/end times)
- [ ] Subject names
- [ ] Room numbers and teacher names
- [ ] Show recurring nature (same class on multiple days)

**Purpose**: Demonstrates timetable management and organization

**Pro tip**: Make sure times are realistic (e.g., 09:00-10:00, 10:15-11:15)

---

### 5. **Habits** (`habits.jpg`)

**What it shows**: Habit tracking with streaks and completion history

**Content to display**:
- [ ] Multiple habits (at least 3-4)
- [ ] 7-day dot grid on each habit showing recent completion
- [ ] Streak counter (current + longest)
- [ ] Habit icons/categories
- [ ] Mix of completed and incomplete days in the grid
- [ ] Optional: Habit categories (Health, Study, Social)

**Purpose**: Demonstrates personal life tracking; shows streaks and visual feedback

**Pro tip**: Show habits with high streaks (e.g., 15+ days) to motivate

---

### 6. **Skills** (`skills.jpg`)

**What it shows**: Skill progress tracking

**Content to display**:
- [ ] Multiple skills (at least 3-4)
- [ ] Progress sliders showing varying levels (e.g., 25%, 60%, 85%)
- [ ] Milestone badges (25%, 50%, 75%, 100%)
- [ ] Skill names and icons
- [ ] Optional: Time spent tracking
- [ ] Optional: Resource links

**Purpose**: Demonstrates skill development tracking; shows progress visualization

**Pro tip**: Show at least one skill at 100% to highlight milestone achievements

---

### 7. **Hero Banner** (`studyus-showcase.jpg`) — OPTIONAL

**What it shows**: App on multiple device frames

**Content to display**:
- [ ] iPhone/Android side-by-side
- [ ] Show dashboard on one phone, attendance on another
- [ ] Product tagline: "Let's Organize College Life"
- [ ] Clean, professional layout

**Purpose**: Eye-catching banner for GitHub README hero section

**Tools to create**:
- **App mockups**: Figma, Sketch, or use free tools like:
  - [CleanMock](https://cleanmock.com/) — drag & drop screenshots into device frames
  - [Smartmockups](https://smartmockups.com/) — free device mockups
  - [AppMockUp](https://www.appmockup.com/) — professional mockups

---

## 🎨 Screenshot Best Practices

### Do's ✅
- ✅ Use realistic data (real subject names, assignment titles, etc.)
- ✅ Show the theme in action (colors, fonts, spacing)
- ✅ Include visual feedback (highlights, badges, progress rings)
- ✅ Show variety (mix of full, warning, and critical states)
- ✅ Capture both dark and light mode if supported
- ✅ Use consistent device frame (all iPhone, or all Android)
- ✅ Optimize file size before uploading

### Don'ts ❌
- ❌ Empty/placeholder data ("New Subject", "New Assignment")
- ❌ Partial screens (cut off at edges)
- ❌ Tiny text (hard to read)
- ❌ Very large files (>500KB per screenshot)
- ❌ Watermarks or app store badges unless relevant
- ❌ Personal info (real student names, emails, etc.)
- ❌ Inconsistent device sizes or orientations

---

## 📸 Capture Steps

### Using Expo Dev Server

1. **Start the app**:
   ```bash
   pnpm --filter @workspace/student-os run dev
   ```

2. **Open in emulator or Expo Go on real device**

3. **Navigate to each screen** and populate with sample data:
   - Create 3-4 subjects
   - Add several classes to timetable
   - Create 5-6 assignments with varying dates
   - Add 4-5 habits with some completed
   - Add 4-5 skills with different progress levels
   - Mark some attendance records

4. **Take screenshots**:
   - **Android Emulator**: Ctrl+S or through toolbar
   - **iOS Simulator**: Cmd+S
   - **Expo Go App**: Device screenshot (Power + Volume Up on iOS, Power + Volume Down on Android)

5. **Save to `docs/assets/screenshots/` folder** with names from list above

6. **Optimize image**:
   ```bash
   # Using ImageMagick
   convert input.png -quality 85 -resize 800x output.png
   
   # Or use online tools:
   # TinyPNG.com, Compressor.io, etc.
   ```

---

## 🎬 Optional: Create a Demo Video

For extra impact, create a short 30–60 second demo video showing:

1. Home dashboard overview
2. Creating an assignment and viewing deadline
3. Marking attendance with "Can I Bunk?" calculation
4. Checking off a habit
5. Adjusting skill progress

**Host on YouTube** and embed in README.md with link:
```markdown
[![Watch Demo](https://img.youtube.com/vi/VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=VIDEO_ID)
```

---

## 📋 Checklist for Uploading

- [ ] Created `docs/assets/` folder
- [ ] Created `docs/assets/screenshots/` subfolder
- [ ] Captured 6 main screenshots (dashboard, attendance, assignments, classes, habits, skills)
- [ ] Optional: Created hero banner
- [ ] Optimized all images (aim for <150KB each)
- [ ] Named files correctly (no spaces, all lowercase)
- [ ] Updated README.md to reference correct paths
- [ ] Verified all images render on GitHub

---

## 📞 Troubleshooting Screenshots

**Screenshot came out blurry?**
- Try taking screenshot again at higher quality
- Check device resolution/pixel density settings

**Text is too small?**
- Zoom in before taking screenshot (pinch zoom on device)
- Or adjust device font size in simulator settings

**Colors look wrong?**
- Ensure device theme matches (light/dark mode)
- Screenshot in same theme as your README preview

**File too large?**
- Compress using ImageMagick, TinyPNG, or similar
- Aim for 80–150KB per screenshot

**Hard to see details?**
- Take a second close-up screenshot of just that section
- Or add an inline note in README explaining what to look for

---

## 🎯 Final Tips

1. **Tell a story**: Arrange screenshots to show user journey (Sign Up → Dashboard → Features)
2. **Less is more**: 6–8 good screenshots beat 15 mediocre ones
3. **Be authentic**: Show real data, real usage, not fake perfection
4. **Update regularly**: As features improve, refresh the screenshots
5. **Highlight unique features**: Make sure "Can I Bunk?" and "Habits Streak" are visible

---

**Ready to capture? Start with the Dashboard and Attendance — those are your two showcase screens!** 📸

