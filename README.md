# Angular 21 Authentication Boilerplate

This is the frontend SPA for the full-stack authentication system deployment.

## Live Deployed Application
- **Live URL**: https://ipt-2026-frontend.onrender.com/

## Setup Instructions

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the development server:
   ```bash
   npm start
   ```
   *Note: In development (`npm start`), the app uses the built-in "Fake Backend" by default for Stage A testing without requiring the Node.js API to be running.*

## Deployment Configuration (Stage B)

To prepare for production deployment and integration with the live backend:

1. Ensure `src/environments/environment.prod.ts` contains the URL to your live deployed backend API.
2. Build the project for production:
   ```bash
   npm run build -- --configuration production
   ```
   *This command will swap out the development environment with `environment.prod.ts`, automatically disabling the fake backend and connecting the frontend to your live Node.js API.*

### Render SPA Routing Fix
When deploying this application as a Static Site on Render (or similar hosts), deep links (like email verification URLs) will return 404 errors by default because the routing is handled client-side by Angular.

**To fix this, you must add a Rewrite Rule in your Render dashboard:**
- **Source**: `/*`
- **Destination**: `/index.html`
- **Action**: `Rewrite`
