# Private Time — Phase 1

## Setup
1. Firebase Console: create a project, upgrade to Blaze (set a budget alert), enable Authentication > Google, create Firestore (production mode).
2. Project settings > Web app: copy config into `.env` (see `.env.example`).
3. `npm install` and `cd functions && npm install`.
4. `firebase login`, `firebase use <project-id>`.
5. `firebase deploy --only firestore:rules,functions`
6. Sign in once on the site with your Google account, then provision yourself:
   `cd functions && GOOGLE_APPLICATION_CREDENTIALS=/path/key.json node scripts/make-superadmin.js you@gmail.com`
   (keep that key file out of git and out of the frontend), then sign out and in again.
7. `npm run dev` to test locally, or `npm run build && firebase deploy --only hosting`.

## Phase 1 status
Done: design system, Google sign-in, server-created profiles, roles via custom claims, route guards,
teacher approve/suspend/revoke (with audit log), Firestore rules (default deny).
Not tested here: the build sandbox has no internet, so nothing has been installed or run yet.
Role changes apply after the user signs in again (tokens are revoked on change).
