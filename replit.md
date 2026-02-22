# InterviewX - AI Interview Trainer

## Overview

InterviewX is an AI-powered interview practice platform that helps users prepare for job interviews. Users select a target role and difficulty level, then practice answering AI-generated interview questions while receiving real-time feedback on their performance. The system analyzes video/audio responses and provides detailed scoring across multiple dimensions including relevance, fluency, confidence, and engagement. A gamification layer with XP, levels, streaks, and badges encourages continued practice.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter (lightweight React router)
- **State Management**: Zustand with persistence middleware for client-side state
- **Data Fetching**: TanStack Query (React Query) for server state management
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **Styling**: Tailwind CSS with custom design tokens and CSS variables for theming
- **Build Tool**: Vite with React plugin

**Key Frontend Decisions**:
- Component-based architecture with clear separation between pages, components, and UI primitives
- Path aliases configured (`@/` for client/src, `@shared/` for shared code)
- Dark/light theme support via ThemeProvider context
- Offline-first consideration with question packs stored in public directory

### Backend Architecture
- **Runtime**: Node.js with Express
- **Language**: TypeScript with ESM modules
- **API Pattern**: RESTful endpoints under `/api` prefix
- **Build**: esbuild for production bundling with selective dependency bundling for cold start optimization

**Key Backend Decisions**:
- Monorepo structure with shared schema between client and server
- Development uses Vite middleware for HMR; production serves static files
- Session-based authentication pattern (connect-pg-simple for session storage)
- Password hashing with bcrypt

### Data Layer
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM with drizzle-kit for migrations
- **Schema Location**: `shared/schema.ts` (shared between frontend/backend)
- **Validation**: Zod schemas generated from Drizzle schemas via drizzle-zod

**Database Entities**:
- Users (authentication, XP/level progression, streaks)
- Questions (role-based question bank with difficulty levels)
- Interview Sessions (completed practice sessions with scores)
- Session Answers (individual question responses)
- Badges and UserBadges (gamification achievements)
- Offline Question Packs (cached questions for offline use)

### AI Integration
- **Primary**: OpenAI API for question generation and response analysis
- **Fallback**: Role-based question bank stored in server for offline/API-unavailable scenarios
- **Video Analysis**: TensorFlow.js and MediaPipe Face Mesh for client-side facial expression analysis

## External Dependencies

### Third-Party Services
- **OpenAI API**: Powers AI question generation and answer evaluation (requires `OPENAI_API_KEY`)
- **PostgreSQL Database**: Primary data store (requires `DATABASE_URL`)

### Key NPM Dependencies
- **AI/ML**: `openai`, `@tensorflow/tfjs`, `@mediapipe/face_mesh`
- **Database**: `drizzle-orm`, `pg`, `connect-pg-simple`
- **UI**: `@radix-ui/*` components, `tailwindcss`, `class-variance-authority`, `lucide-react`
- **Forms**: `react-hook-form`, `@hookform/resolvers`, `zod`
- **State**: `zustand`, `@tanstack/react-query`
- **Auth**: `bcrypt`, `express-session`, `passport`, `passport-local`
- **Utilities**: `date-fns`, `nanoid`, `clsx`, `tailwind-merge`

### Development Tools
- **Vite**: Development server with HMR and production builds
- **drizzle-kit**: Database migration management
- **tsx**: TypeScript execution for Node.js
- **Replit Plugins**: Runtime error overlay, cartographer, dev banner (development only)