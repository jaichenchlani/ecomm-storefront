# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Medusa Next.js Starter Template - an ecommerce storefront built with Next.js 15, TypeScript, and Tailwind CSS that integrates with Medusa v2 backend.

## Development Commands

- `npm run dev` - Start development server on port 8000 (uses Turbopack)
- `npm run build` - Build for production  
- `npm run start` - Start production server on port 8000
- `npm run lint` - Run ESLint
- `npm run analyze` - Analyze bundle size (set ANALYZE=true)

## Architecture

### Project Structure
- `src/app/` - Next.js App Router pages and layouts
  - `[countryCode]/` - Internationalized routing by country
  - `(main)/` - Main storefront pages (home, products, cart, account)
  - `(checkout)/` - Checkout flow pages
- `src/lib/` - Utilities and configuration
  - `data/` - API layer functions for Medusa backend calls
  - `util/` - Helper functions
  - `hooks/` - React hooks
  - `context/` - React context providers
- `src/modules/` - Feature-based UI components
  - Each feature (account, cart, checkout, etc.) has its own module
  - Components organized by templates, components, and actions
- `src/types/` - TypeScript type definitions

### Key Files
- `src/lib/config.ts` - Medusa SDK configuration and setup
- `src/middleware.ts` - Region/country routing middleware
- `src/lib/data/` - Data layer functions (cart.ts, products.ts, customer.ts, etc.)

### Medusa Integration
- Uses `@medusajs/js-sdk` for API calls
- Backend URL defaults to `http://localhost:9000`
- Requires Medusa v2 backend running
- Uses publishable keys for API authentication
- Supports internationalization with region-based routing

### Environment Variables
- `MEDUSA_BACKEND_URL` - Medusa server URL
- `NEXT_PUBLIC_MEDUSA_PUBLISHABLE_KEY` - Medusa publishable key
- `NEXT_PUBLIC_STRIPE_KEY` - Stripe public key
- `NEXT_PUBLIC_DEFAULT_REGION` - Default country region (defaults to "us")

### Path Aliases (tsconfig.json)
- `@lib/*` → `src/lib/*`
- `@modules/*` → `src/modules/*`  
- `@pages/*` → `src/pages/*`

## Development Notes

- Uses Next.js 15 App Router with server components
- Country-based routing via middleware (e.g., `/us/products`, `/uk/products`)
- Tailwind CSS for styling with `@medusajs/ui` components
- TypeScript strict mode enabled
- React 19 with server-only patterns
- Stripe integration for payments