# Contributing to StudyUs

Thank you for your interest in contributing to StudyUs! This document outlines the process and guidelines for contributing.

## Getting Started

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/your-username/studyus.git
   cd studyus
   ```
3. **Add upstream** to sync with main repository:
   ```bash
   git remote add upstream https://github.com/original-repo/studyus.git
   ```
4. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

1. **Install dependencies**:
   ```bash
   pnpm install
   ```

2. **Start the development server**:
   ```bash
   # Mobile app
   pnpm --filter @workspace/student-os run dev
   
   # API server (if needed)
   pnpm --filter @workspace/api-server run dev
   ```

3. **Run typechecking**:
   ```bash
   pnpm run typecheck
   ```

## Guidelines

### Code Style

- **TypeScript** is required — ensure strict mode compliance
- **Use `prettier`** for formatting (runs automatically on commit)
- **Follow the existing file structure** in the app
- **Keep components small and focused** — prefer composition over large monolithic components
- **Use React Context** for state, not Redux or other libraries
- **No bare color strings** in `StyleSheet.create()` — use the `useColors()` hook

### Commits

- Use **clear, descriptive commit messages**:
  ```
  feat: add time picker UI for class scheduling
  fix: resolve attendance calculation bug
  docs: update README with new features
  ```
- Reference issues when applicable:
  ```
  fix: correct to-do live update on dashboard (#123)
  ```

### Pull Requests

1. **Before submitting**, ensure:
   - Code typechecks: `pnpm run typecheck`
   - No console errors in Expo dev server
   - You've tested on both Android/iOS or in Expo Go
   - Commit messages are clear and descriptive

2. **Provide a detailed PR description**:
   - What problem does this solve?
   - How does it work?
   - Are there any breaking changes?
   - Screenshots for UI changes

3. **Expect feedback** — be responsive and open to suggestions

### Testing

- While comprehensive tests are not yet in place, ensure:
  - Your changes don't break existing features
  - You've tested your feature end-to-end
  - Edge cases are considered (empty states, errors, etc.)

### Documentation

- Update the **README.md** if you add user-facing features
- Add inline **code comments** for complex logic
- Keep the feature status in the Roadmap section current

## What We're Looking For

### High Priority Contributions

- ✅ **Smart Notification System** — Comprehensive notifications for classes, assignments, attendance alerts, habits, skills, and todos
- ✅ **UI/UX Refinements** — Safe area spacing, responsive design fixes, visual polish
- ✅ **To-Do Improvements** — Repeat types (Daily/Weekly/One-Time), better time picker
- ✅ **Bug Fixes** — Report and fix issues you find

### Medium Priority

- 🔄 **Exam Planner** — Countdown timers, syllabus tracking, study schedule
- 🔄 **Notes & Note-Taking** — Rich text, attachments, organization
- 🔄 **GPA Calculator** — Subject credits + grade aggregation

### Lower Priority (Backlog)

- 📋 Goals & milestones
- 📔 Journal with mood tracking
- 💰 Finance tracker
- 📊 Advanced analytics

### Not Accepting (For Now)

- 🚫 Complete redesigns without discussion — open an issue first
- 🚫 Adding new dependencies — discuss in an issue before implementing
- 🚫 Changing the authentication flow or database schema without approval

## Reporting Issues

Found a bug? Have a feature idea? Please **open an issue** with:

- **Title**: Clear, concise description of the problem
- **Description**: What's happening, what should happen
- **Steps to Reproduce** (for bugs): Clear steps to trigger the issue
- **Screenshots**: Visual evidence of the issue
- **Environment**: Device, OS version, app version

### Labels

- `bug` — Something isn't working
- `enhancement` — New feature or improvement
- `documentation` — Documentation updates
- `good first issue` — Good for newcomers
- `help wanted` — Needs community assistance

## Code of Conduct

- Be respectful and inclusive
- No harassment, discrimination, or hostile language
- Provide constructive feedback
- Assume good intent

## Questions?

- Check existing **issues and discussions** — your question may already be answered
- Open a new **discussion** for questions or ideas
- Comment on related **PRs or issues** with additional context

## Recognition

Contributors will be recognized in:
- The project's `CONTRIBUTORS.md` file (coming soon)
- Pull request acknowledgments

Thank you for helping make StudyUs better! 🎓

---

**Happy coding!**

Hardik Sharma & StudyUs Community
