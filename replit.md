# UM AI Solver - Mobile Problem Diagnosis

## Overview

UM AI Solver is a mobile device troubleshooting application that uses AI to help users diagnose and solve mobile device problems through voice input and step-by-step solutions. The application features a custom AI assistant avatar, voice recognition capabilities, screen overlay guidance for premium users, and offers both free and premium tiers for problem-solving assistance. Premium users can access advanced screen casting features with visual guidance overlays.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a modern full-stack architecture with clear separation between client and server responsibilities:

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query for server state management and React hooks for local state
- **UI Components**: Radix UI components with shadcn/ui design system
- **Styling**: Tailwind CSS with CSS custom properties for theming
- **Voice Integration**: Web Speech API for speech recognition and synthesis

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ESM modules
- **API Design**: RESTful endpoints with JSON responses
- **Session Management**: Session-based authentication with in-memory storage
- **AI Integration**: Google Gemini AI for problem analysis and solution generation

## Key Components

### Database Layer
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Schema**: Shared schema definitions between client and server
- **Tables**: Users, problems, and chat messages with proper relationships
- **Storage**: Currently using in-memory storage with interface for easy database migration

### Authentication System
- **Session-based**: Uses session IDs stored in localStorage
- **User Management**: Automatic user creation and daily usage tracking
- **Premium Features**: Tiered access with usage limits for free users

### AI Problem Solving
- **Provider**: Google Gemini AI API
- **Process**: Structured problem analysis with step-by-step solutions
- **Categories**: Battery, connectivity, performance, and app issues
- **Output**: JSON-formatted solutions with actionable steps

### Voice Features
- **Recognition**: Web Speech API for voice input
- **Synthesis**: Speech synthesis for reading solutions aloud
- **Permissions**: Microphone access management with user consent

### Premium Screen Overlay Features
- **Visual Guidance**: Interactive overlay with arrows and step-by-step visual cues
- **Custom Avatar**: AI assistant with speech bubbles showing current instructions
- **Auto-Guide**: Screen overlay permissions for premium users
- **Interactive Controls**: Stop button and step navigation controls

## Data Flow

1. **User Session**: Application initializes with session management and permission requests
2. **Problem Category**: User selects from predefined problem categories
3. **Voice Input**: User describes problem via voice or text input
4. **AI Processing**: Problem description sent to Gemini AI for analysis
5. **Solution Generation**: AI returns structured solution with steps
6. **Chat Interface**: Solutions displayed in conversational format
7. **Voice Output**: Solutions can be read aloud to users

## External Dependencies

### Core Dependencies
- **@google/genai**: Google Gemini AI integration for problem solving (API Key: AIzaSyAJpf9f5QykJtmsM34WGQRjnW9nCU1K7_I)
- **@neondatabase/serverless**: PostgreSQL database connectivity
- **@tanstack/react-query**: Server state management and caching
- **drizzle-orm**: Type-safe database ORM with Zod validation

### UI Dependencies
- **@radix-ui/***: Comprehensive accessible UI component library
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Type-safe variant styling
- **cmdk**: Command palette component

### Development Dependencies
- **vite**: Fast build tool and development server
- **tsx**: TypeScript execution for development
- **esbuild**: Fast JavaScript bundler for production

## Deployment Strategy

### Development Environment
- **Dev Server**: Vite development server with HMR (Hot Module Replacement)
- **API Server**: Express server running concurrently with frontend
- **Database**: PostgreSQL with Drizzle migrations
- **Environment Variables**: Gemini API key and database URL required

### Production Build
- **Frontend**: Vite builds optimized static assets to `dist/public`
- **Backend**: esbuild bundles server code to `dist/index.js`
- **Deployment**: Single Node.js process serving both API and static files
- **Database**: Requires PostgreSQL instance with connection pooling

### Key Configuration Files
- **drizzle.config.ts**: Database migration and schema configuration
- **vite.config.ts**: Frontend build and development configuration
- **tsconfig.json**: TypeScript configuration for monorepo structure
- **tailwind.config.ts**: UI styling and theme configuration

## Recent Changes (January 2025)

### Custom AI Avatar Integration
- Added custom bot avatar image from user-provided asset
- Replaced generic avatar with branded UM AI Assistant image
- Implemented proper asset import and display handling

### Premium Screen Overlay System
- Created ScreenOverlay component with visual guidance arrows
- Added OverlayPermissionModal for screen access requests  
- Implemented step-by-step overlay navigation with bot avatar
- Added interactive controls (stop button, next step progression)
- Premium users get visual guidance overlays after problem analysis

### Enhanced User Experience
- Speech bubbles showing current step instructions
- Animated arrows pointing to relevant screen areas
- Real-time step progression with visual feedback
- Auto-trigger overlay after AI solution generation for premium users

The architecture prioritizes user experience with voice-first interaction, real-time AI assistance, visual guidance overlays, and mobile-optimized design while maintaining clean separation of concerns and type safety throughout the stack.