# Skill — nextjs-frameworks

## Purpose

Apply Next.js as a delivery tool without allowing framework decisions to dominate architecture.

This skill ensures Next.js supports the product without becoming the center of the system.

The objective is Next.js productivity without framework lock-in.

---

## Use This Skill When

Use this skill for:

* implementing pages and routes with App Router
* integrating with backend API (Laravel)
* designing layouts and nested routes
* configuring authentication (NextAuth.js or similar)
* setting up data fetching patterns
* integrating Tailwind + Shadcn UI
* making Next.js-specific implementation decisions

If the question is "how should Next.js support this?", this skill should be used.

---

## Core Rule

Next.js is a delivery mechanism.

It is not the architecture.

Framework convenience must never justify coupling.

The Domain lives in the backend (Laravel).

Next.js consumes it.

---

## App Router Rule

Use Server Components by default.

Rules:

* Prefer server components for data fetching
* Use client components only when interaction is required (onClick, useState, useEffect)
* Extract client islands intentionally, not by default
* Keep the component tree as simple as possible

Forbidden:

* Adding "use client" to everything for convenience
* Fetching data in Client Components when Server Components would suffice

---

## Routing Rule

Organize routes by feature, not by technical concern.

```
app/
├── (auth)/              # Route group: login, register
│   ├── login/
│   └── register/
├── (shop)/              # Route group: public shopping
│   ├── products/
│   ├── categories/
│   └── cart/
├── (dashboard)/         # Route group: protected user area
│   ├── orders/
│   ├── settings/
│   └── profile/
├── admin/               # Admin area (separate if needed)
└── api/                 # API routes (if needed)
```

Rules:

* Use route groups (...) to organize by context
* Keep URL structure clean and meaningful
* Nested routes for related pages
* Dynamic segments for resources ([id], [slug])

---

## Data Fetching Rule

Fetch data where it is needed.

Rules:

* Server Components fetch server-side
* Client Components use SWR, React Query, or similar for server data
* Keep data requirements close to the component that uses them

Forbidden:

* Fetching in parent and passing down unnecessarily
* Client-side fetching when server would be simpler

---

## API Integration Rule

Use typed API clients.

Rules:

* Create typed fetch wrappers per feature
* Keep API base URL configurable via environment variable
* Handle errors explicitly (no silent failures)
* Separate API logic from UI components
* Use interfaces matching backend DTOs

Example structure:

```
lib/api/
├── client.ts           # Base fetch wrapper
├── products.ts         # Product API methods
├── orders.ts           # Order API methods
└── auth.ts            # Auth API methods
```

---

## Auth Rule

Use NextAuth.js or similar.

Rules:

* Protect routes server-side with middleware
* Keep session handling server-side when possible
* Integrate with Laravel backend for user validation via API
* Never expose sensitive data to client

Environment variables for auth:

* NEXTAUTH_SECRET
* NEXTAUTH_URL

---

## UI Rule

Use Tailwind CSS with Shadcn UI or similar component library.

Rules:

* Extract reusable components to `components/ui/`
* Keep styling consistent with design system
* Use Server Components for layout, Client for interactive parts
* Prefer composition over custom styles

Component organization:

```
components/
├── ui/                 # Shadcn/base components (Button, Input, Card)
├── features/           # Feature-specific (ProductCard, OrderSummary)
└── layouts/            # Layout (Header, Footer, Sidebar)
```

---

## Environment Rule

Use environment variables for configuration.

Required:

* NEXT_PUBLIC_API_URL — Backend API base URL
* NEXTAUTH_SECRET — Auth secret
* NEXTAUTH_URL — App URL

Never hardcode URLs.

---

## Error Handling Rule

Handle errors explicitly.

Rules:

* Create error boundaries for graceful failures
* Show user-friendly messages
* Log errors for debugging
* Use error.tsx for route-level error handling
* Use loading.tsx for pending states

---

## Performance Rule

Optimize intentionally.

Rules:

* Use next/image for images
* Implement lazy loading for heavy components
* Cache API responses appropriately
* Use Server Components to reduce client bundle

---

## Forbidden

* business logic inside components
* hardcoded API URLs
* client-side fetching when server would suffice
* mixing Server and Client Components unnecessarily
* large page components without logical extraction
* exposing backend internals to client
* storing sensitive data in client
* creating custom styles when Tailwind suffices

These create coupling and maintenance debt.

---

## Review Questions

Before implementation, ask:

* does this need to be a Client Component
* is the API call properly typed
* is this data needed on server or can be client-fetched
* is the routing structure clean
* is error handling covered

---

## Expected Output

This skill should produce:

* clean App Router implementation
* typed API integration with backend
* consistent component patterns
* maintainable route structure
* clear separation of concerns
* secure authentication flow
* performant pages

Next.js should accelerate frontend delivery, not become the architecture.