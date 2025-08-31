# CFDI Management System

## Overview

This is a full-stack web application for managing Mexican CFDI (Comprobante Fiscal Digital por Internet) documents. The system allows users to connect to Odoo ERP systems, download CFDIs, and manage email distribution. It provides a comprehensive dashboard for viewing, filtering, and bulk downloading fiscal documents with automated email sending capabilities.

## User Preferences

Preferred communication style: Simple, everyday language.

## Critical Requirements (User extremely frustrated - 2025-01-30)
- **NO FAKE DATA**: Everything must come from real Odoo database
- **PDFs must be real**: Download actual PDF attachments from Odoo, never generate fake ones
- **Filtering must work perfectly**: All filters must work with real data
- **System must be stable**: No crashes, no errors, everything must work reliably
- User is frustrated with poor quality - MUST deliver working solutions, not mockups

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript using Vite as the build tool
- **UI Library**: Shadcn/UI components built on Radix UI primitives with Tailwind CSS
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: React Query (TanStack Query) for server state and caching
- **Form Handling**: React Hook Form with Zod validation for type-safe form management
- **Styling**: Tailwind CSS with CSS variables for theming support

### Backend Architecture
- **Framework**: Express.js with TypeScript in ESM format
- **Database ORM**: Drizzle ORM with PostgreSQL dialect for type-safe database operations
- **Storage Layer**: Abstracted storage interface with in-memory implementation for development
- **API Design**: RESTful endpoints with proper error handling and request logging middleware
- **File Processing**: Built-in file management system for CFDI downloads and email attachments

### Database Schema
- **Odoo Connections**: Store connection credentials and status for multiple Odoo instances
- **Companies**: Track companies associated with each Odoo connection
- **CFDIs**: Store CFDI metadata including XML/PDF URLs, status, and download tracking
- **Email Templates**: Configurable email templates for different document types
- **Download Jobs**: Track bulk download operations with progress monitoring

### External Integrations
- **Odoo API**: Direct integration with Odoo ERP systems for fetching CFDI data
- **Email Service**: SMTP-based email system using Nodemailer for automated document distribution
- **File Management**: Local file storage with configurable naming patterns and folder structures

### Key Features
- **Multi-Connection Support**: Manage multiple Odoo instances from a single dashboard
- **Advanced Filtering**: Filter CFDIs by date range, document type, status, and partner
- **Bulk Operations**: Select and download multiple CFDIs simultaneously
- **Email Automation**: Send CFDIs via email with customizable templates
- **Progress Tracking**: Real-time progress monitoring for download and email operations
- **Responsive Design**: Mobile-friendly interface with proper accessibility support

## External Dependencies

### Database
- **PostgreSQL**: Primary database using Neon serverless PostgreSQL
- **Drizzle Kit**: Database migrations and schema management

### Third-Party Services
- **Odoo ERP**: Source system for CFDI data via JSON-RPC API
- **SMTP Email Service**: Configurable email provider for document distribution (Gmail, custom SMTP)

### UI/UX Libraries
- **Radix UI**: Headless UI components for accessibility and customization
- **Tailwind CSS**: Utility-first CSS framework
- **Lucide React**: Modern icon library
- **React Hook Form**: Form validation and management
- **Zod**: Runtime type validation

### Development Tools
- **Vite**: Fast build tool with HMR support
- **TypeScript**: Type safety across the entire stack
- **ESBuild**: Production bundling for server code
- **PostCSS**: CSS processing with Tailwind integration