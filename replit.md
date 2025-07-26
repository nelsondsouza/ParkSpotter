# Replit.md - Vehicle Parking App

## Overview

This is a full-stack Vehicle Parking Management System built with a modern tech stack. The application provides a comprehensive platform for managing parking lots, spots, and reservations with separate interfaces for administrators and regular users.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript using Vite as the build tool
- **UI Library**: Shadcn/ui components built on top of Radix UI primitives
- **Styling**: Tailwind CSS with custom design system
- **State Management**: TanStack Query (React Query) for server state
- **Routing**: Wouter for client-side routing
- **Forms**: React Hook Form with Zod validation
- **Charts**: Chart.js for data visualization

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Authentication**: Passport.js with local strategy using scrypt for password hashing
- **Session Management**: Express sessions with PostgreSQL session store
- **Database ORM**: Drizzle ORM
- **API Design**: RESTful API with role-based access control

### Database Design
- **Primary Database**: PostgreSQL via Neon Database
- **Schema**: Well-structured relational design with proper foreign key relationships
- **Entities**: Users, Parking Lots, Parking Spots, and Reservations
- **Migrations**: Managed through Drizzle Kit

## Key Components

### Authentication System
- **Strategy**: Session-based authentication using Passport.js
- **Security**: Password hashing with scrypt and salt
- **Authorization**: Role-based access (admin/user)
- **Session Storage**: PostgreSQL-backed session store for persistence

### User Management
- **Roles**: Two-tier system (admin and regular user)
- **Registration**: User self-registration with email validation
- **Profile Management**: Basic user information and contact details

### Parking Management
- **Lot Management**: Admins can create, update, and delete parking lots
- **Spot Management**: Dynamic spot generation and status tracking
- **Availability Tracking**: Real-time availability updates
- **Pricing**: Configurable hourly rates per parking lot

### Reservation System
- **Booking Flow**: Users can reserve available spots in real-time
- **Session Management**: Active reservation tracking
- **History**: Complete reservation history with cost calculations
- **Status Management**: Active and completed reservation states

### Analytics and Reporting
- **Admin Dashboard**: Comprehensive statistics and charts
- **User Dashboard**: Personal usage analytics
- **Data Visualization**: Chart.js integration for visual reporting
- **Metrics**: Occupancy rates, revenue tracking, and usage patterns

## Data Flow

### User Journey
1. **Authentication**: User logs in or registers through auth page
2. **Dashboard Access**: Role-based redirect to appropriate dashboard
3. **Lot Discovery**: Browse available parking lots with real-time availability
4. **Reservation**: Book available spots with immediate confirmation
5. **Management**: View active reservations and history

### Admin Workflow
1. **Lot Management**: Create and configure parking lots
2. **Spot Generation**: Automatic spot creation based on lot capacity
3. **Monitoring**: Real-time dashboard with occupancy and revenue metrics
4. **Analytics**: Access to comprehensive reporting and charts

### Data Synchronization
- **Real-time Updates**: TanStack Query manages cache invalidation
- **Optimistic Updates**: Immediate UI feedback with server reconciliation
- **Error Handling**: Graceful error states with user feedback

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: Neon PostgreSQL database connection
- **drizzle-orm**: Type-safe database ORM
- **@tanstack/react-query**: Server state management
- **passport**: Authentication middleware
- **express-session**: Session management
- **chart.js**: Data visualization

### UI Dependencies
- **@radix-ui/***: Comprehensive UI component primitives
- **tailwindcss**: Utility-first CSS framework
- **lucide-react**: Icon library
- **react-hook-form**: Form state management
- **zod**: Schema validation

### Development Dependencies
- **vite**: Build tool and dev server
- **typescript**: Type safety
- **tsx**: TypeScript execution for development
- **esbuild**: Production bundling

## Deployment Strategy

### Build Process
- **Frontend**: Vite builds optimized React bundle to `dist/public`
- **Backend**: esbuild bundles Express server to `dist/index.js`
- **Database**: Drizzle migrations applied via `db:push` command

### Environment Configuration
- **Database**: Requires `DATABASE_URL` environment variable
- **Sessions**: Requires `SESSION_SECRET` for secure session management
- **Development**: Hot reload with Vite middleware integration

### Production Considerations
- **Static Assets**: Frontend served as static files from Express
- **API Routes**: Backend handles `/api/*` routes
- **Database**: PostgreSQL connection pooling via Neon
- **Sessions**: Persistent sessions in PostgreSQL

### Scalability Design
- **Stateless Backend**: Session data stored in database
- **Connection Pooling**: Efficient database connection management
- **Caching Strategy**: TanStack Query provides client-side caching
- **Modular Architecture**: Clean separation of concerns for easy scaling