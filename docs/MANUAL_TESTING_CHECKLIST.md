# 🧪 Manual Testing Checklist - ClaudeCodeUI-Flow

## 📋 Pre-Release Testing (Complete Before Each Release)

### ✅ Installation & Setup

- [ ] **Fresh Install**
  - Clone repo
  - `npm install` successful (no errors)
  - `npm run dev` starts without errors
  - App accessible at http://localhost:3000
  - No console errors on initial load

- [ ] **Environment Setup**
  - `.env` file properly configured
  - Claude-Flow installed globally (`which claude-flow`)
  - Claude Code installed (if testing that backend)
  - Cursor installed (if testing that backend)
  - `.swarm/memory.db` accessible (if exists)

### ✅ Backend Selector

- [ ] **Visual Check**
  - Selector visible in header/sidebar
  - 3 options displayed: Claude | Cursor | Claude-Flow
  - Icons/labels clear
  - Current selection highlighted

- [ ] **Functionality**
  - Click "Claude" → selected
  - Click "Cursor" → selected
  - Click "Claude-Flow" → selected
  - Refresh page → selection persisted
  - Health indicators show (green/yellow/red)
  - Hover tooltip shows version

- [ ] **Health Check**
  - Claude-Flow installed → green indicator
  - Claude-Flow not installed → red indicator + error message
  - Tooltip shows: "v2.0.0" or "Not found"

### ✅ Swarm Orchestration

- [ ] **UI Components**
  - Form fields visible: Task, Agents, Parallel, Non-interactive
  - Validation works (empty task → error)
  - Slider for agents (1-12) functional
  - Checkboxes toggle correctly
  - Submit button enabled when form valid

- [ ] **Presets**
  - Preset buttons displayed ("Build API", "Refactor", etc.)
  - Click preset → form pre-fills
  - Values correct (task description, agents, etc.)

- [ ] **Execution**
  - Submit form → loading state shows
  - Terminal web displays output in real-time
  - Stdout appears progressively
  - Stderr displayed in different color (red/orange)
  - ANSI colors rendered correctly
  - Completion → success message
  - Error handling → error message displayed

- [ ] **Terminal Web**
  - Output scrolls automatically
  - Scrollback works (scroll up to see history)
  - Copy text works (select + Ctrl+C)
  - Clear terminal button works
  - Search (Ctrl+F) works
  - Download logs button creates .txt file

### ✅ Hive-Mind Wizard

- [ ] **Wizard Steps**
  - Step 1 (Objective): Textarea works, validation
  - Step 2 (Topology): Radio buttons (mesh, hierarchical, ring, star)
  - Step 3 (Agents): Slider + type selection
  - Step 4 (Options): Checkboxes (parallel, monitoring, etc.)
  - Step 5 (Review): Summary displays all params correctly

- [ ] **Navigation**
  - "Next" button → advances step
  - "Previous" button → goes back
  - "Cancel" → closes wizard (confirmation?)
  - Progress indicator (1/5, 2/5, etc.) updates
  - Can't advance if step invalid

- [ ] **Submission**
  - Step 5 "Launch" → executes command
  - Terminal shows hive-mind output
  - Success feedback displayed
  - New session in history

### ✅ Agent Spawner

- [ ] **Form**
  - Agent type dropdown (researcher, coder, analyst, etc.)
  - Name input (optional)
  - Capabilities multi-select (optional)
  - Submit button enabled

- [ ] **Presets**
  - "Research Agent" button → spawns immediately
  - "Code Agent" button → spawns immediately
  - Success toast displayed

- [ ] **Custom Agent**
  - Fill form manually
  - Submit → agent spawned
  - Success message with agent ID/name
  - Active agents list updated (if available)

### ✅ History Viewer

- [ ] **Table Display**
  - Sessions load from `.swarm/memory.db`
  - Columns: Timestamp, Task, Status, Duration, Agents, Actions
  - Data displayed correctly
  - Timestamps formatted (e.g., "2025-10-15 14:30")
  - Status badges (success=green, error=red, running=yellow)
  - Duration formatted (e.g., "2m 34s")

- [ ] **Sorting**
  - Click "Timestamp" header → sort asc/desc
  - Click "Duration" header → sort by duration
  - Sort indicator (arrow up/down) visible

- [ ] **Filtering**
  - Date range picker works
  - Status filter dropdown works (all, success, error, running)
  - Search by task description works
  - Filters combine correctly (AND logic)

- [ ] **Pagination**
  - If >20 sessions, pagination controls visible
  - "Next" → loads next page
  - "Previous" → loads previous page
  - Page number displayed (e.g., "Page 1 of 3")

- [ ] **Row Click**
  - Click row → modal opens
  - Modal displays full session details:
    - Full task description
    - All parameters
    - Output logs
    - Agents used
    - Timestamp + duration
  - Close modal works (X button, Escape, click outside)

- [ ] **Actions**
  - "Replay" button → opens orchestrator with params
  - "Details" button → opens modal
  - "Delete" button → confirmation dialog → removes from UI (not DB!)

### ✅ Presets Library

- [ ] **Gallery View**
  - Presets displayed as cards
  - Default presets visible (Build API, Refactor, etc.)
  - Custom presets (if saved) visible
  - Icons/descriptions displayed

- [ ] **Preset Actions**
  - Click preset card → opens orchestrator
  - Form pre-filled correctly
  - Can modify before executing

- [ ] **Save Preset**
  - In orchestrator, configure custom settings
  - Click "Save as Preset"
  - Modal opens: name, description, tags
  - Submit → preset added to library
  - New preset visible in gallery

- [ ] **Import/Export**
  - Click "Export Presets" → JSON file downloads
  - Click "Import Presets" → file picker opens
  - Upload JSON → presets added to library
  - Duplicate handling (replace or skip?)

- [ ] **Search/Filter**
  - Search box filters presets by name/description
  - Tag filters work (if implemented)

### ✅ System Health Check

- [ ] **Dashboard**
  - All checks displayed:
    - Claude-Flow installed
    - Claude-Flow version
    - Memory DB accessible
    - Disk space
    - Node.js version
    - npm/pnpm available
  - Indicators show correctly (🟢 🟡 🔴)

- [ ] **Health Status**
  - All green → "System Healthy"
  - Some yellow → "Warnings Present"
  - Any red → "Critical Issues"

- [ ] **Troubleshooting**
  - Click red indicator → shows tips
  - "Fix" button (if available) attempts fix
  - Refresh button re-runs checks

### ✅ Dark Mode

- [ ] **Toggle**
  - Dark mode switch visible
  - Click → switches to dark theme
  - All components update (background, text, borders)
  - Terminal colors appropriate for dark theme
  - Refresh → dark mode persisted (localStorage)

- [ ] **Visual Quality**
  - Text readable (good contrast)
  - No white flashes on load
  - No elements broken in dark mode
  - Icons/images appropriate for theme

### ✅ Responsive Design

- [ ] **Desktop (1920x1080)**
  - Sidebar visible and fixed
  - All content displayed
  - No horizontal scroll
  - Terminal full width

- [ ] **Tablet (768x1024)**
  - Sidebar collapsible
  - Hamburger menu works
  - Content adapts (no overflow)
  - Touch targets adequate (>44px)

- [ ] **Mobile (375x667)**
  - Sidebar drawer (hidden by default)
  - Hamburger menu functional
  - Forms stack vertically
  - Buttons large enough to tap
  - Terminal scrollable
  - No text cut off

### ✅ Accessibility (WCAG AA)

- [ ] **Keyboard Navigation**
  - Tab order logical (header → sidebar → main → footer)
  - Focus visible on all interactive elements
  - Enter submits forms
  - Escape closes modals/dropdowns
  - Arrow keys navigate dropdowns/selects

- [ ] **Screen Reader (NVDA/JAWS/VoiceOver)**
  - Buttons announced correctly (e.g., "Button: Start Swarm")
  - Headings announced with levels
  - Form labels associated
  - Error messages announced
  - Live regions announce updates (e.g., "Swarm completed")

- [ ] **Color Contrast**
  - Text/background contrast ≥ 4.5:1
  - Large text ≥ 3:1
  - Dark mode also compliant
  - axe DevTools: 0 contrast violations

- [ ] **Focus Management**
  - Modal opens → focus trapped inside
  - Modal closes → focus returns to trigger
  - Error → focus moves to errored field

### ✅ Performance

- [ ] **Lighthouse Audit**
  - Performance: >90
  - Accessibility: >95
  - Best Practices: >95
  - SEO: >90 (if public)

- [ ] **Load Times**
  - First Contentful Paint (FCP): <1.5s
  - Time to Interactive (TTI): <3s
  - Largest Contentful Paint (LCP): <2.5s

- [ ] **Runtime Performance**
  - No jank on navigation (smooth 60fps)
  - Large lists virtualized (if >100 items)
  - No memory leaks (stable after 5 min use)

- [ ] **Bundle Size**
  - Total JS (gzipped): <500KB
  - No unnecessary dependencies
  - Code splitting implemented

### ✅ Security

- [ ] **Input Validation**
  - Task field: XSS prevented (e.g., `<script>alert('xss')</script>` rendered as text)
  - Command injection prevented (e.g., `; rm -rf /` sanitized)
  - SQL injection prevented (parameterized queries)

- [ ] **Secrets**
  - No hardcoded API keys in code
  - Environment variables used
  - `.env` in `.gitignore`

- [ ] **Dependencies**
  - `npm audit`: 0 high/critical vulnerabilities
  - `npx snyk test`: clean report

### ✅ Error Handling

- [ ] **User Feedback**
  - Success → green toast (auto-dismiss)
  - Error → red toast (manual dismiss)
  - Warning → orange toast
  - Info → blue toast

- [ ] **Error Messages**
  - User-friendly (not technical jargon)
  - Actionable (suggest solution)
  - Copy button to copy error for reporting

- [ ] **Edge Cases**
  - CLI not found → clear error message
  - DB not found → fallback UI (empty history)
  - Network error → retry mechanism
  - Timeout → appropriate error

### ✅ Cross-Browser Testing

- [ ] **Chrome**
  - All features work
  - No console errors
  - UI renders correctly

- [ ] **Firefox**
  - All features work
  - No console errors
  - UI renders correctly

- [ ] **Safari**
  - All features work
  - No console errors
  - UI renders correctly

- [ ] **Edge**
  - All features work
  - No console errors
  - UI renders correctly

### ✅ E2E Tests (Playwright)

- [ ] All E2E tests pass:
  ```bash
  npx playwright test
  ```
- [ ] No flaky tests (run 3 times)
- [ ] Screenshots on failure generated
- [ ] Video recordings available

---

## 🚀 Release Readiness Checklist

### Pre-Release

- [ ] All manual tests passed
- [ ] All automated tests passed (unit + integration + E2E)
- [ ] Security audit clean (`npm audit`, Snyk)
- [ ] Performance benchmarks met (Lighthouse >90)
- [ ] Documentation complete (user + developer)
- [ ] CHANGELOG.md updated
- [ ] Version bumped (package.json)
- [ ] 5+ external beta testers feedback

### Release

- [ ] Git tag created (`v1.0.0-beta`)
- [ ] GitHub Release published
- [ ] npm package published (if applicable)
- [ ] Announcement posts made (Reddit, Discord, Twitter)
- [ ] Feedback form created and linked

### Post-Release

- [ ] Monitor GitHub Issues for bug reports
- [ ] Monitor Discord/Reddit for feedback
- [ ] Respond to issues within 24h
- [ ] Triage bugs (critical → hotfix, others → next release)

---

## 📊 Testing Metrics

**Target Coverage:**
- Unit tests: >80%
- Integration tests: >70%
- E2E tests: Critical paths covered

**Target Performance:**
- Lighthouse Performance: >90
- Lighthouse Accessibility: >95
- Bundle size: <500KB gzipped

**Target Quality:**
- 0 high/critical npm audit vulnerabilities
- 0 axe DevTools violations
- <5 open critical bugs before release

---

**Tester Name:** _______________
**Date:** _______________
**Version Tested:** _______________
**Environment:** _______________

**Overall Pass/Fail:** ☐ Pass | ☐ Fail

**Notes:**
```
[Additional notes, observations, or issues found]
```
