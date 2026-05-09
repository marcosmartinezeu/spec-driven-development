# Skill — dashboard-ui

## Purpose

Design and implement admin dashboard interfaces using Blade templates and Tailwind CSS.

This skill extends `server-rendered-ui` with dashboard-specific patterns: data tables, metric cards, filtering interfaces, and management screens that private users interact with.

The objective is functional, data-dense interfaces that help users manage content efficiently.

---

## Use This Skill When

Use this skill for:

* admin panel layouts (sidebar, navbar, content area)
* data tables with sorting, filtering, and pagination
* metric cards and KPI displays
* search and filter forms
* CRUD management screens
* user management interfaces
* reports and analytics views

If the question is "how should this dashboard screen look and behave?", this skill should be used.

---

## Core Rule

Dashboard UI serves data management, not decoration.

The interface must help users complete operational tasks quickly: view records, filter data, take actions, see results.

Visual noise reduces usability.

---

## Layout Rules

### Dashboard Shell

Every dashboard page follows this structure:

```
┌─────────────────────────────────────────────────┐
│  Top Navbar (logo, search, user menu)          │
├──────────┬──────────────────────────────────────┤
│          │  Breadcrumbs                        │
│          ├──────────────────────────────────────┤
│ Sidebar  │                                      │
│ (nav)    │  Main Content Area                  │
│          │  (cards, tables, forms)             │
│          │                                      │
└──────────┴──────────────────────────────────────┘
```

### Sidebar Rules

Sidebar must include:

* Logo/brand at top
* Navigation links grouped by function
* Collapsible on mobile (hamburger menu)
* Active state indicator for current section
* User role indicator when applicable

Sidebar navigation groups:

* Overview / Dashboard home
* Core business sections (Products, Orders, Users)
* Settings section
* Logout

### Navbar Rules

Navbar must include:

* Global search (optional but recommended)
* User avatar/name dropdown
* Notifications indicator (when applicable)
* Mobile menu toggle

### Content Area Rules

Content area follows:

* Breadcrumb navigation at top
* Page title as h1
* Primary action button (Add new, Create, etc.)
* Main content (table, form, or detail view)
* Pagination below tables

### Responsive Breakpoints

* Mobile: < 768px → sidebar becomes drawer, tables scroll horizontally
* Tablet: 768px - 1024px → sidebar collapsible, stacked cards
* Desktop: > 1024px → full layout

---

## Component Rules

### Metric Cards

Use for KPIs and summary data:

* Title (what the metric represents)
* Value (large, prominent number)
* Trend indicator (up/down arrow with percentage)
* Optional: comparison period

Example patterns:

```
┌─────────────┐  ┌─────────────┐
│ Total Sales │  │ New Users  │
│   $24,500   │  │    142     │
│  ▲ 12% vs   │  │  ▼ 5% vs   │
│   last week │  │  last week │
└─────────────┘  └─────────────┘
```

Rules:

* Max 4 cards per row on desktop
* Use consistent sizing
* Color-code trends (green for positive, red for negative)
* Optional: click to drill down

### Data Tables

Use for listing records with management options.

Required features:

* Sortable columns (click header to sort)
* Pagination (10/25/50/100 per page)
* Row actions (View, Edit, Delete)
* Bulk selection checkbox (when applicable)
* Empty state when no data

Optional features:

* Column visibility toggle
* Export button (CSV/Excel)
* Search/filter row

Table structure:

```
┌─────────────────────────────────────────────────┐
│  Search [___________]  Filter [▼]  [Export]     │
├─────────────────────────────────────────────────┤
│ ☐ │ Name      │ Email        │ Status │ Actions│
├─────────────────────────────────────────────────┤
│ ☐ │ John Doe  │ john@...     │ Active │ 👁 ✏ 🗑│
│ ☐ │ Jane Smith│ jane@...     │ Active │ 👁 ✏ 🗑│
└─────────────────────────────────────────────────┘
Showing 1-10 of 150  [Prev] [1] [2] ... [15] [Next]
```

### Forms

Dashboard forms follow these rules:

* Labels above inputs (not inline)
* Group related fields with fieldset or visual separation
* Inline validation errors below field
* Primary button right-aligned in forms
* Cancel/Back button as secondary style

Form field types needed:

* Text input (standard, with icon prefix)
* Textarea (for descriptions, notes)
* Select dropdown (single select)
* Multi-select (tags, checkboxes)
* Date picker
* File upload
* Toggle switch (for boolean fields)
* Number input with increment/decrement

### Action Buttons

Button hierarchy:

* **Primary** — Main action (Save, Create, Submit)
* **Secondary** — Supporting action (Cancel, Back, Filter)
* **Danger** — Destructive action (Delete, Remove)
* **Ghost** — Low-priority action (View, Details)

Button placement:

* Primary actions: top-right of content area or bottom-right of form
* Table row actions: right-aligned in last column
* Danger actions: always require confirmation modal

### Modals

Use for:

* Confirmation dialogs (delete, bulk actions)
* Quick forms (create from modal)
* Detail views (view without leaving page)

Modal structure:

* Title at top
* Content in middle
* Action buttons at bottom (Cancel left, Primary right)

### Alerts and Toasts

* **Alerts** — Inline, for form validation errors, success messages after redirect
* **Toasts** — Top-right, for non-blocking feedback (saved, copied, etc.)

Alert types:

* Success (green) — Operation completed
* Error (red) — Something went wrong
* Warning (yellow) — Attention needed
* Info (blue) — General information

---

## UX Rules

### Loading States

* Show skeleton placeholders while loading data
* Disable form buttons during submit
* Show spinner on table pagination/filter changes
* Skeleton should match final layout shape

### Empty States

Every list/table must have meaningful empty state:

* Clear message ("No products found")
* Suggest next action ("Create your first product")
* Include primary action button when appropriate

### Error Handling

* Show validation errors inline, next to field
* Show general errors in alert box at top of form
* Log detailed errors to console/network tab
* Show user-friendly message (not technical details)

### Confirmation

Required before:

* Deleting any record (modal confirmation)
* Bulk actions
* Submitting forms with significant impact
* Logging out with unsaved changes

### Navigation Feedback

* Active menu item visually highlighted
* Breadcrumbs reflect current location
* Back button works as expected

---

## Responsive Rules

### Mobile Requirements

* Sidebar becomes hamburger menu drawer
* Tables scroll horizontally with sticky first column
* Cards stack vertically (1 column)
* Forms: labels above inputs remain consistent
* Touch targets minimum 44px

### Tablet Adjustments

* Sidebar collapsible (icon-only mode)
* Tables: consider reducing visible columns
* Cards: 2 columns if space allows

### Desktop Optimizations

* Full sidebar visible by default
* 4 metric cards per row
* Tables with all columns visible
* Hover states on interactive elements

---

## Integration with Laravel

This skill works with `laravel-frameworks` and `server-rendered-ui`.

### Blade Components

Create reusable components for:

* `x-dashboard-layout` — Main wrapper with sidebar/navbar
* `x-dashboard-card` — Metric card wrapper
* `x-dashboard-table` — Table with pagination integration
* `x-dashboard-form` — Form wrapper with error handling
* `x-dashboard-modal` — Modal component
* `x-dashboard-alert` — Alert component

### Route Structure Recommendation

```
routes/
├── web.php (authenticated routes)
└── dashboard/
    ├── overview.php (dashboard home)
    ├── products/ (resource CRUD)
    ├── orders/ (resource CRUD)
    └── users/ (resource CRUD)
```

### Data Passing

* Controllers pass data to views, not to components directly
* Use View Composers for shared data (user, notifications)
* Query parameters handled in controller, passed to view

---

## Forbidden

* Mixing business logic into Blade templates
* Hardcoding URLs in views (use route() helper)
* Inline styles (use Tailwind classes)
* Tables without pagination for large datasets
* Forms without validation feedback
* Deleting without confirmation
* Mobile-unfriendly tables (horizontal scroll mandatory)
* Metric cards without trend indicators
* Missing empty states
* Breaking navigation patterns between sections

These create unusable or inconsistent dashboards.

---

## Expected Output

This skill should produce:

* Consistent dashboard shell across all pages
* Functional data tables with sort/filter/pagination
* Metric cards with trend indicators
* Responsive layouts for mobile/tablet/desktop
* Proper loading and empty states
* Clear action confirmation flows
* Maintainable Blade components
* Consistent styling following Tailwind conventions

The dashboard should feel professional, fast, and intuitive.