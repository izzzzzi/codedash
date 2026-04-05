# Skeleton Preloader & Sidebar Font Fix

## Sidebar — Unified font size

Currently 3 different font sizes in sidebar items: 14px (nav), 12px (.small — Install Agents, Changelog), 10px (section headers).

**Fix:** All sidebar items → 13px. Remove `.small` class usage. Section headers (Agents, Install Agents) stay 10px uppercase — they are labels, not navigation items.

### Changes

- `styles.css`: Change `.sidebar-item` font-size from 14px to 13px
- `styles.css`: Remove `.sidebar-item.small` rules (font-size: 12px, padding: 6px, small svg)
- `index.html`: Remove `class="small"` from Install Agents items and Changelog item

## Skeleton Preloader

When dashboard first loads, the content area is empty while `loadSessions()` fetches data. Show skeleton placeholder cards with shimmer animation.

### Implementation

- `styles.css`: Add `@keyframes skeleton-shimmer` animation, `.skeleton-card` styles
- `app.js`: In `init()`, render 6 skeleton cards into `#content` before `loadSessions()`. After `loadSessions()` completes, `render()` replaces them with real content (already happens — `applyFilters()` calls `render()` which sets `content.innerHTML`).

### Skeleton card structure

Mimics real card layout:
- Top row: badge placeholder + project placeholder + time placeholder
- Body: 2 text line placeholders
- Footer: 3 small metadata placeholders

Shimmer: `linear-gradient(90deg, transparent 25%, rgba(255,255,255,0.06) 50%, transparent 75%)` animated left-to-right, 1.5s infinite.

## Scope

- No new API endpoints
- No new dependencies
- Pure CSS + minimal JS changes
