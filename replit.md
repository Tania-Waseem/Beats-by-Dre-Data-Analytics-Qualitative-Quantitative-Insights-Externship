# Interactive Data Visualization Dashboard

## Overview

This project is an interactive data visualization dashboard built with React and Express. It displays analytical insights through multiple chart types including radar charts, bar charts, and word clouds. The application focuses on presenting pain point analysis data with interactive visualizations and insight cards. Currently, the application uses hardcoded mock data for demonstration purposes, with the infrastructure in place to integrate real data sources.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React with TypeScript using Vite as the build tool

**UI Component System**: The application uses shadcn/ui (New York style variant) built on top of Radix UI primitives. This provides a comprehensive set of accessible, customizable components with Tailwind CSS styling.

**Design Philosophy**: Follows a "data-first" approach inspired by Vercel and Notion's minimal aesthetics. The design emphasizes clarity, generous whitespace, and subtle sophistication with charts as the primary focus. Typography uses the Inter font family with a well-defined scale for hierarchy.

**State Management**: React Query (@tanstack/react-query) handles server state management and data fetching, with configuration for query caching and refetch behavior.

**Routing**: Wouter provides lightweight client-side routing.

**Data Visualization**: 
- Plotly.js (via react-plotly.js) powers the radar and bar charts
- D3-cloud generates word cloud visualizations
- AOS (Animate On Scroll) library adds scroll-triggered animations

**Styling**: Tailwind CSS with extensive customization through CSS variables for theming. The design system includes custom color palettes, spacing units, and component-specific styling patterns.

### Backend Architecture

**Framework**: Express.js running on Node.js with TypeScript

**Server Structure**: Minimal RESTful API setup with a modular route registration system. The server includes middleware for JSON parsing, request logging with timestamps, and static file serving.

**Build Strategy**: The application uses a custom build script that:
- Bundles the React frontend using Vite
- Bundles the Express server using esbuild
- Selectively bundles specific server dependencies (allowlist approach) to optimize cold start times
- Outputs to a `dist` directory for production deployment

**Development Mode**: Integrates Vite's development server with HMR (Hot Module Replacement) for rapid frontend development while the Express server handles API routes.

### Data Storage

**Database Setup**: Configured for PostgreSQL using Drizzle ORM

**Schema Definition**: Currently defines a basic `users` table with username/password authentication fields. The schema uses Drizzle's type-safe query builder and Zod for validation.

**Storage Interface**: Implements an `IStorage` interface with CRUD operations. Currently uses an in-memory storage implementation (`MemStorage`) for development, designed to be swapped with a database-backed implementation.

**Migration System**: Drizzle Kit handles schema migrations with a dedicated configuration pointing to the PostgreSQL database URL from environment variables.

### Authentication & Authorization

The application has infrastructure for user authentication through the defined user schema, but authentication logic (sessions, password hashing, JWT, etc.) is not yet implemented in the route handlers.

### Architectural Patterns

**Separation of Concerns**: Clear separation between client code (React app), server code (Express), and shared code (schemas, types).

**Type Safety**: End-to-end TypeScript with shared type definitions between frontend and backend via the `@shared` path alias.

**Path Aliases**: Configured aliases (`@/`, `@shared/`, `@assets/`) for clean imports throughout the codebase.

**Component Organization**: UI components are organized in a flat structure under `client/src/components/ui/` for shadcn components, with custom visualization components at the root components level.

**Mock Data Strategy**: Current implementation uses hardcoded data in components with TODO comments indicating where real data integration should occur, making it easy to identify integration points.

## External Dependencies

### UI & Visualization Libraries
- **Radix UI**: Comprehensive suite of unstyled, accessible UI primitives (accordion, dialog, dropdown, popover, etc.)
- **Plotly.js**: Interactive charting library for radar and bar charts
- **d3-cloud**: Word cloud layout algorithm
- **AOS**: Scroll animation library
- **html2canvas**: Dashboard export/screenshot functionality
- **Lucide React**: Icon library

### Styling & Theming
- **Tailwind CSS**: Utility-first CSS framework with custom configuration
- **class-variance-authority**: Type-safe variant styling
- **tailwind-merge & clsx**: Utility for merging Tailwind classes

### Form Handling
- **React Hook Form**: Form state management
- **@hookform/resolvers**: Validation resolver integration
- **Zod**: Schema validation library

### Data & State Management
- **TanStack React Query**: Server state management and caching
- **Drizzle ORM**: Type-safe SQL query builder
- **Drizzle Zod**: Schema validation integration

### Routing & Navigation
- **Wouter**: Lightweight routing library

### Development Tools
- **Vite**: Frontend build tool and dev server
- **tsx**: TypeScript execution for Node.js
- **esbuild**: Fast JavaScript bundler for server code
- **Replit-specific plugins**: Development banner, error overlay, and cartographer (development environment only)

### Database
- **PostgreSQL**: Primary database (via `pg` driver)
- **connect-pg-simple**: PostgreSQL session store (infrastructure present but not actively used)

### Potential Future Integrations
Based on package.json, the codebase has dependencies for:
- Email functionality (nodemailer)
- Payment processing (Stripe)
- AI/ML services (OpenAI, Google Generative AI)
- Authentication strategies (Passport.js)
- File uploads (Multer)
- Excel file handling (xlsx)
- WebSocket support (ws)

These suggest planned features but are not currently implemented in the application code.