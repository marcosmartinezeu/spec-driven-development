# Skill — nextjs-project-conventions

## Purpose

Capture project-specific conventions for a Next.js-derived project.

This example is intentionally opinionated enough to be useful, but still small enough to adapt.

It should be copied and refined only when the derived project actually uses these conventions.

---

## Active Stack

* framework: `Next.js 14+ (App Router)`
* language: `TypeScript`
* styling: `Tailwind CSS`
* components: `Shadcn UI`
* data fetching: `SWR` or `React Query`
* API: `REST (consuming Laravel backend)`
* auth: `NextAuth.js`

This example assumes `docs/project/active-stack.md` already declares Next.js as the active frontend framework.

---

## Project Structure

```
src/
├── app/                         # App Router
│   ├── (auth)/                 # Auth route group
│   │   ├── login/
│   │   └── register/
│   ├── (shop)/                 # Public shopping
│   │   ├── products/
│   │   │   ├── [slug]/
│   │   │   └── page.tsx
│   │   ├── categories/
│   │   └── cart/
│   ├── (dashboard)/            # Protected user area
│   │   ├── orders/
│   │   ├── profile/
│   │   └── settings/
│   ├── layout.tsx              # Root layout
│   └── page.tsx               # Home page
├── components/
│   ├── ui/                    # Shadcn base components
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── input.tsx
│   │   └── ...
│   ├── features/              # Feature components
│   │   ├── products/
│   │   ├── cart/
│   │   └── orders/
│   └── layouts/               # Layout components
│       ├── header.tsx
│       ├── footer.tsx
│       └── sidebar.tsx
├── lib/
│   ├── api/                   # Typed API clients
│   │   ├── client.ts
│   │   ├── products.ts
│   │   ├── orders.ts
│   │   └── auth.ts
│   ├── auth/                  # Auth configuration
│   │   └── auth.ts
│   └── utils/                 # Utilities
├── types/                      # TypeScript interfaces
│   ├── product.ts
│   ├── order.ts
│   └── user.ts
├── hooks/                      # Custom hooks
│   ├── useCart.ts
│   └── useProducts.ts
└── constants/                  # App constants
```

---

## Naming Conventions

### Routes

* lowercase, kebab-case
* examples: `product-detail`, `order-history`, `my-account`

### Components

* PascalCase
* examples: `ProductCard`, `OrderTable`, `UserMenu`

### Hooks

* camelCase with `use` prefix
* examples: `useProducts`, `useCart`, `useAuth`

### API / Services

* camelCase
* examples: `productService.ts`, `authApi.ts`, `orderClient.ts`

### Files

* page.tsx for routes
* layout.tsx for layouts
* loading.tsx for loading states
* error.tsx for error boundaries

---

## API Conventions

### Base Configuration

* Base URL from `NEXT_PUBLIC_API_URL` environment variable
* All endpoints relative to base

### Typed Responses

Create interfaces matching backend DTOs:

```typescript
// types/product.ts
export interface Product {
  id: string;
  name: string;
  slug: string;
  price: number;
  description: string;
  images: string[];
  category: Category;
}

export interface ProductListResponse {
  data: Product[];
  meta: {
    total: number;
    page: number;
    per_page: number;
  };
}
```

### Error Handling

```typescript
// lib/api/client.ts
export class ApiError extends Error {
  constructor(public status: number, message: string) {
    super(message);
  }
}
```

### Service Pattern

```typescript
// lib/api/products.ts
import { client } from './client';
import { Product, ProductListResponse } from '@/types/product';

export const productApi = {
  list: (params?: { category?: string; search?: string }) =>
    client.get<ProductListResponse>('/products', { params }),

  get: (slug: string) =>
    client.get<Product>(`/products/${slug}`),

  create: (data: CreateProductDto) =>
    client.post<Product>('/products', data),
};
```

---

## Component Rules

### Server Components by Default

* Use Server Components for pages and layouts
* Add "use client" only when needed (onClick, useState, useEffect)

### Client Components

Extract to separate files when needed:

```typescript
// components/features/cart/CartButton.tsx
'use client';

export function CartButton() {
  // interactive logic
}
```

### UI Components

Keep in `components/ui/`:

* Base components from Shadcn
* Wrappers around UI library

### Feature Components

Keep in `components/features/[feature]/`:

* Components specific to a domain
* Composed of UI components

---

## Route Conventions

### Public Routes

```
app/(shop)/page.tsx           → /
app/(shop)/products/page.tsx  → /products
app/(shop)/products/[slug]/page.tsx → /products/[slug]
```

### Auth Routes

```
app/(auth)/login/page.tsx     → /login
app/(auth)/register/page.tsx  → /register
```

### Protected Routes

```
app/(dashboard)/orders/page.tsx    → /dashboard/orders
app/(dashboard)/settings/page.tsx → /dashboard/settings
```

### Route Groups

Use route groups (...) to organize without affecting URL:

```
(app/auth)     → not in URL
(app/shop)    → not in URL
```

---

## Auth Conventions

### NextAuth Setup

```typescript
// lib/auth/auth.ts
import NextAuth from 'next-auth';
import Credentials from 'next-auth/providers/credentials';
import { authApi } from '@/lib/api/auth';

export const { handlers, signIn, signOut, auth } = NextAuth({
  providers: [
    Credentials({
      async authorize(credentials) {
        const user = await authApi.login(credentials);
        return user;
      },
    }),
  ],
  callbacks: {
    async jwt({ token, user }) {
      if (user) {
        token.accessToken = user.accessToken;
      }
      return token;
    },
    async session({ session, token }) {
      session.accessToken = token.accessToken as string;
      return session;
    },
  },
});
```

### Route Protection

Use middleware.ts or layout-level checks:

```typescript
// app/(dashboard)/layout.tsx
import { auth } from '@/lib/auth/auth';

export default async function DashboardLayout({ children }) {
  const session = await auth();
  if (!session) {
    redirect('/login');
  }
  return <>{children}</>;
}
```

---

## Styling Conventions

### Tailwind

* Use utility classes
* Avoid custom CSS unless necessary
* Keep responsive classes inline

### Component Styling

```typescript
// Prefer this
<div className="flex items-center justify-between">

// Over this
<div className="custom-flex">
```

---

## Testing Conventions

* Vitest for unit tests
* Playwright for E2E tests
* Test components in isolation
* Mock API calls

---

## Environment Variables

Create `.env.example`:

```bash
NEXT_PUBLIC_API_URL=http://localhost:8000/api
NEXTAUTH_SECRET=your-secret
NEXTAUTH_URL=http://localhost:3000
```

---

## Forbidden

* hardcoded API endpoints
* client-side secrets
* large monolithic components
* mixing fetch with UI logic
* using useClient when not needed
* creating custom CSS when Tailwind works

---

## Expected Output

This skill should produce:

* consistent Next.js project structure
* clear API integration patterns
* maintainable component organization
* type-safe frontend
* clean route organization
* proper authentication flow
* consistent styling