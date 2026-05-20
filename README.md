# Angular 21 Authentication Boilerplate

A full-featured Single Page Application (SPA) built with Angular 21, implementing a complete authentication system including Sign-Up with email verification, Login, JWT refresh token handling, Forgot Password, and Role-Based Access Control (RBAC).

## 🚀 Live Deployment
- **Live Application URL**: https://ipt-2026-frontend.onrender.com

## 🔗 Related Repository
- **Backend (Node.js + MySQL API)**: https://github.com/jude785/Lab-6-Activity-Building-a-Node.js-TypeScript-MySQL-Boilerplate-API

## ✨ Features
- User registration with email verification flow
- Login with JWT + `httpOnly` refresh token cookie management
- Automatic token refresh via `APP_INITIALIZER`
- Forgot password and password reset via email link
- Role-Based Access Control (Admin panel restricted to Admin role)
- Built-in Fake Backend for offline development and testing (Stage A)
- Angular route guards protecting authenticated/admin routes

## 🛠️ Local Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/jude785/Lab-7-Activity-Angular-21-Auth-Boilerplate---Sign-Up-with-Verification-Login-and-Forgot-Password.git
   cd Lab-7-Activity-Angular-21-Auth-Boilerplate---Sign-Up-with-Verification-Login-and-Forgot-Password
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Start the development server** (Fake Backend enabled by default):
   ```bash
   npm start
   ```
   The app runs at `http://localhost:4200`. The **Fake Backend** is automatically active in development mode (`production: false` in `environment.ts`), so no real API is needed for Stage A testing.

## 🔧 Stage A: Fake Backend Testing

The app includes a built-in fake backend interceptor. It is enabled automatically when `environment.ts` has `production: false`. This allows full testing of:
- Registration (with a mock email verification alert)
- Login / Logout
- JWT and refresh token simulation
- Admin panel access control

## 🌐 Stage B: Live Backend Integration

The app connects to the live backend via `src/environments/environment.prod.ts`:

```typescript
export const environment = {
    production: true,
    apiUrl: 'https://ipt-2026-backend-koy6.onrender.com'
};
```

When the Angular production build runs (`ng build --configuration production`), Angular automatically replaces `environment.ts` with `environment.prod.ts`, disabling the fake backend and pointing the app to the live Node.js API.

To build for production:
```bash
npm run build -- --configuration production
```

## 🔁 Render SPA Routing Fix

Deep links (like `/account/verify-email?token=...`) return 404 on Render by default because routing is handled client-side.

**Add this Rewrite Rule in your Render Static Site dashboard:**

| Setting | Value |
|---|---|
| **Source** | `/*` |
| **Destination** | `/index.html` |
| **Action** | `Rewrite` |

This ensures all routes are handled by Angular's router.
