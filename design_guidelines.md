# InterviewX – AI Interview Trainer Design Guidelines

## Design Approach

**Selected Approach:** Hybrid (Design System + Custom Elements)
- **Base System:** Material Design 3 principles for professional consistency
- **References:** Linear (clean interfaces, excellent typography), Grammarly (trust + analytics), Loom (video-first UX)
- **Rationale:** Professional tool requiring user trust with unique video/AI components

## Typography System

**Font Families:**
- Primary: Inter (via Google Fonts) - UI, body text, data displays
- Accent: Space Grotesk (via Google Fonts) - Headlines, scores, badges

**Hierarchy:**
- Hero Headlines: 3xl to 5xl, font-bold, Space Grotesk
- Section Titles: 2xl to 3xl, font-semibold
- Card Headers: xl, font-semibold
- Body Text: base, font-normal, leading-relaxed
- Captions/Labels: sm, font-medium
- Data/Scores: 2xl to 4xl, font-bold, tabular-nums

## Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, 8, 12, 16, 20, 24
- Component padding: p-4 to p-8
- Section spacing: py-12 to py-20
- Card gaps: gap-4 to gap-6
- Element margins: m-2 to m-6

**Grid System:**
- Container: max-w-7xl mx-auto px-4
- Interview screen: Custom 2-column grid (camera sidebar + question main area)
- History/Reports: 3-column grid on desktop, stack on mobile
- Dashboard: Asymmetric grid with larger stats cards

## Component Library

### Core Navigation
- **Top Navbar:** Fixed position, backdrop-blur, thin border-bottom, height h-16
  - Logo left, primary nav center, user avatar + notifications right
  - Mobile: Hamburger menu with slide-out drawer

### Camera & Interview Components
- **CameraFeed:** Rounded-2xl container with subtle border, aspect-video
  - Live preview overlay: Minimal controls at bottom
  - Expression indicators: Floating badges (top-right) showing confidence/engagement metrics
  - Recording indicator: Red dot with pulse animation when active
  
- **QuestionCard:** Large, prominent card with generous padding (p-8)
  - Question number badge (top-left, rounded-full)
  - Question text: text-xl to text-2xl, leading-relaxed
  - Timer: Floating bottom-right, circular progress indicator
  - Action buttons: Large, full-width or prominent placement

- **ControlBar:** Sticky bottom bar with primary actions
  - Start/Stop Recording, Submit Answer, Skip buttons
  - Use icon + text labels for clarity

### Scoring & Analytics Components
- **ScoreCard:** Dashboard-style cards with clear metric hierarchy
  - Large numerical score: 4xl, bold, centered at top
  - Progress ring/arc visualization around score
  - Breakdown sections below: Relevance, Fluency, Expression (each with mini-bar charts)
  - Suggestion chips: Rounded-full badges with icons

- **ProgressBadge:** Card with icon, title, description, progress bar
  - Unlocked badges: Full opacity, subtle glow effect
  - Locked badges: Opacity-50, grayscale filter
  - Grid layout: 3-4 columns on desktop

- **HistoryTable/Cards:** Hybrid view (table on desktop, cards on mobile)
  - Session date, role, score, duration columns
  - Clickable rows with hover elevation
  - Score visualization: Color-coded bars or dots

### Forms & Inputs
- **Role Selector:** Large card-based selection
  - Grid of role cards: 2-3 columns, each with icon, title, description
  - Selected state: Border highlight, subtle background
  - Difficulty toggle: Segmented control beneath

- **Consent Screen:** Centered modal overlay
  - Clear camera/mic icon illustrations
  - Permission list with checkmarks
  - Primary CTA button: Large, full-width

### Gamification Elements
- **Level Indicator:** Circular or shield badge with current level
  - XP bar beneath showing progress to next level
  - Animated on XP gain

- **Achievement Notification:** Toast-style notification from top-right
  - Badge icon, title, XP earned
  - Auto-dismiss after 5s

## Page Layouts

### Landing Page
- **Hero Section:** 60vh height, split layout
  - Left: Headline, subheading, 2 CTAs (Start Practice + Watch Demo)
  - Right: Animated illustration or demo video preview (rounded-2xl shadow)
- **Features Grid:** 3 columns, icon + title + description cards
- **How It Works:** Numbered step cards with connecting lines
- **Social Proof:** Logo cloud or testimonial cards (2 columns)
- **Pricing/CTA:** Centered section with gradient background

### Interview Screen
- **Layout:** Sidebar (1/3 width) + Main (2/3 width)
  - Sidebar: Camera feed, expression metrics, session info
  - Main: Question card (centered, large), control bar (sticky bottom)
- **Mobile:** Stack vertically, camera feed collapses to smaller preview at top

### Report/Results Page
- **Top Section:** Overall score hero (centered, large)
  - Circular progress with score inside
  - Congratulatory message or improvement prompt
- **Breakdown Grid:** 2-3 columns of metric cards
- **Detailed Analysis:** Full-width sections
  - Transcript review with highlights
  - Expression timeline graph
  - Suggestions as expandable accordions
- **Action CTAs:** Retry, Share Result, View History buttons

### History Page
- **Header:** Stats overview (total sessions, avg score, streak counter)
- **Filters Bar:** Role dropdown, date range, sort options
- **Sessions Grid/List:** Cards with quick stats, expandable for details

## Visual Principles

**Elevation & Depth:**
- Cards: shadow-sm with hover:shadow-md transitions
- Modals: shadow-xl with backdrop-blur overlay
- Floating elements: shadow-lg

**Interactive States:**
- Buttons: Slight scale on hover (hover:scale-105), opacity on active
- Cards: Border color change + subtle lift on hover
- Inputs: Border color transition, focus ring

**Data Visualization:**
- Use consistent color coding: Green (high scores), yellow (medium), red (low)
- Bar charts: Rounded caps, smooth transitions
- Progress indicators: Circular or linear with animated fills

**Trust Elements:**
- Privacy badge in footer
- Data security icon near consent screen
- "Your data is secure" microcopy

## Icons
**Library:** Heroicons (via CDN)
- Use outline style for navbar/general UI
- Use solid style for filled states, badges, notifications

## Animations
**Minimal, Purposeful Only:**
- Score reveal: Count-up animation (1-2s)
- Badge unlock: Scale + fade-in
- Page transitions: Fade (200ms)
- Loading states: Skeleton screens (no spinners)

## Images
**Hero Section:** Yes - large hero image/illustration
- Placement: Right side of hero (50% width on desktop)
- Description: Professional person practicing interview in modern setup OR abstract illustration showing AI analysis of speech/expressions
- Style: Modern, high-quality, slightly blurred background with subject in focus

**Throughout App:**
- Empty states: Custom illustrations (friendly, not corporate)
- Achievement badges: Custom icon designs (simple, recognizable)
- Role selector cards: Minimal icons representing each role

## Accessibility Notes
- All interactive elements meet 44×44px touch target minimum
- Contrast ratios: WCAG AA minimum (4.5:1 for text)
- Camera permissions: Clear explanatory text before requesting access
- Keyboard navigation: Focus indicators on all interactive elements
- Screen reader labels on all icon-only buttons