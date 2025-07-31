# CinePixel - AI Media Generation Platform

## Overview
CinePixel is a modern full-stack web application that allows users to generate stunning AI-powered images and videos using Replicate's API. The platform features a beautiful custom-designed interface, user authentication, a credit-based system, and a comprehensive gallery for managing generated content. The brand reflects creativity, AI innovation, and visual storytelling.

## User Preferences
Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for client-side routing
- **UI Components**: Shadcn/ui component library with Radix UI primitives
- **Styling**: Tailwind CSS with CSS variables for theming
- **State Management**: React hooks and context for local state, TanStack Query for server state
- **Build Tool**: Vite for development and production builds

### Backend Architecture
- **Runtime**: Node.js with Express.js framework
- **Language**: TypeScript with ES modules
- **API Design**: RESTful API with JWT-based authentication
- **External Services**: Replicate API for AI generation, Supabase for additional services
- **Session Management**: JWT tokens stored in localStorage on client

### Database & Storage
- **ORM**: Drizzle ORM with PostgreSQL dialect
- **Database**: PostgreSQL (configured for Neon serverless)
- **Schema**: Users table with credits system, Generations table for tracking AI outputs
- **Migrations**: Drizzle Kit for database schema management

## Key Components

### Authentication System
- JWT-based authentication with bcrypt password hashing
- User registration with email/password
- Token-based session management
- Protected routes with middleware authentication
- Credit system initialization (100 credits per new user)

### AI Generation Services
- **Image Generation**: Integration with Replicate's image models
- **Video Generation**: Integration with Replicate's video models
- **Status Tracking**: Async generation with status polling
- **Credit Management**: Deduction system for each generation

### User Interface
- **Dashboard**: Main interface for creating new generations
- **Gallery**: View and manage all user generations
- **Responsive Design**: Mobile-first approach with sidebar navigation
- **Component Library**: Comprehensive UI components from Shadcn/ui

## Data Flow

### Generation Workflow
1. User submits generation request (image/video)
2. Server validates user authentication and credits
3. Request sent to Replicate API with user parameters
4. Generation status tracked in database
5. Client polls for completion status
6. Completed media URLs stored and displayed

### Authentication Flow
1. User registers/logs in with credentials
2. Server validates and returns JWT token
3. Client stores token and includes in API requests
4. Protected routes verify token on each request
5. User data cached client-side for UI updates

## External Dependencies

### Core Production Dependencies
- **@neondatabase/serverless**: Neon PostgreSQL serverless client
- **@supabase/supabase-js**: Supabase client integration
- **@tanstack/react-query**: Server state management
- **bcrypt**: Password hashing
- **drizzle-orm**: Type-safe database ORM
- **express**: Web application framework
- **jsonwebtoken**: JWT token handling
- **replicate**: AI model API client

### UI/UX Dependencies
- **@radix-ui/react-***: Accessible UI primitives
- **tailwindcss**: Utility-first CSS framework with custom CinePixel gradients and effects
- **class-variance-authority**: Component variant management
- **react-hook-form**: Form handling with validation

## CinePixel Branding

### Design System
- **Logo**: Custom animated SVG logo featuring film reel with play button and pixel elements
- **Colors**: Gradient palette from indigo (#6366f1) through purple (#8b5cf6) to pink (#ec4899)
- **Typography**: Gradient text effects for headings and brand elements
- **UI Style**: Glass morphism effects, backdrop blur, elevated shadows, and smooth hover animations

### Key Visual Elements
- Animated sparkles in logo for dynamic feel
- Glass effect cards with backdrop blur
- Gradient backgrounds and text throughout interface
- Smooth hover animations with glow effects
- Modern rounded corners and elevated shadows

## Deployment Strategy

### Development Environment
- **Dev Server**: Vite dev server with Express API proxy
- **Hot Reload**: Full-stack hot reloading with Vite middleware
- **Build Process**: Separate frontend (Vite) and backend (esbuild) builds

### Production Configuration
- **Frontend**: Static assets served from Express
- **Backend**: Single Node.js process serving API and static files
- **Database**: PostgreSQL connection via environment variables
- **Environment**: NODE_ENV-based configuration switching

### Build Commands
- `npm run dev`: Development with hot reloading
- `npm run build`: Production build (frontend + backend)
- `npm run start`: Production server startup
- `npm run db:push`: Database schema deployment

The application follows a monorepo structure with shared TypeScript schemas between frontend and backend, ensuring type safety across the full stack. The credit-based system provides usage control, while the Replicate integration handles the complex AI generation workflows.

## Recent Updates (July 31, 2025)

### One-Click Content Enhancement Feature ✨
- Added four AI enhancement options: Upscale (10 credits), Refine (8 credits), Style Transfer (12 credits), Quality Boost (6 credits)
- Smart enhancement button appears on completed, non-enhanced content
- Beautiful popover interface with CinePixel gradient design
- Enhanced content tracking with visual badges and metadata
- Automatic gallery refresh when enhancements complete
- Database schema updated with enhancement fields (is_enhanced, original_generation_id, enhancement_type)

### Deployment Readiness
- Production build tested and working (npm run build)
- All environment secrets configured (DATABASE_URL, REPLICATE_API_TOKEN, JWT_SECRET, SUPABASE_URL, SUPABASE_ANON_KEY)
- Database schema deployed to Supabase PostgreSQL
- Vercel deployment configuration completed (vercel.json, api/index.ts)
- Ready for both Replit Autoscale and Vercel deployment

### Vercel Deployment Setup
- Added vercel.json configuration for serverless deployment
- Created api/index.ts for Vercel serverless functions
- Optimized for Vercel's edge network and CDN
- Full deployment guide available in README-VERCEL-DEPLOYMENT.md