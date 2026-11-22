# Daily Walk — Installable PWA + online backend starter

## What's ready in this package
- Version 4 UI preserved.
- Installable Progressive Web App manifest and icons.
- Service worker for an offline app shell.
- An Install button appears when the browser offers installation.
- `backend/schema.sql` starter database for Supabase (profiles, private journals, groups, memberships, posts, reports, and user blocks), with row-level security.

## Important: online service is not connected yet
Online account login, cloud journal sync, and real group posts require a Supabase project and its public project URL/key. This package includes a secure-ish starter schema, but the browser app still runs in local-only mode until the backend credentials and client integration are configured and tested. Do not publish it as a live community before moderation/reporting/blocking, account recovery, privacy, and age-appropriate protections are implemented and verified.

## Deploy the installable app (HTTPS required)
1. Create a GitHub repository and upload the contents of this folder (the `index.html`, `manifest.webmanifest`, `sw.js`, and `icons` folder must be at the repo root).
2. Publish using GitHub Pages, Netlify, or Cloudflare Pages. HTTPS hosting is required for service workers/installability.
3. Open the hosted HTTPS URL in Chrome on Android.
4. Tap **Install** when shown, or Chrome menu → **Install app** / **Add to Home screen**.
5. The installed app opens standalone. The service worker caches the app shell; current app data is stored in the browser on this device.

## Prepare Supabase
1. Create a Supabase project.
2. In SQL Editor, run `backend/schema.sql`.
3. Copy `backend/supabase-config.example.js` to `backend/supabase-config.js`, and add only the project's public anon/publishable key and URL.
4. Implement and test auth + sync client calls before using real data. Never expose service-role keys in frontend code.
5. Add group moderation and reporting workflows, verify row-level-security policies with test accounts, and set appropriate privacy/retention rules.

## Build a native APK later
This PWA can be installed from the browser once deployed. A native Android APK/AAB needs an Android wrapper (e.g. Capacitor) and an Android build environment/SDK; that build is not produced in this package.
